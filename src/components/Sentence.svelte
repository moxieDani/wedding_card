<script lang="ts">
const 문구1 = `멈출 새 없이 바쁘게 걷다가
지친 걸음을 잠시 멈춰
운명처럼 만난 저희 두 사람.`;

const 문구2 = `함께 걸으니
홀로 걸었을 때보다
더 아름다운 세상을 만났습니다.`;

const 문구3 = `이제는 서로가 있기에
때론 멈춰 쉬어갈 수 있으며
더 멀리 갈 수 있습니다.`;

const 문구4 = `저희 두 사람이 앞으로의 긴 여정에
윤슬처럼 빛나는 햇살을 가득 받으며
힘차게 걸어갈 수 있도록
격려와 응원으로 축복해 주시면
감사하겠습니다.`;
</script>

<section class="greeting-section">
  <div class="sec-tit maru-buri flex-center">이제 서로, 평생 함께</div>
  <div class="sec-txt">
    {문구1}
  </div>
  <div class="sec-txt">
    {문구2}
  </div>
  <div class="sec-txt">
    {문구3}
  </div>
  <div class="sec-txt">
    {문구4}
  </div>
  <div class="info flex-center">
    <div class="ib">
      <div class="tb">
        <div class="row">
          <p class="honju">
            <span class="gt-span">권선종</span>
            <span class="gt-span bul" />
            <span class="gt-span">김진숙</span>
          </p>
          <p class="gwangye">의 장남 <span class="slsb">기순</span></p>
        </div>
        <div class="row">
          <p class="honju">
            <span class="gt-span">박용관</span>
            <span class="gt-span bul" />
            <span class="gt-span">최분옥</span>
          </p>
          <p class="gwangye">의 장녀 <span class="slsb">서은</span></p>
        </div>
      </div>
    </div>
  </div>
</section>

<style>
.greeting-section {
  padding: 3.125rem 0;
}
.greeting-section .sec-tit {
  position: relative;
  font-weight: bold;
  line-height: 1.25rem;
  text-align: center;
  color: #111;
}
.greeting-section .sec-txt {
  margin-bottom: 1rem;
  font-size: 1rem;
  font-weight: 300;
  line-height: 2rem;
  color: #111;
  text-align: center;
  white-space: pre-wrap;
}
.greeting-section .info {
  font-size: 0;
  line-height: 0;
  padding-top: 10%;
  text-align: center;
}
.greeting-section .info .row {
  display: table-row;
}
.greeting-section .info p {
  display: table-cell;
  vertical-align: top;
}
.greeting-section .info .honju {
  font-size: 0;
  text-align: right;
}
.greeting-section .info .honju .gt-span {
  display: inline-block;
  vertical-align: top;
  font-weight: 700;
  font-size: 1rem;
  letter-spacing: 0.14em;
  line-height: 1.5rem;
  text-align: center;
  white-space: pre-wrap;
}
.greeting-section .info .honju .bul {
  position: relative;
  width: 0.75rem;
  height: 1.5rem;
  overflow: hidden;
}
.greeting-section .info .honju .bul:after {
  content: '.';
  position: absolute;
  left: 0;
  top: 0;
  width: 100%;
  display: block;
  font-size: 0.813rem;
  font-weight: 400;
  line-height: 1;
  text-align: center;
}
.greeting-section .info .gwangye {
  height: 2.5rem;
  padding-left: 0.188rem;
  font-size: 0.9rem;
  font-weight: 300;
  line-height: 1.625rem;
}
.greeting-section .info .slsb {
  vertical-align: top;
  font-weight: 700;
  font-size: 1.2rem;
  letter-spacing: 0.14rem;
  line-height: 1.5rem;
  text-align: center;
}
</style>
