<script lang="ts">
const 타이틀1 = 'WEDDING INVITATION';
const 타이틀2 = '권기순 | 박서은';
const 일시 = '2024. 09. 07. SAT PM 2:00';
const 장소 = '대전 루이비스컨벤션 1층 그레이스홀';
</script>

<link rel="stylesheet" href="https://fonts.googleapis.com/earlyaccess/nanummyeongjo.css" />

<section class="background">
  <section class="welcome_title nanum-myeongjo">
    <h4>{타이틀1}</h4>
    <h4>{타이틀2}</h4>
    <section class="welcome">
      <h2 class="when">{일시}</h2>
      <h3 class="where">{장소}</h3>
    </section>
  </section>
</section>

<style>
.background {
  display: flex; /* Flex 컨테이너로 설정 */
  justify-content: center; /* 가로 중앙 정렬 */
  align-items: center; /* 세로 중앙 정렬 */
  width: 100%;
  height: 100vh; /* 뷰포트 높이 전체를 사용 */
  background-image: linear-gradient(rgba(0, 0, 0, 0), rgba(0, 0, 0, 0)),
    url(https://moxie2ks.synology.me/wedding/gallery/9-960.webp);
  background-repeat: no-repeat;
  background-size: cover;
  background-position: center;
}
.welcome_title {
  padding-bottom: 5rem;
  color: black;
  z-index: 1;
  font-size: 1.2rem;
  text-align: center;
  text-shadow: 2px 2px 2px rgb(0 0 0 / 20%);
}
.welcome {
  padding-top: 5rem;
  padding-bottom: 8rem;
  color: black;
  z-index: 1;
  text-align: center;
}
.when,
.where {
  font-size: 1.2rem;
  font-weight: bold;
}
.nanum-myeongjo {
  font-family: 'Nanum Myeongjo', serif;
}
</style>
