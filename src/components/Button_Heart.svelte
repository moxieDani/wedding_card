<script lang="ts">
  // ref: https://dribbble.com/shots/12234916--Like-Button-for-Figma-Cool
  let animated = false;
  let liked = false;
  let timerId = -1;

  export let count = 1;
  export let onClick = () => null;

  const countUp = async () => {
    window.clearTimeout(timerId);
    animated = false;
    await new Promise(resolve => setTimeout(resolve, 0));
    animated = true;
    if (!liked) liked = true;
  
    onClick();
  
    timerId = window.setTimeout(() => (animated = false), 800);
  };
</script>

<button class="like" on:click={countUp} class:liked class:shake={!liked}>
  <span class:bubble-motion={animated} />
  <p class="count-motion" class:active={animated}>{count}<br>💕</p>
</button>

<style lang="scss">
.like {
  position: relative;
  cursor: pointer;
  width: 46px;
  height: 46px;
  display: inline-flex;
  justify-content: center;
  align-items: center;
  border-radius: 12px;
  transition: all 0.3s ease;
  margin: 2rem 3rem;

  &::after {
    z-index: -2;
    position: absolute;
    content: '';
    width: 100%;
    height: 100%;
    background: #f6f6f8;
    border-radius: 12px;
    transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  }

  &:hover,
  &.liked {
    &::after {
      border-radius: 10px;
      background: #feeef3;
      transform: scale(0.88);
    }
  }

  &.shake {
    animation: shake 0.25s infinite alternate;
  }
}

@keyframes shake {
  0% { transform: translateY(-2.5px); }
  100% { transform: translateY(2.5px); }
}

p {
  position: absolute;
  font-size: 12px;
  font-weight: 600;
  padding: 6px 10px;
  color: #f65c8a;
  opacity: 0;
  transition: all 0.3s cubic-bezier(0.34, 1.56, 0.64, 1);
  font-family: -apple-system, sans-serif;
}

.count-motion {
  min-width: 100%;
  opacity: 1;
}

span {
  opacity: 1;
  z-index: -99;
  position: absolute;
  width: 90%;
  height: 90%;
  border-radius: 100%;
  background: radial-gradient(50% 50% at 50% 50%, rgba(255, 255, 255, 0) 0%, #feeff3 100%);
}

.bubble-motion {
  animation: bubbleMotion 0.8s cubic-bezier(0.25, 1, 0.5, 1) forwards;

  @keyframes bubbleMotion {
    to {
      transform: scale(2.6);
      opacity: 0;
    }
  }
}
</style>
