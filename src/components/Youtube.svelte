<script lang="ts">
export let DDAY = 1;
const 문구 = `참석이 어려우신 분들은
	온라인 중계로 시청하실 수 있습니다.`;
</script>

<h2 class="youtube-title maru-buri flex-center">결혼식 생중계 안내</h2>
<section class="youtube-txt flex-center">{문구}</section>
<section class="flex-center">2024년 9월 7일 오후 1시 50분 🎬</section>

{#if DDAY == 0}
<div class="video-wrap">
  <iframe
    width="560"
    height="315"
    src="https://www.youtube.com/embed/SpsEkx3V_mM?si=HT6EEU3KH80c5B17"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin"
    allowfullscreen
  />
</div>
{:else}
<div class="video-wrap">
  <iframe
    width="560"
    height="315"
    src="https://www.youtube.com/embed/SpsEkx3V_mM?autoplay=1&mute=1&loop=1&playlist=SpsEkx3V_mM"
    title="YouTube video player"
    frameborder="0"
    allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
    referrerpolicy="strict-origin-when-cross-origin"
    allowfullscreen
  />
</div>
{/if}
<style>
.youtube-title {
  padding-top: 2.938rem;
  margin-bottom: 2.5rem;
}
.youtube-txt {
  margin-bottom: 2.813rem;
  font-weight: 300;
  line-height: 1.5rem;
  color: #111;
  text-align: center;
  white-space: pre-wrap;
}
.video-wrap {
  position: relative;
  padding-bottom: 56.25%;
  height: 0;
  overflow: hidden;
  margin-top: 10%;
  margin-bottom: 10%;
}
.video-wrap iframe {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
