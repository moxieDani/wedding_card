<script lang="ts">
import bus from '@/assets/bus.png';
</script>

<div class="info">
  <div class="contain">
    <dl>
      <dt>대중교통 안내</dt>
      <dd class="bus-info">
        <span class="bus-item">대전 시내버스</span>
        <span class="bus-item"><img src={bus} alt="버스 아이콘" class="bus-icon" />701</span>
        <span class="bus-item"><img src={bus} alt="버스 아이콘" class="bus-icon" />704</span>
        <span class="bus-item"><img src={bus} alt="버스 아이콘" class="bus-icon" />705</span>
        <span class="bus-item"><img src={bus} alt="버스 아이콘" class="bus-icon" />802</span>
      </dd>
    </dl>
    <dl>
      <dt>주차 안내(2시간 무료)</dt>
      <dd>호텔 & 컨벤션 주차장 : 지상<br/>북문 주차장 : 주차타워, 지하<br/>남문 주차장 : 지상, 지하</dd>
    </dl>
    <dl>
      <dt>전세 버스 안내</dt>
      <dd>예식당일 오전 9시 30분 출발 / 강구 나비산식당 주차장</dd>
    </dl>
    <dl>
      <dt>신부측 피로연 안내</dt>
      <dd>9월 2일(월) 오전 11시 ~ 오후 8시 / 강구 나비산식당</dd>
    </dl>
  </div>
</div>

<style>
.info {
  -webkit-text-size-adjust: none;
  font-size: 1.2rem;
  line-height: 1.5;
  color: #111;
  word-wrap: break-word;
  word-break: break-all;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  font-family: 'Nanum Myeongjo', 'Nanum Gothic', sans-serif, 'helvetica', serif, 'AppleGothic';
  display: block;
  padding-top: 0.625rem;
  background: #f4f4f4;
}
.contain {
  -webkit-text-size-adjust: none;
  font-size: 1.2rem;
  line-height: 1.5;
  color: #111;
  word-wrap: break-word;
  word-break: break-all;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  box-sizing: border-box;
  margin: 0;
  font-family: 'Nanum Myeongjo', 'Nanum Gothic', sans-serif, 'helvetica', serif, 'AppleGothic';
  display: block;
  padding: 0 1rem;
  padding-top: 1.25rem;
  padding-bottom: 1.25rem;
  background: #fff;
}
dl {
  -webkit-text-size-adjust: none;
  font-size: 1.2rem;
  line-height: 1.5;
  color: #111;
  word-wrap: break-word;
  word-break: break-all;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  box-sizing: border-box;
  margin: 0;
  font-family: 'Nanum Myeongjo', 'Nanum Gothic', sans-serif, 'helvetica', serif, 'AppleGothic';
  display: block;
  padding: 0.625rem 0;
  border-bottom: 1px solid #eee;
}
dt {
  -webkit-text-size-adjust: none;
  word-wrap: break-word;
  word-break: break-all;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  box-sizing: border-box;
  margin-top: 1.5rem;
  margin-bottom: 1rem;
  padding: 0;
  list-style: none;
  display: block;
  font-family: 'Noto Sans KR';
  font-size: 1rem;
  font-weight: 600;
  line-height: 0.3rem;
  color: #111;
}
dd {
  -webkit-text-size-adjust: none;
  word-wrap: break-word;
  word-break: break-all;
  -webkit-tap-highlight-color: rgba(0, 0, 0, 0);
  box-sizing: border-box;
  margin: 0;
  padding: 0;
  list-style: none;
  display: block;
  font-family: 'Noto Sans KR';
  font-size: 1rem;
  font-weight: 400;
  color: #626262;
  white-space: pre-wrap;
  margin-bottom: 1rem;  
}
.bus-icon {
  width: 1em;
  height: 1em;
  vertical-align: middle; /* 또는 'text-bottom' */
  display: inline-block; /* 추가 */
}
.bus-info {
  display: flex;
  align-items: center;
  line-height: 0rem;
}
.bus-item {
  color: black;
  font-family: 'Helvetica Neue';
  background-color: #bae7f9; /* 하늘색 */
  display: flex;
  align-items: center;
  margin-right: 0.5em; /* 아이템 간 간격 */
  border-radius: 0.2em; /* 모서리 둥글게 */
}
</style>
