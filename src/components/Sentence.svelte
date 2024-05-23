<script lang="ts">
const 문구 = `멈출 새 없이 바쁘게 걷다가
지친 걸음을 잠시 멈춰
인연처럼 만난 서로에게
사랑을 배울 수 있었고
함께 걷다보니
홀로 걷던 풍경보다
더 아름다웠고
혼자서 보이지 않았던
더 큰 세상을 만났습니다.
이제는 서로가 있기에
때론 멈춰 쉬어갈 수 있으며
더 멀리 갈 수 있습니다.
저희 두 사람이 앞으로의 긴 여정에
윤슬처럼 빛나는 햇살을 가득 받으며
힘차게 걸어갈 수 있도록
격려와 응원으로 축복해 주시면
감사하겠습니다.`;
</script>

<section class="greeting-section">
  <div class="sec-tit flex-center">이제 서로, 평생 함께</div>
  <div class="sec-txt">{문구}</div>
  <div class="info flex-center">
    <div class="ib">
      <div class="tb">
        <div class="row">
          <p class="honju">
            <span class="gt-span">권기순</span>
            <span class="gt-span bul"></span>
            <span class="gt-span">김진숙</span>
          </p>
          <p class="default">의</p>
          <p class="gwangye">장남</p>
          <p class="slsb">기순</p>
        </div>
        <div class="row">
          <p class="honju">
            <span class="gt-span">박용관</span>
            <span class="gt-span bul"></span>
            <span class="gt-span">최분옥</span>
          </p>
          <p class="default">의</p>
          <p class="gwangye">장녀</p>
          <p class="slsb">서은</p>
        </div>
      </div>
    </div>
  </div>
</section>
<style>
.sectence {
  text-align: center;
  white-space: pre;
  font-size: 1.2rem;
  line-height: 2;
  color: #333;
}
.greeting-section{
	padding:3.125rem 0;
}
.greeting-section .sec-tit {
    position: relative;
    padding-top: 0.938rem;
    margin-bottom: 2.5rem;
    font-family: 'KoPub Batang';
    font-size: 1rem;
    font-weight: 700;
    line-height: 1.250rem;
    text-align: center;
    color: #111;
    letter-spacing: 0.4em;
}
.greeting-section .sec-txt{
	margin-bottom:2.813rem;
	font-size:0.813rem;
	font-weight:300;
	line-height:1.5rem;
	color:#111;
  text-align:center;
  white-space:pre-wrap;
}
.greeting-section .sec-txt.large{
    font-size:0.937rem;
}

.greeting-section .sec-txt.big-large{
    font-size:1.06rem;
}

.greeting-section .info{
	font-size:0;
	line-height:0;
	text-align:center;
}
.greeting-section .info .row{
	display:table-row;
}
.greeting-section .info p{
	display:table-cell;
	vertical-align:top;
}
.greeting-section .info .honju{
	font-size:0;
	text-align:right;
}

.greeting-section .info .honju.typeB{	
    padding: 0.25rem 0.25rem 0.25rem 0;
}

.greeting-section .info .honju .gt-span{
	display:inline-block; 
	vertical-align:top;
	font-size:0.813rem;
	font-weight:400;
	line-height:1.5rem;
	text-align:center;
	white-space:pre-wrap;
}
.greeting-section .info .honju .gt-span.large{	
	font-size:0.938rem;	
	line-height:1.5rem;	
}
.greeting-section .info .honju .gt-span.big-large{	
	font-size:1.06rem;	
	line-height:1.5rem;	
}
.greeting-section .info .honju .gt-span.deceased-on{
	position:relative;
	padding-left:1.1rem;
}
.greeting-section .info .honju .gt-span.deceased-on:after{
	content:'故'; 
	position:absolute; 
	left:0.188rem; top:0; 
	display:block; 
	font-family:inherit;
	font-size:inherit; 
	font-weight:inherit; 
	line-height:inherit;
	color:#111;
}
.greeting-section .info .honju .gt-span.deceased-flower-on{
	position:relative;
	padding-left:1.1rem;
}
.greeting-section .info .honju .gt-span.deceased-flower-on:after{
	content:"";
    background-image: url(/mobile/new_m/mcard/images/common/chrysanthemum.png?ver=0.0.1); 
    background-size: cover;
    background-position: center;
	position:absolute; 
	left:0.188rem; 
    top:0.375rem; 
    width:0.75rem;
    height:0.625rem;
	display:block; 
	font-family:inherit;
	font-size:inherit; 
	font-weight:inherit; 
	line-height:inherit;	
}
.greeting-section .info .honju .bul{
	position:relative;
	width:0.750rem;
	height:1.5rem;
	overflow:hidden;
}
.greeting-section .info .honju .bul:after{
	content:'.';
	position:absolute;
	left:0; top:0;
	width:100%;
	display:block;
	font-size:0.813rem;
	font-weight:400;
	line-height:1;
	text-align:center;
}
.greeting-section .info .default{
	height:1.5rem;
	font-size:0.625rem;
	font-weight:300;
	line-height:1.625rem;
}
.greeting-section .info .default.typeB{
	height:3.125rem;	
	line-height:3.25rem;
}

.greeting-section .info .default.large{
	height:1.5rem;
	font-size:0.75rem;	
	line-height:1.625rem;
}

.greeting-section .info .default.typeB.large{
	height:3.25rem;
	font-size:0.75rem;
	font-weight:300;
	line-height:3.375rem;
}

.greeting-section .info .default.big-large{
	height:1.5rem;
	font-size:0.875rem;	
	line-height:1.625rem;
}

.greeting-section .info .default.typeB.big-large{
	height:3.375rem;
	font-size:0.875rem;
	font-weight:300;
	line-height:3.5rem;
}
.greeting-section .info .gwangye{
	height:1.5rem;
	padding-left:0.188rem;
	font-size:0.625rem;
	font-weight:300;
	line-height:1.625rem;
}
.greeting-section .info .gwangye.typeB{
	height:3.125rem;		
	line-height:3.25rem;
}

.greeting-section .info .gwangye.large{	
	font-size:0.75rem;		
}

.greeting-section .info .gwangye.typeB.large{	
    height:3.25rem;			
    line-height:3.375rem;
}

.greeting-section .info .gwangye.big-large{	
	font-size:0.875rem;		
}

.greeting-section .info .gwangye.typeB.big-large{
	height:3.375rem;		
	line-height:3.5rem;
}
.greeting-section .info .slsb{
	padding-left:0.313rem;
	font-size:1rem;
	font-weight:400;
	line-height:1.5rem;
	text-align:left;
	white-space:pre-wrap;
}
.greeting-section .info .slsb.typeB{	
	line-height:3.25rem;	
}

.greeting-section .info .slsb.large{	
	font-size:1.125rem;		
}

.greeting-section .info .slsb.typeB.large{	
    line-height:3.375rem;	
	font-size:1.125rem;	
}

.greeting-section .info .slsb.big-large{	
	font-size:1.25rem;	
	line-height:1.5rem;	
}

.greeting-section .info .slsb.typeB.big-large{	
	font-size:1.25rem;	
	line-height:3.5rem;	
}
</style>
