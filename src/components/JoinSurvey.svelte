<script lang="ts">
import close from '@/assets/close.png';

let focusedModal = false;
let modalContainerEl: HTMLElement;
let guest_selected = '';
let attend_selected = '';
let meal_selected = '';
let phone = '';
let form: any;
let submitted = false;

const 문구 = `축하의 마음으로 참석해주시는 한 분 한 분
  귀한 마음으로 모실 수 있도록
  부담없이 알려주시면 정성을 다해 준비하겠습니다.`;

const selectBox = (setter: (value: string) => void) => (value: string) => setter(value);

function hideFocusedModal(needHidden: boolean) {
  document.body.style.overflow = needHidden ? 'hidden' : '';
  focusedModal = needHidden;
}

function formatPhoneNumber(event) {
  let value = event.target.value.replace(/\D/g, ''); // 숫자만 남기기
  if (value.length > 11) {
    value = value.slice(0, 11); // 11자 초과 부분 제거
  }
  if (value.length > 3 && value.length <= 7) {
    value = value.replace(/(\d{3})(\d+)/, '$1-$2');
  } else if (value.length > 7) {
    value = value.replace(/(\d{3})(\d{4})(\d+)/, '$1-$2-$3');
  }
  phone = value;
}

function handleSubmit() {
  const formElements = document.querySelectorAll('#formId *');
  formElements.forEach(el => {
    el.style.transition = 'opacity 2s';
    el.style.opacity = 0;
  });

  setTimeout(() => {
    submitted = true;
    form.innerHTML = `
      <section class="survey-info flex-center">
        참석 여부 정보를 정상적으로 전달하였습니다.
      </section>
      <section class="survey-info flex-center" style="padding-bottom:2rem;">
        감사합니다.
      </section>
      `;
  }, 2000);
}

function onIframeLoad() {
  if (submitted) {
    handleSubmit();
  }
}

function submitForm() {
  if (!guest_selected) {
    alert('신랑측 또는 신부측을 선택해주세요.');
    return;
  }
  if (!attend_selected) {
    alert('참석 여부를 선택해주세요.');
    return;
  }
  if (!meal_selected) {
    alert('식사 여부를 선택해주세요.');
    return;
  }
  form.submit();
  handleSubmit();
}
</script>

<h2 class="container maru-buri flex-center">참석 의사 전달하기</h2>
<section class="survey-info flex-center">{문구}</section>
<div class="flex-center">
  <button class="open-button" on:click={() => hideFocusedModal(true)}>
    참석 의사 전달하기{submitted ? '(완료)' : ''}
  </button>
</div>

