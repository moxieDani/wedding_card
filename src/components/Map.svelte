<script lang="ts">
import { onMount } from 'svelte';
import MapLink from '@/components/MapLink.svelte';
import VisitInfo from '@/components/VisitInfo.svelte';
import MapMark from '@/assets/map-mark.png';

let naverMap;
let elluce = { lat: 36.4247938, lng: 127.397869 };

onMount(() => {
  const naver_script = document.createElement('script');
  naver_script.src = `https://openapi.map.naver.com/openapi/v3/maps.js?ncpClientId=${import.meta.env.VITE_APP_NAVER_CLIENT_ID}`;
  naver_script.onload = () => {
    initNaverMap();
  };
  document.head.appendChild(naver_script);
});

function initNaverMap() {
  naverMap = new naver.maps.Map('map', {
    center: new naver.maps.LatLng(elluce.lat, elluce.lng).destinationPoint(0, -80),
    zoom: 16,
    minZoom: 8,
    zoomControl: true,
    zoomControlOptions: {
      position: naver.maps.Position.TOP_RIGHT,
    },
  });

  let marker = new naver.maps.Marker({
    icon: {
      url: MapMark,
      scaledSize: new naver.maps.Size(60, 60),
      origin: new naver.maps.Point(0, 0),
    },
    position: new naver.maps.LatLng(elluce.lat, elluce.lng),
    map: naverMap,
  });
}

function resetNaverMap() {
  if (naverMap) {
    naverMap.setCenter(new naver.maps.LatLng(elluce.lat, elluce.lng).destinationPoint(0, -80));
    naverMap.setZoom(15.5);
  }
}
</script>

<section>
  <h2 class="maru-buri">오시는 길</h2>
</section>
<div class="head">
  <div class="tit">대전 루이비스컨벤션 1층 그레이스홀</div>
  <div class="txt">
    <p>📍 대전 유성구 테크노중앙로 161</p>
    <p>📞 042-933-2500</p>
  </div>
  <div role="none" class="tel" on:click={() => (window.location.href = 'tel:042-933-2500')} style="cursor: pointer;" />
</div>
<div id="map" style="position: relative;">
  <button
    on:click={resetNaverMap}
    style="font-size: 0.8rem; position: absolute; bottom: 1px; left: 50%; transform: translateX(-50%); z-index: 1; font-weight:600; background-color:white;"
  >
    결혼식장 위치 보기
  </button>
</div>
<MapLink />
<VisitInfo />

<style>
section {
  padding: 2.5rem 1rem;
  padding-bottom: 0rem;
  text-align: center;
}
.head {
  position: relative;
  min-height: 2.25rem;
  padding: 1rem;
  background: #fafafa;
  box-sizing: content-box;
}
.tel {
  font-family: 'Nanum Myeongjo', 'Nanum Gothic', sans-serif, 'helvetica', serif, 'AppleGothic';
  color: #555;
  position: absolute;
  right: 1rem;
  top: 2rem;
  width: 2.8rem;
  height: 2.8rem;
  background: url('https://img.icons8.com/ios/100/phone--v1.png') 50% 50% no-repeat;
  background-size: 1.5rem;
  border: 0.01rem solid black;
  border-radius: 50%;
}
.tit {
  font-family: 'Noto Sans KR';
  font-size: 1rem;
}
.txt {
  font-family: 'Noto Sans KR';
  font-size: 0.9rem;
  font-weight: 300;
  line-height: 1.5rem;
  padding-left: 0.1rem;
  color: #777;
}
#map {
  width: 100%;
  height: 300px;
  margin-bottom: 2rem;
  z-index: 0;
}
</style>
