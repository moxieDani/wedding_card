<link rel="stylesheet" href="https://fonts.googleapis.com/earlyaccess/nanummyeongjo.css">

<script lang="ts">
  const 타이틀1 = 'WEDDING INVITATION';
  const 타이틀2 = '권기순 | 박서은';
  const 일시 = '2024. 09. 07. SAT PM 2:00';
  const 장소 = '대전 루이비스컨벤션 그레이스홀';
</script>

<section class="background flex-center">
  <section class="welcome_title nanum-myeongjo">
    <h4>{타이틀1}</h4>
    <h4>{타이틀2}</h4>
    <section class="welcome3">
      <h2 class="when">{일시}</h2>
      <h3 class="where">{장소}</h3>
    </section>
  </section>
</section>
  <style>
  .background {
    width: 100%;
    height: 100%;
    background-image: linear-gradient(rgba(0, 0, 0, 0.04), rgba(0, 0, 0, 0.1)),
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
  .welcome2 {
    color: white;
    z-index: 1;
    text-align: center;
    text-shadow: 2px 2px 2px rgb(0 0 0 / 20%);
  }
  .welcome3 {
    padding-top: 5rem;
    padding-bottom: 8rem;
    color: black;
    z-index: 1;
    text-align: center;
  }
  .who {
    font-size: 1.5rem;
  }
  .when{
    font-size: 1.2rem;
    font-weight: bold;
  }
  .where {
    font-size: 1.1rem;
    font-weight: bold;
  }
  .nanum-myeongjo {
    font-family: 'Nanum Myeongjo', serif;
  }
  </style>
  