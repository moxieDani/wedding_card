<script lang="ts">
  import { onMount } from 'svelte';
  import tMapIcon from '@/assets/tmap.svg';
  import kakaoNaviIcon from '@/assets/kakao-navi.svg';
  import kakaoMapIcon from '@/assets/kakao-map.png';
  import naverMapIcon from '@/assets/naver-map.png';

  const 바로가기 = {
    kakao: 'http://kko.to/6HdjDZARgi',
    naver: 'https://naver.me/GRoGEhNe',
    tmap: `https://apis.openapi.sk.com/tmap/app/routes?appKey=${
      import.meta.env.VITE_APP_TMAP_API_KEY
    }&name=대전루이비스컨벤션&lon=127.397869&lat=36.4247938`,
  };

  let elluce = { lat: 36.4247938, lng: 127.397869 };

  onMount(() => {
    const script = document.createElement('script');
    script.src = "https://t1.kakaocdn.net/kakao_js_sdk/2.7.2/kakao.min.js";
    script.integrity = "sha384-TiCUE00h649CAMonG018J2ujOgDKW/kVWlChEuu4jK2vxfAAD0eZxzCKakxg55G4";
    script.crossOrigin = "anonymous";
    script.onload = () => {
      Kakao.init(import.meta.env.VITE_APP_KAKAO_JAVASCRIPT_KEY);
    };
    document.head.appendChild(script);
  });

  function shareLocation() {
    Kakao.Navi.share({
      name: '대전루이비스컨벤션',
      x: 127.397868,
      y: 36.4247938,
      coordType: 'wgs84',
    });
  }

  function handleClick(event) {
    event.preventDefault(); // 기본 링크 동작을 막습니다.
    window.open(바로가기.kakao, 'popup', 'width=600,height=600');
  }
</script>

<div class="flex-center map-icons">
  <div>
    <a href={바로가기.tmap} target="_blank">
      <img class="map-icon" src={tMapIcon} alt="tmap" />
    </a>
    <div class="map-icon-text">티맵</div>
  </div>
  <div>
    <!-- svelte-ignore a11y-click-events-have-key-events -->
    <a id="share-location" on:click={shareLocation}>
      <img class="map-icon" src={kakaoNaviIcon} alt="길 안내하기 버튼" />
    </a>
    <div class="map-icon-text">카카오내비</div>
  </div>
  <div>
    <a href={"#"} on:click={handleClick} style="cursor: pointer;">
      <img class="map-icon" src={kakaoMapIcon} alt="kakao-map" />
    </a>
    <div class="map-icon-text">카카오맵</div>
  </div>
  <div>
    <a href={바로가기.naver} target="_blank">
      <img class="map-icon" src={naverMapIcon} alt="naver-map" />
    </a>
    <div class="map-icon-text">네이버지도</div>
  </div>
</div>

<style>
.map-icons {
  margin-bottom: 2rem;
  gap: 2rem;
}
.map-icons img {
  display: inline-block;
}
.map-icon {
  width: 3rem;
  height: 3rem;
  margin: 0 0.25rem;
}
.map-icon-text {
  margin-top: 0.5rem;
  font-family: 'Noto Sans KR';
  font-size: 0.8rem;
  font-weight: 600;
  text-align: center;
}
</style>
