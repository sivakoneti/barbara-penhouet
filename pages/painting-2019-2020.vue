<template>
  <section class="page-painter-2020" ref="smoothscroll">
    <article class="banner">
      <h2>PEINTURES 2019-2020</h2>
    </article>
    <article class="first-row">
      <div class="column-1">
        <span>PEAU DE SILENCE</span>
        <p>Un corps, le corps, nos corps. Barbara P. se plait à arpenter les territoires complexes du corps, ses intérieurs, ses extérieurs,      ses mouvances, ses formes, ses textures. Le vide se faufilant, des discussions homme-homme, homme-espace, homme-nature, homme-temps, figuration-abstraction apparaissent.  En tant que peintre et architecte les « espaces d'entre deux » et leur exploration sont déterminants dans son travail.
          <br/><br/>
          Les lutteurs et les danceurs dansent pradoxalement entre l'attirance et répulsion de l'autre. Ce point d'équilibre entre l'individualité de l'homme et son besoin d'être ensemble est l'essence du travail de Barbara qu'elle tente de chorégraphier.
          <br/><br/>
          On ne peut construire le vide, à l’instar du bonheur, de l’harmonie,de l’intimité ou du silence. Il tient sa raison d’être en suspension de la présences de d’autres éléments. 
          À l’image de la rue symbole de démocratie et de liberté, mes représentations sont une ode au vivre ensemble par le silence de l’interstice, incluant ses amours et désamours.</p>
      </div>
      <div class="column-2">
        <img src="/images/painter/painter-6.jpg" alt="painter-2" />
      </div>
    </article>
    <span class="title-loop">LES PEINTURES</span>
    <SwiperItem :pictures="pictures" />
    <Footer :up="up" />
  </section>
</template>

<script>
  import Footer from '@/components/Footer.vue'
import SwiperItem from '../components/SwiperItem.vue'
  export default {
    layout: 'bg-white',
    components: {
      Footer,
      SwiperItem,
    },
    data() {
      return {
        pictures: [
          {
            src: '/images/painter/slider-2017/slider-1.jpg',
          },
          {
            src: '/images/painter/slider-2017/slider-2.jpg',
          },
          {
            src: '/images/painter/slider-2017/slider-3.jpg',
          },
          {
            src: '/images/painter/slider-2017/slider-4.jpg',
          },
          {
            src: '/images/painter/slider-2017/slider-5.jpg',
          },
          {
            src: '/images/painter/slider-2017/slider-6.jpg',
          },
        ]
      }
    },
    methods: {
      up() {
        const myEl = this.$refs.smoothscroll
        this.$smoothScroll({
          scrollTo: myEl,
          duration: 2000,
          updateHistory: false,
        })
      }
    }
  }
</script>

<style lang="scss" scoped>
$breakpoint-tablet: 1025px;

.page-painter-2020 {
  .banner {
    background: url("/images/painter/painter-5.jpg");
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
    height: 554px;
    position: relative;
    @media (max-width: $breakpoint-tablet) {
      background: url("/images/painter/painter-5-mobile.jpg");
      background-position: right;
      background-size: cover;
      background-repeat: no-repeat;
      height: 80vw;
    }
    h2 {
      position: absolute;
      top: 50%;
      left: 50%;
      text-align: center;
      transform: translate(-50%, -50%);
      font-size: 110px;
      color: #FFFFFF;
      width: 900px;
      @media (max-width: $breakpoint-tablet) {
        font-size: 12.800vw;
        color: #EF0311;
        text-align: center;
        width: 100%;
      }
    }
  }
  .first-row {
    display: flex;
    padding: 33px 100px;
    max-width: 1440px;
    margin: 0 auto;
    @media (max-width: $breakpoint-tablet) {
      display: block;
      padding: 8.800vw 8.533vw;
    }
    .column-1 {
      width: 50%;
      color: #EF0311;
      padding-right: 55px;
      @media (max-width: $breakpoint-tablet) {
        width: 100%;
        padding-right: 0;
      }
      span {
        font-size: 20px;
        font-weight: bold;
        @media (max-width: $breakpoint-tablet) {
          text-align: justify;
          font-size: 3.733vw;
        }
      }
      p {
        font-size: 14px;
        padding-top: 25px;
        @media (max-width: $breakpoint-tablet) {
          text-align: justify;
          font-size: 2.667vw;
        }
      }
    }
    .column-2 {
      width: 50%;
      @media (max-width: $breakpoint-tablet) {
        width: 100%;
        margin-top: 6.667vw;
      }
      img {
        width: 100%;
      }
    }
  }
  .title-loop {
    font-size: 20px;
    font-weight: bold;
    padding: 0 100px;
    @media (max-width: $breakpoint-tablet) {
      text-align: justify;
      font-size: 3.733vw;
      padding: 8.800vw 8.533vw;
    }
  }
  .second-row {
    column-gap: 24px;
    display: flex;
    margin: 33px 0;
    padding: 0 100px;
    .column-1,
    .column-2 {
      width: 50%;
      img {
        width: auto;
        height: 44.097vw;
      }
    }
  }
}
</style>