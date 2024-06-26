<script lang="ts">
import guitar from '@/assets/guitar.png';

let audioPlayer: HTMLAudioElement | null = null;

function playMusic() {
  if (!audioPlayer) {
    audioPlayer = new Audio('https://kr.object.ncloudstorage.com/wedding/music.mp3');
  }

  if (audioPlayer.paused) {
    audioPlayer.play();
  } else {
    audioPlayer.pause();
  }
}
</script>

<button class="music-button" on:click={playMusic}>
  <img src={guitar} alt="music-icon" />
</button>

<style>
button {
  padding: 0.5rem;
}
.music-button {
  position: fixed;
  left: 0.5rem;
  bottom: 0.5rem;
}
.music-button img {
  width: 2rem;
}
</style>
