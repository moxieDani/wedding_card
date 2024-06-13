<script lang="ts">
import { initializeApp } from 'firebase/app';
import { getDatabase, ref, onValue, update, increment } from 'firebase/database';
import { onMount } from 'svelte';
import { format } from 'date-fns';
import Button_Heart from './Button_Heart.svelte';
import { getAnalytics } from 'firebase/analytics';

const firebaseConfig = {
  apiKey: import.meta.env.VITE_APP_FIREBASE_API_KEY,
  authDomain: import.meta.env.VITE_APP_FIREBASE_AUTH_DOMAIN,
  databaseURL: import.meta.env.VITE_APP_FIREBASE_DATABASE_URL,
  projectId: import.meta.env.VITE_APP_FIREBASE_PROJECT_ID,
  storageBucket: import.meta.env.VITE_APP_FIREBASE_STORAGE_BUCKET,
  messagingSenderId: import.meta.env.VITE_APP_FIREBASE_MESSAGING_SENDER_ID,
  appId: import.meta.env.VITE_APP_FIREBASE_APP_ID,
  measurementId: import.meta.env.VITE_APP_FIREBASE_MEASUREMENT_ID
};

const app = initializeApp(firebaseConfig);

// note: 위치 옮길 필요는 있지만, 일단 여기에
getAnalytics(app);

const db = getDatabase(app);
const heartsRef = ref(db, 'hearts');
const messagesRef = ref(db, 'messages');

type MessageRawObject = { [datetime: string]: { name: string; text: string } };
type Message = { id: string; name: string; text: string; datetime: string };
let heartCount = 0;
let messages: Message[] = [];
let displayedMessages: Message[] = [];
let typedNickname = '';
let typedMessage = '';
let currentPage = 1;
const messagesPerPage = 6;
$: enabledSendButton = typedNickname.length > 0 && typedMessage.length > 0;

const onClickHeart = () => {
  update(heartsRef, { count: increment(1) });
};

const onSubmit = () => {
  const name = typedNickname.trim();
  const text = typedMessage.trim();
  if (name.length === 0 || text.length === 0) {
    alert('빈 공백은 안됩니다. :(');
    return;
  }
  const datetime = Date.now().toString();
  update(messagesRef, { [datetime]: { name, text } });
  typedNickname = '';
  typedMessage = '';
};

const sortString = (a: string, b: string) => {
  if (a > b) return -1;
  if (a < b) return 1;
  return 0;
};

const updateDisplayedMessages = () => {
  const start = (currentPage - 1) * messagesPerPage;
  const end = start + messagesPerPage;
  displayedMessages = messages.slice(start, end);
};

const goPrePage = () => {
  if (currentPage > 1) {
    currentPage -= 1;
    updateDisplayedMessages();
  }
};

const goNextPage = () => {
  if (currentPage < Math.ceil(messages.length / messagesPerPage)) {
    currentPage += 1;
    updateDisplayedMessages();
  }
};

onMount(() => {
  onValue(heartsRef, snapshot => {
    const value = snapshot.val() ?? { count: 0 };
    heartCount = value.count;
  });
  onValue(messagesRef, snapshot => {
    const value: MessageRawObject = snapshot.val() ?? {};
    messages = Object.entries(value)
      .map(([id, value]) => {
        const datetime = format(+id, 'yyyy-MM-dd HH:mm:ss');
        return { id, datetime, ...value };
      })
      .sort((a, b) => sortString(a.datetime, b.datetime));
    updateDisplayedMessages();
  });
});
</script>

