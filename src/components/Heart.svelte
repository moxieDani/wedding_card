<script lang="ts">
import groom from '@/assets/groom.png';
import bride from '@/assets/bride.png';
import close from '@/assets/close.png';
import { onMount } from 'svelte';
import { copyToClipboard } from '@/utils';

const hearts = {
  groom: [
    { name: '예금주 : 권선종', account: '하나 622-047465-00107' },
    { name: '예금주 : 김진숙', account: '농협 417-02-001403' },
    { name: '예금주 : 권기순', account: '우리 1002-347-929038' },
  ],
  bride: [
    { name: '예금주 : 박용관', account: '농협 715084-51-080365' },
    { name: '예금주 : 최분옥', account: '농협 715084-52-104654' },
    { name: '예금주 : 박서은', account: '국민 714602-00-037091' },
  ],
};

type ModalContents = 'none' | '신랑' | '신부';
let focusedModal: ModalContents = 'none';
let modalContainerEl: HTMLElement;

const changeFocusedModal = (next: ModalContents) => () => {
  focusedModal = next;
};
const copyText = (text: string) => () => {
  copyToClipboard(text);
  alert(`${text} 복사되었습니다`);
};

onMount(() => {
  window.addEventListener('click', event => {
    const target = event.target as HTMLElement | null;
    if (!target) return;
    if (target !== modalContainerEl) return;
    focusedModal = 'none';
  });
});
</script>

<section class="container">
  <h2 class="maru-buri">신랑신부에게 마음 전하기</h2>

  <div class="flex-center">
    <button class="open-button" on:click={changeFocusedModal('신랑')}>
      <img class="img-icon groom-bg-color" src={groom} alt="groom-icon" />
      <br />
      신랑측 계좌번호 보기
    </button>
    <span class="button-gap" />
    <button class="open-button" on:click={changeFocusedModal('신부')}>
      <img class="img-icon bride-bg-color" src={bride} alt="bride-icon" />
      <br />
      신부측 계좌번호 보기
    </button>
  </div>
</section>

<div class="modal-container" bind:this={modalContainerEl} class:hide={focusedModal === 'none'}>
  {#each ['신랑', '신부'] as type}
    <section class="modal-contents" class:hide={focusedModal !== type}>
      <button class="close-button" on:click={changeFocusedModal('none')}>
        <img class="close-icon" src={close} alt="close-icon" />
      </button>

      <h3 class="modal-title maru-buri">
        {#if type === '신랑'}
          <img class="img-icon groom-bg-color" src={groom} alt="groom-icon" />
        {:else}
          <img class="img-icon bride-bg-color" src={bride} alt="bride-icon" />
        {/if}
        {type}측 계좌번호
      </h3>

      {#each type === '신랑' ? hearts.groom : hearts.bride as person, index (index)}
        <div style="padding-left: 10%; font-family: MaruBuri; font-size:1rem;">{person.name}</div>
        <div class="modal-item" on:click={copyText(person.account)} role="none">
          <div class="account">{person.account}</div>
          <div class="account-copy-text">복사</div>
        </div>
      {/each}
    </section>
  {/each}
</div>

<style>
.container {
  padding: 2rem 1rem;
  text-align: center;
}
.open-button {
  font-size: 0.9rem;
  font-family: 'Noto Sans KR';
}
.button-gap {
  padding: 1rem;
}
.hide {
  display: none;
}
.modal-container {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 10;
  font-family: 'KoPub Batang';
  font-size: 1.2rem;
}
.modal-contents {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  width: 95%;
  min-width: 200px;
  max-width: 600px;
  padding: 1rem;
  background-color: #fff;
}
.modal-title {
  display: flex;
  flex-flow: row;
  align-items: center;
  margin-bottom: 1.2rem;
}
.modal-item {
  font-family: 'MaruBuri';
  border-radius: 0.5rem;
  cursor: pointer;
  margin-bottom: 2rem;
  top: 0; /* 화면의 가장 위로 */
  z-index: 1000; /* 다른 요소들 위로 */
}
.img-icon {
  display: inline-block;
  width: 3rem;
  height: 3rem;
  border-radius: 50%;
  margin-right: 0.5rem;
  margin-bottom: 0.5rem;
}
.groom-bg-color {
  background-color: #b9e8ed;
}
.bride-bg-color {
  background-color: #fca6d9;
}
.account {
  padding-left: 10%;
  color: rgba(0, 0, 0, 0.8);
  font-size: 1rem;
}
.account-copy-text {
  position: absolute;
  right: 10%;
  transform: translateY(-100%);
  font-weight: 600;
  font-size: 1rem;
}
.close-button {
  position: absolute;
  top: 1rem;
  right: 1rem;
}
.close-icon {
  width: 1rem;
  height: 1rem;
}
</style>