<div class="modal-container" bind:this={modalContainerEl} class:hide={!focusedModal}>
  <section class="modal-contents" class:hide={!focusedModal}>
    <button class="close-button" on:click={() => hideFocusedModal(false)}>
      <img class="close-icon" src={close} alt="close-icon" />
    </button>
    <h2 class="maru-buri flex-center">참석 의사 전달{submitted ? '완료' : '하기'}</h2>
    <form
      bind:this={form}
      id="formId"
      action="https://docs.google.com/forms/d/e/{import.meta.env.VITE_APP_GOOGLE_FORM_ADDRESS}/formResponse"
      method="POST"
      target="hidden_iframe"
      on:submit|preventDefault={submitForm}
    >
      <section class="survey-container">
        <div class="row-wrap">
          <div class="input-wrap">
            <div
              role="none"
              class="item {guest_selected === 'groom' ? 'selected' : ''}"
              on:click={selectBox(value => (guest_selected = value))('groom')}
            >
              <div class="check_box flex-center">
                <input
                  type="radio"
                  name="entry.203296518"
                  value="신랑측"
                  checked={guest_selected === 'groom'}
                />
                <span class="chk-txt">신랑측</span>
              </div>
            </div>
            <div
              role="none"
              class="item {guest_selected === 'bride' ? 'selected' : ''}"
              on:click={selectBox(value => (guest_selected = value))('bride')}
            >
              <div class="check_box flex-center">
                <input
                  type="radio"
                  name="entry.203296518"
                  value="신부측"
                  checked={guest_selected === 'bride'}
                />
                <span class="chk-txt">신부측</span>
              </div>
            </div>
          </div>
        </div>
        <div class="row-wrap">
          <p class="item-ttl">참석 여부</p>
          <div class="input-wrap">
            <div
              role="none"
              class="item {attend_selected === 'n' ? 'selected' : ''}"
              on:click={selectBox(value => (attend_selected = value))('n')}
            >
              <div class="check_box flex-center">
                <input
                  type="radio"
                  name="entry.1209815777"
                  value="참석 가능"
                  checked={attend_selected === 'n'}
                />
                <span class="chk-txt">참석 가능</span>
              </div>
            </div>
            <div
              role="none"
              class="item {attend_selected === 'y' ? 'selected' : ''}"
              on:click={selectBox(value => (attend_selected = value))('y')}
            >
              <div class="check_box flex-center">
                <input
                  type="radio"
                  name="entry.1209815777"
                  value="참석 불가"
                  checked={attend_selected === 'y'}
                />
                <span class="chk-txt">참석 불가</span>
              </div>
            </div>
          </div>
        </div>
        <div class="row-wrap">
          <p class="item-ttl">성함</p>
          <input type="text" name="entry.1159220997" required />
        </div>
        <div class="row-wrap">
          <p class="item-ttl">연락처</p>
          <input type="tel" name="entry.683743563" bind:value={phone} on:input={formatPhoneNumber} required />
        </div>
        <div class="row-wrap">
          <p class="item-ttl">식사 여부</p>
          <div class="input-wrap">
            <div
              role="none"
              class="item {meal_selected === 'y' ? 'selected' : ''}"
              on:click={selectBox(value => (meal_selected = value))('y')}
            >
              <div class="check_box flex-center">
                <input type="radio" name="entry.236212412" value="식사 가능" checked={meal_selected === 'y'} />
                <span class="chk-txt">식사 가능</span>
              </div>
            </div>
            <div
              role="none"
              class="item {meal_selected === 'n' ? 'selected' : ''}"
              on:click={selectBox(value => (meal_selected = value))('n')}
            >
              <div class="check_box flex-center">
                <input
                  type="radio"
                  name="entry.236212412"
                  value="식사 불가능(답례품 수령)"
                  checked={meal_selected === 'n'}
                />
                <span class="chk-txt">식사 불가능<br /><span class="sm-txt">(답례품 수령)</span></span>
              </div>
            </div>
          </div>
          <div class="flex-center">
            <button class="open-button" type="submit" value="Submit">정보 전달하기</button>
          </div>
        </div>
      </section>
    </form>
    {#if submitted}
      <div class="button-group flex-center">
        <button class="open-button" on:click={() => hideFocusedModal(false)}> 닫기 </button>
      </div>
    {/if}
    <!-- svelte-ignore a11y-missing-attribute -->
    <iframe name="hidden_iframe" id="hidden_iframe" style="display: none" on:load={onIframeLoad} />
  </section>
</div>

<style>
.container {
  padding-top: 2rem;
  text-align: center;
}
.open-button {
  font-family: 'Noto Sans KR';
  margin-bottom: 2rem;
  width: 50%;
  height: 3rem;
  background-color: #f3f3f3;
  border-radius: 4rem;
}
.survey-info {
  font-size: 0.95rem;
  margin-bottom: 2.813rem;
  line-height: 1.5rem;
  color: #111;
  text-align: center;
  white-space: pre-wrap;
}
.modal-container {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(0, 0, 0, 0.6);
  z-index: 1000;
}
.hide {
  display: none;
}
.modal-contents {
  background: #fff;
  padding: 2rem;
  width: 100%;
  height: 100%;
  max-width: 600px;
}
.close-button {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: none;
  cursor: pointer;
}
.close-icon {
  width: 24px;
  height: 24px;
}
form {
  margin-top: 2rem;
}
.survey-container,
.row-wrap {
  display: flex;
  flex-direction: column;
  gap: 20px;
}
.input-wrap {
  display: flex;
  flex-wrap: wrap;
  gap: 10px;
}
.item {
  flex: 1;
  min-width: 45%;
  border: 1px solid #cecece;
  cursor: pointer;
  padding: 5px;
}
.item-ttl {
  font-weight: bold;
  margin-bottom: -1rem;
}
.item.selected {
  background-color: #e5e5e5;
  border-color: #007bff;
  color: #007bff;
}
.item.selected .chk-txt {
  color: #007bff;
}
.check_box {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
.check_box input[type='radio'] {
  display: none;
}
.check_box input[type='radio']:checked + label .chk-txt {
  font-weight: bold;
  color: #007bff;
}
input[type='text'] {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
input[type='tel'] {
  width: 100%;
  padding: 5px;
  border: 1px solid #ccc;
  box-sizing: border-box;
}
.sm-txt {
  font-size: 0.8em;
  color: #888;
}
</style>
