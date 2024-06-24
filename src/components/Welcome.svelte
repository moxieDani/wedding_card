<script lang="ts">
import { onMount } from 'svelte';

let 타이틀1 = '권기순';
let 타이틀2 = '그리고';
let 타이틀3 = '박서은';
let 일시 = '2024년 9월 7일 토요일 오후 2시';
let 장소 = '대전 루이비스컨벤션 1층 그레이스홀';

let show = {
  title1: false,
  title2: false,
  title3: false,
  whenWhere: false,
  background: false,
};

onMount(() => {
  setTimeout(() => (show.title1 = true), 500);
  setTimeout(() => (show.title2 = true), 1250);
  setTimeout(() => (show.title3 = true), 2000);
  setTimeout(() => (show.whenWhere = true), 2750);
  setTimeout(() => (show.background = true), 100);
});
</script>

<section class="background {show.background ? 'show' : ''}">
  <section class="welcome_titles">
    <section class="welcome_title {show.title1 ? 'show' : ''}" style="font-weight: 600;">{타이틀1}</section>
    <section class="welcome_title {show.title2 ? 'show' : ''}" style="font-size: 0.9rem;">{타이틀2}</section>
    <section class="welcome_title {show.title3 ? 'show' : ''}" style="font-weight: 600;">{타이틀3}</section>
  </section>
  <section class="when_where {show.whenWhere ? 'show' : ''}">
    <section>{일시}</section>
    <section>{장소}</section>
  </section>
</section>

<style>
.background {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  background: linear-gradient(rgba(0, 0, 0, 0), rgba(0, 0, 0, 0)),
    url(https://moxie2ks.synology.me/wedding/welcome.webp) no-repeat center/cover;
  opacity: 0;
  transition: opacity 1s ease-in-out;
}
.background.show {
  opacity: 1;
}
.welcome_titles {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  position: relative;
  bottom: 20%;
  z-index: 1;
  text-align: center;
  letter-spacing: 0.15em;
}
.welcome_title {
  padding: 0 0.5rem;
  color: black;
  font-size: 1.5rem;
  text-shadow: 2px 2px 2px rgb(0 0 0 / 3%);
  opacity: 0;
  transition: opacity 1s ease-in-out;
}
.when_where {
  position: relative;
  bottom: 15%;
  color: black;
  z-index: 1;
  text-align: center;
  opacity: 0;
  transition: opacity 1s ease-in-out;
  font-size: 1rem;
}
.show {
  opacity: 1;
}
</style>
