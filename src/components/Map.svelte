<script lang="ts">
  import { onMount } from 'svelte';
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
      center: new naver.maps.LatLng(elluce.lat, elluce.lng).destinationPoint(0, 50),
      zoom: 15.5,
      minZoom: 8,
      zoomControl: true,
      zoomControlOptions: {
        position: naver.maps.Position.TOP_RIGHT
      }
    });

    let marker = new naver.maps.Marker({
      icon: {
        url: MapMark,
        scaledSize: new naver.maps.Size(50, 50),
        origin: new naver.maps.Point(0, 0),
      },
      position: new naver.maps.LatLng(elluce.lat, elluce.lng),
      map: naverMap
    });

    const contentString = `
      <div class="iw_inner" style="width: 170px; height: 45px; text-align: center;">
      <h3>대전 루이비스컨벤션</h3>
      <p style="font-size: 0.8rem; margin: 0;">1층 그레이스홀</p>
      <p style="font-size: 0.7rem; margin: 0;">대전 유성구 테크노중앙로 161</p>
      <a href="tel:042-933-2500" style="font-size: 0.8rem; color:blue; font-weight:bold">Tel : 042-933-2500 </a>
      </div>
    `;

    let infowindow = new naver.maps.InfoWindow({
      content: contentString,
      maxWidth: 200,
      height: 50,
      backgroundColor: "white",
      borderColor: "black",
      borderWidth: 0.5,
      disableAnchor: true,
      textAlign: "center",
      margin: "auto",
      pixelOffset: new naver.maps.Point(0, -40)
    });

    naver.maps.Event.addListener(marker, "click", function() {
      if (infowindow.getMap()) {
          infowindow.close();
      } else {
        infowindow.open(naverMap, marker);
      }
    });

    infowindow.open(naverMap, marker);
  }

  function resetNaverMap() {
    if (naverMap) {
      naverMap.setCenter(new naver.maps.LatLng(elluce.lat, elluce.lng).destinationPoint(0, 30));
      naverMap.setZoom(15.5);
    }
  }

</script>

<section>
  <h2 class="maru-buri">오시는 길</h2>
  <div id="map" style="position: relative;">
    <button on:click={resetNaverMap} style="font-size: 0.8rem; position: absolute; bottom: 1px; left: 50%; transform: translateX(-50%); z-index: 1; font-weight:600; background-color:white;">
      결혼식장 위치 보기
    </button>
  </div>
</section>

<style>
section {
  padding: 2rem 1rem;
  text-align: center;
}
#map {
  width: 100%;
  height: 300px;
  z-index: 0;
}
</style>
