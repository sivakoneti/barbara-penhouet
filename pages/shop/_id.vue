<template>
  <section ref="smoothscroll">
    <div class="page-product">
      <div class="image-product">
        <img :src="product.image.url" alt="" />
      </div>
      <div class="details-product">
        <span class="product-title">{{ product.name }}</span>
        <span class="product-price">{{ product.price }} € TTC</span>
        <span class="product-description">T-shirt blanc Barbara Penhouet</span>
        <span class="product-description">Print brodé de la série “nom de la série”</span>
        <span class="product-description">Fabriqué en France. 100% coton.</span>
        <div class="product-sizes">
          <button class="btn" @click="activeButton = 'XS'" :class="{active: activeButton === 'XS' }">XS</button>
          <button class="btn" @click="activeButton = 'S'" :class="{active: activeButton === 'S' }">S</button>
          <button class="btn" @click="activeButton = 'M'" :class="{active: activeButton === 'M' }">M</button>
          <button class="btn" @click="activeButton = 'L'" :class="{active: activeButton === 'L' }">L</button>
        </div>
        <button
          class="buy-button snipcart-add-item"
          :data-item-id="product.id"
          :data-item-name="product.name"
          :data-item-price="product.price"
          :data-item-url="product.url" 
          :data-item-image="product.image.url"
          data-item-description="T-shirt blanc Barbara Penhouet"
          data-item-custom1-name="Taille"
          :data-item-custom1-value="activeButton"
          data-item-custom1-options="XS|S|M|L"
        >
          AJOUTER AU PANIER
        </button>
        <div class="product-delivery">LIVRAISON ET RETOUR
          <br/><br/>
          Nous livrons partout dans le monde!
          Compter en moyenne 5 jours ouvrés pour recevoir son colis en France métropolitaine, et en moyenne 10 jours ouvrés pour recevoir son colis dans les autres pays.
          <br/><br/>
          Nous acceptons les retours, échanges et remboursements.
        </div>
      </div>
    </div>
    <Footer :up="up" />
  </section>
</template>

<script>
  import Footer from '@/components/Footer.vue';
  export default {
    components: {
      Footer
    },
    layout: 'default',
    async asyncData({ $prismic, error, route }) {
      const data = (
        await $prismic.api.getSingle('shop')
      ).data.products.filter((product) => product.id === route.params.id)
      const product = data[0]
      if (product) {
        return { product }
      } else {
        error({ statusCode: 404, message: 'Page not found' })
      }
    },
    data() {
      return {
        id: this.$route.params.id,
        activeButton: '',
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
      },
    },
  }
</script>

<style lang="scss" scoped>
$breakpoint-tablet: 1025px;

.page-product {
  display: flex;
  padding: 151px 240px 0 166px;
  @media (max-width: $breakpoint-tablet) {
    display: block;
    padding: 7.200vw 18.933vw;
  }
  .image-product {
    width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
    height: 100%;
    @media (min-width: $breakpoint-tablet) {
      width: 50%;
    }
    img {
      width: 456px;
      @media (max-width: $breakpoint-tablet) {
        width: 64vw;
      }
    }
  }
  .details-product {
    width: 369px;
    margin: 0 0 0 30px;
    @media (max-width: $breakpoint-tablet) {
      width: 49.600vw;
      margin: 0 auto;
      padding-top: 10.667vw;
    }
    span {
      display: block;
    }
    .product-title {
      font-size: 30px;
      font-weight: bold;
      padding-bottom: 23px;
      @media (max-width: $breakpoint-tablet) {
        font-size: 5.333vw;
      }
    }
    .product-price {
      font-size: 25px;
      font-weight: bold;
      padding: 0 0 69px;
      @media (max-width: $breakpoint-tablet) {
        font-size: 4vw;
        padding: 5.600vw 0 3.733vw;
      }
    }
    .product-description {
      font-size: 14px;
      @media (max-width: $breakpoint-tablet) {
        font-size: 3.200vw;
      }
    }
    .product-sizes {
      display: flex;
      justify-content: space-between;
      padding: 4vw 0;
      @media (min-width: $breakpoint-tablet) {
        padding: 60px 0 95px;
      }
      .btn {
        border: 1px solid #EF0311;
        color: #EF0311;
        width: 9.867vw;
        height: 8.533vw;
        display: flex;
        justify-content: center;
        align-items: center;
        font-size: 5.333vw;
        background-color: #FCF3F4;
        cursor: pointer;
        @media (min-width: $breakpoint-tablet) {
          width: 75px;
          height: 65px;
          font-size: 30px;
        }
      }
      .active, .btn:hover {
        background-color: #EF0311;
        color: white;
      }
    }
    .buy-button {
      background-color: #EF0311;
      color: #ffffff;
      cursor: pointer;
      border: none;
      width: 100%;
      height: 7.733vw;
      font-size: 3.200vw;
      margin-bottom: 6.400vw;
      @media (min-width: $breakpoint-tablet) {
        width: 325px;
        height: 41px;
        font-size: 20px;
        margin-bottom: 110px;
      }
    }
    .product-delivery {
      color: #000000;
      font-size: 3.200vw;
      @media (min-width: $breakpoint-tablet) {
        font-size: 12px;
      }
    }
  }
}
</style>