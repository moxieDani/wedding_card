<script lang="ts">
import { onMount } from 'svelte';
import sakuraCSS from '@/css/sakura.css';
let 타이틀1 = '권기순';
let 타이틀2 = '그리고';
let 타이틀3 = '박서은';
let 일시 = '2024년 9월 7일 토요일 오후 2시';
let 장소 = '대전 루이비스컨벤션 1층 그레이스홀';

let show = {
  title1: false,
  title2: false,
  title3: false,
  when: false,
  where: false,
  background: false,
};

onMount(() => {
  setTimeout(() => (show.title1 = true), 1400);
  setTimeout(() => (show.title2 = true), 2300);
  setTimeout(() => (show.title3 = true), 3100);
  setTimeout(() => (show.when = true), 3800);
  setTimeout(() => (show.where = true), 4800);
  setTimeout(() => (show.background = true), 50);

  // Sakura 효과 추가
  var sakura = new Sakura('#sakura-petals', {
    // Sakura 옵션 설정
    // 여기에 원하는 옵션을 추가할 수 있습니다.
    fallSpeed:1.5,
    maxSize:9,
    minSize:7,
    colors: [
      {
        gradientColorStart: 'rgba(255, 255, 255)',
        gradientColorEnd: 'rgba(214, 238, 255, 0.8)',
        gradientColorDegree: 200,
      },
      {
        gradientColorStart: 'rgba(255, 255, 255)',
        gradientColorEnd: 'rgba(204, 215, 255, 0.77)',
        gradientColorDegree: 180,
      },
      {
        gradientColorStart: 'rgba(255, 255, 255)',
        gradientColorEnd: 'rgba(214, 255, 249, 0.8)',
        gradientColorDegree: 180,
      },
      {
        gradientColorStart: 'rgba(255, 255, 255)',
        gradientColorEnd: 'rgba(255, 204, 215, 0.84)',
        gradientColorDegree: 200,
      },
      {
        gradientColorStart: 'rgba(255, 255, 255)',
        gradientColorEnd: 'rgba(255, 194, 211, 0.75)',
        gradientColorDegree: 210,
      },
      {
        gradientColorStart: 'rgba(255, 255, 255)',
        gradientColorEnd: 'rgba(255, 194, 200, 0.7)',
        gradientColorDegree: 180,
      },
    ]
  });
});
</script>

<div class="wrapper">
  <div id="sakura-petals"  />
  <section class="background {show.background ? 'show' : ''}">
    <section class="welcome_titles">
      <section class="welcome_title {show.title1 ? 'show' : ''}">{타이틀1}</section>
      <section class="welcome_title {show.title2 ? 'show' : ''}" style="font-size: 0.7rem;">{타이틀2}</section>
      <section class="welcome_title {show.title3 ? 'show' : ''}">{타이틀3}</section>
    </section>
    <section class="when_where {show.when ? 'show' : ''}">{일시}</section>
    <section class="when_where {show.where ? 'show' : ''}">{장소}</section>
  </section>
</div>

<style>
.wrapper {
  position: relative;
  width: 100%;
  height: 100vh;
  overflow: auto;
}

.background {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100vh;
  background: linear-gradient(
      to bottom,
      rgba(255, 245, 171, 0.854)0%,
      rgba(255, 255, 255, 0) 30%,
      rgba(255, 255, 255, 0) 87%,
      rgba(255, 222, 58, 0.8) 100%
    ),
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
  font-size: 1.3rem;
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
  font-size: 0.9rem;
}
.show {
  opacity: 1;
}
</style>