<section>
  <h2>축하 메시지</h2>

  <div>
    권기순
    <Button_Heart count={heartCount} onClick={onClickHeart} />
    박서은
  </div>

  <div class="message-container">
    <form on:submit|preventDefault={onSubmit}>
      <textarea class="message-form-text" bind:value={typedMessage} placeholder="축하글을 남겨주세요." />
      <div class="message-form-subbox">
        <input class="message-form-input" type="text" bind:value={typedNickname} placeholder="이름 입력" />
        <button class="message-form-button" type="submit" disabled={!enabledSendButton}>등록하기</button>
      </div>
    </form>
    <ul class="message-list">
      {#each displayedMessages as message (message.id)}
        <li class="message-item">
          <span class="message-item-name">{message.name}</span>
          <span class="message-item-date">{message.datetime}</span>
          <br />
          <p class="message-item-text">{message.text}</p>
        </li>
      {/each}
      {#if messages.length === 0}
        <li class="message-item-empty">
          🙏 <br />
          첫 축하글의 <br />
          주인공이 되어보세요 :)
        </li>
      {/if}
    </ul>
    <div class="paging">
      <a href="javascript:;" class="prev" on:click={goPrePage}>&lt;</a>
      {#each Array(Math.ceil(messages.length / messagesPerPage)).fill(0) as _, i}
      <a href="javascript:void(0);" class="{currentPage === i + 1 ? 'on' : ''}" on:click={() => { currentPage = i + 1; updateDisplayedMessages(); }}>{i + 1}</a>
      {/each}
      <a href="javascript:;" class="next" on:click={goNextPage}>&gt;</a>
    </div>
    {#if messages.length > 0}
      <div class="notice">😅 축하글 수정/삭제는 <br />신랑에게 문의해주세요 :)</div>
    {/if}
  </div>
</section>

<style>
section {
  padding: 2rem 1rem;
  text-align: center;
}
h2 {
  font-size: 1.75rem;
  margin-bottom:10%;
}
.message-container {
  min-width: 200px;
  max-width: 600px;
  margin: 0 auto;
  padding: 0 1.5rem;
  font-size: 0.875rem;
}
.message-form-text {
  display: block;
  width: 100%;
  height: 5rem;
  padding: 0.5rem;
  margin-bottom: 0.5rem;
  border: 1px solid #c4c4c4;
}
.message-form-subbox {
  display: flex;
  flex-flow: row;
}
.message-form-input {
  flex: 1;
  width: 100%;
  padding: 0.5rem;
  margin-right: 0.5rem;
  border: 1px solid #c4c4c4;
}
.message-form-button {
  padding: 0.5rem 1rem;
  background: #f65c8a;
  color: #fff;
  font-weight: bold;
  flex-shrink: 0;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.message-form-button:disabled {
  background: #f65c8a80;
  cursor: not-allowed;
}
.message-list {
  min-height: 300px;
  margin: 1rem 0;
}
.message-item-empty {
  color: gray;
  padding: 6rem 0;
}
.message-item {
  padding: 1rem 0;
  border-bottom: 1px solid #b6b2a2;
  text-align: left;
}
.message-item-name {
  font-size: 1rem;
  margin-right: 1rem;
}
.message-item-date {
  font-size: 0.75rem;
  color: #8c8c8c;
}
.message-item-text {
  font-size: 0.875rem;
  color: #666;
  margin-top: 0.25rem;
}
.notice {
  color: gray;
  padding: 2rem 0;
}
.paging {
  position: relative;
  width: 100%;
  background: #fff;
  text-align: center;
  padding: 1rem 0;
  color: #111;
  font-size: 0.875rem;
  display: flex;
  justify-content: center;
  gap: 0.5rem;
}
.paging a {
  color: #007bff;
  padding: 0.5rem 1rem;
  text-decoration: none;
  border: 1px solid #ddd;
  border-radius: 4px;
  transition: background-color 0.3s, color 0.3s;
}
.paging a:hover {
  background-color: #007bff;
  color: white;
}
.paging a.on {
  background-color: #007bff;
  color: white;
  border-color: #007bff;
}
.paging a.prev, .paging a.next {
  font-weight: bold;
  background-color: #f1f1f1;
}
.paging a.prev:hover, .paging a.next:hover {
  color: #007bff;;
}
</style>
