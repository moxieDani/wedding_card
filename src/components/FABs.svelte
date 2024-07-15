<script lang="ts">
let audioPlayer: HTMLAudioElement | null = null;
let isPlaying: boolean = false;
let isPageActive: boolean = true;
let musicButtonStr = '🔇';
function playMusic() {
  if (!audioPlayer) {
    audioPlayer = new Audio('https://kr.object.ncloudstorage.com/wedding/music.mp3');
    audioPlayer.play();
    isPlaying = true;
    musicButtonStr = '🔊';
  } else if (audioPlayer.paused) {
    audioPlayer.play();
    isPlaying = true;
    musicButtonStr = '🔊';
  } else {
    audioPlayer.pause();
    isPlaying = false;
    musicButtonStr = '🔇';
  }
}

// 페이지가 로드되면 자동으로 음악 재생
window.addEventListener('load', playMusic);

// 페이지 활성화 상태 추적
window.addEventListener('focus', () => {
  isPageActive = true;
  if (isPlaying) {
    audioPlayer?.play();
    musicButtonStr = '🔊';
  } else {
    musicButtonStr = '🔇';
  }
});

window.addEventListener('blur', () => {
  isPageActive = false;
  audioPlayer?.pause();
  musicButtonStr = '🔇';
});
</script>

<button class="music-button" on:click={playMusic}>
  {musicButtonStr}
</button>

<style>
.music-button {
  padding: 0.5rem;
  position: fixed;
  left: 0.5rem;
  bottom: 0.5rem;
}
</style>
