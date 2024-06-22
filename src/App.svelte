<script lang="ts">
  import { onMount } from 'svelte';
  import Bowser from 'bowser';
  import Welcome from '@/components/Welcome.svelte';
  import Sentence from '@/components/Sentence.svelte';
  import Gallery from '@/components/Gallery.svelte';
  import Map from '@/components/Map.svelte';
  import Heart from '@/components/Heart.svelte';
  import Cheerup from '@/components/Cheerup.svelte';
  import Footer from '@/components/Footer.svelte';
  import FABs from '@/components/FABs.svelte';
  import Calendar from '@/components/Calendar.svelte';
  import Youtube from '@/components/Youtube.svelte';
  import Survey from '@/components/JoinSurvey.svelte';

  let observer: any;

  const setScreenSize = () => {
    const vh = window.innerHeight * 0.01;
    document.documentElement.style.setProperty('--vh', `${vh}px`);
  };

  onMount(() => {
    const parser = Bowser.getParser(window.navigator.userAgent);
    if (parser.getPlatformType() !== 'mobile') {
      window.addEventListener('resize', setScreenSize);
    }
    setScreenSize();

    observer = new IntersectionObserver(
      (entries) => {
        entries.forEach((entry) => {
          if (!entry.isIntersecting) {
            entry.target.classList.remove("fade-in");
          } else {
            entry.target.classList.add("fade-in");
          }
        });
      },
      { threshold: 0.1 }
    );

    const targetElements = document.querySelectorAll(".fade-wrap");
    targetElements.forEach((element) => {
      observer.observe(element);
    });

    return () => {
      observer.disconnect();
    };
  });
</script>

<main>
  <div class="pv-box">
    <div class="fade-wrap fade-in">
      <Welcome />
      <div class="seperator" />
    </div>
    <div class="fade-wrap">
      <Sentence />
      <div class="seperator" />
    </div>
    <div class="fade-wrap">
      <Gallery />
      <div class="seperator" />
    </div>
    <div class="fade-wrap">
      <Youtube />
    </div>
    <div class="fade-wrap">
      <Calendar />
    </div>
    <div class="fade-wrap">
      <Map />
    </div>
    <div class="fade-wrap">
      <Heart />
      <div class="seperator" />
    </div>
    <div class="fade-wrap">
      <Survey />
      <div class="seperator" />
    </div>
    <div class="fade-wrap">
      <Cheerup />
      <div class="seperator" />
    </div>
    <div class="fade-wrap">
      <Footer />
    </div>
    <FABs />
  </div>
</main>

<style>
  main {
    position: relative;
    height: calc(var(--vh, 1vh) * 100);
  }
  .seperator {
    background-color: #f8f9fa;
    height: 1rem;
  }
  .pv-box {
    width: 100%;
    height: 100%;
    overflow-y: scroll;
  }
  .pv-box .fade-wrap {
    transition: 1s;
    opacity: 1;
  }
  .pv-box .fade-wrap:not(.fade-in) {
    opacity: 0;
  }
</style>
