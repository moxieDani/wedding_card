<script lang="ts">
import PhotoSwipe from 'photoswipe';
import PhotoSwipeUI_Default from 'photoswipe/dist/photoswipe-ui-default';

import 'photoswipe/dist/photoswipe.css';
import 'photoswipe/dist/default-skin/default-skin.css';
import { onMount } from 'svelte';

const imageUrls = Array.from({ length: 41 }, (_, i) => `https://moxie2ks.synology.me/wedding/gallery/${i}-960.webp`);
const srcsets = imageUrls.map((_, i) =>
  [
    `https://moxie2ks.synology.me/wedding/gallery/${i}-320.webp 960w`,
    `https://moxie2ks.synology.me/wedding/gallery/${i}-640.webp 1920w`,
    `https://moxie2ks.synology.me/wedding/gallery/${i}-960.webp 2880w`,
  ].join(','),
);

const imageRatios: Record<string, number> = {};
const imageSizes: Record<string, { width: number; height: number }> = {};

let rootElement: HTMLDivElement;
let imageWidth: number;
let showMorePhotos = false;

const openPhotoSwipe = (index: number) => (e: Event) => {
  const thumbnailElement = e.target as HTMLElement | null;
  if (!rootElement || !thumbnailElement) return;

  const resizedItems = imageUrls.map(src => {
    const w = window.innerWidth;
    const ratio = imageRatios[src] ?? 1;
    const h = Math.floor(w * ratio);
    return { src, w, h };
  });

  const options: PhotoSwipeUI_Default.Options = {
    index,
    galleryUID: index + 1,
    showAnimationDuration: 0,
    tapToClose: true,
    captionEl: false,
    shareEl: false,
    fullscreenEl: false,
    maxSpreadZoom: 1.5,
  };

  const gallery = new PhotoSwipe(rootElement, PhotoSwipeUI_Default, resizedItems, options);
  gallery.init();
};

const loadImageSize = (url: string) => {
  return new Promise<void>(resolve => {
    const img = new Image();
    img.onload = () => {
      imageSizes[url] = { width: img.naturalWidth, height: img.naturalHeight };
      imageRatios[url] = img.naturalHeight / img.naturalWidth;
      resolve();
    };
    img.src = url;
  });
};

onMount(async () => {
  await Promise.all(imageUrls.map(loadImageSize));

  window.addEventListener('resize', () => {
    imageWidth = Math.floor(window.innerWidth / 3);
  });
  imageWidth = Math.floor(window.innerWidth / 3);
});
</script>

<h2 class="gallery-title maru-buri flex-center">갤러리</h2>
<section class="flex-center">
  <div class="gallery">
    {#each imageUrls as url, index (index)}
      <img
        role="none"
        loading="lazy"
        src={url}
        srcset={srcsets[index]}
        alt="{index + 1}번째 사진 보기"
        width={imageWidth}
        height={imageWidth}
        on:click={openPhotoSwipe(index)}
        hidden={index >= 15 && !showMorePhotos}
      />
    {/each}
  </div>

  <div class="pswp" tabIndex={-1} role="dialog" aria-hidden="true" bind:this={rootElement}>
    <div class="pswp__bg" />
    <div class="pswp__scroll-wrap">
      <div class="pswp__container">
        <div class="pswp__item" />
        <div class="pswp__item" />
        <div class="pswp__item" />
      </div>
      <div class="pswp__ui pswp__ui--hidden">
        <div class="pswp__top-bar">
          <div class="pswp__counter" />
          <button class="pswp__button pswp__button--close" title="Close (Esc)" />
          <button class="pswp__button pswp__button--zoom" title="Zoom in/out" />
          <div class="pswp__preloader">
            <div class="pswp__preloader__icn">
              <div class="pswp__preloader__cut">
                <div class="pswp__preloader__donut" />
              </div>
            </div>
          </div>
        </div>
        <button class="pswp__button pswp__button--arrow--left" title="Previous (arrow left)" />
        <button class="pswp__button--arrow--right" title="Next (arrow right)" />
        <div class="pswp__caption">
          <div class="pswp__caption__center" />
        </div>
      </div>
    </div>
  </div>
</section>
<section class="flex-center" style="padding-bottom:2%;">
  <div class="toggle-button-container">
    {#if imageUrls.length > 14}
      <button
        class="toggle-button"
        on:click={() => {
          showMorePhotos = !showMorePhotos;
          if (!showMorePhotos) {
            const galleryElement = document.querySelector('.gallery');
            galleryElement.scrollIntoView({ block: 'start' });
          }
        }}
      >
        {showMorePhotos ? '닫기' : '더 보기'}
      </button>
    {/if}
  </div>
</section>

<style>
.gallery {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  column-gap: 7px;
  row-gap: 7px;
  margin: 3%;
}
.gallery-title {
  position: relative;
  padding-top: 2.938rem;
  line-height: 1.25rem;
  text-align: center;
  color: #111;
}
.gallery img {
  object-fit: cover;
}
.toggle-button {
  border: 1px solid #f7f7f7; /* 테두리 색상 변경 */
  color: gray;
  padding: 10px 70px;
  text-align: center;
  font-size: 16px;
  margin: 4px 2px;
  cursor: pointer;
  border-radius: 50px;
}
.toggle-button:hover {
  border-color: #f7f7f7; /* 호버 시 테두리 색상 변경 */
}
</style>
