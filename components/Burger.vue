<template>
    <div
      id="burger"
      :class="{ 'active' : isBurgerActive }"
      @click.prevent="toggle">
        <slot>
            <button type="button" class="burger-button" title="Menu">
                <span class="burger-bar burger-bar--1"></span>
                <span class="burger-bar burger-bar--2"></span>
                <span class="burger-bar burger-bar--3"></span>
            </button>
            <div v-if="isBurgerActive" class="sidebar">
              <nuxt-link to="/" class="logo-link">
                <img
                  class="burger-logo"
                  src="/images/logo.png"
                  alt="Barbara Penhouet"
                />
              </nuxt-link>
              <ul class="burger-list">
                <nuxt-link to="/illustrations-et-animations/">
                  <li>Illustrations</li>
                </nuxt-link>
                <nuxt-link to="/shop/">
                  <li>Shop</li>
                </nuxt-link>
              </ul>
              <div>
                <img
                  class="burger-instagram"
                  src="/images/instagram.svg"
                  alt="Logo Instagram"
                />
              </div>
            </div>
        </slot>
    </div>
</template>
<script>
    export default {
        data: () => ({
          isBurgerActive: false
        }),
        methods: {
          toggle() {
              this.isBurgerActive = !this.isBurgerActive
          }
        }
    }
</script>
<style lang="scss" scoped>
$breakpoint-tablet: 1025px;
    .hidden {
        visibility: hidden;
    }

    button {
        cursor: pointer;
    }

    /* remove blue outline */
    button:focus {
        outline: 0;
    }

    .sidebar {
      position: absolute;
      top: 0;
      left: 0;
      width: 100%;
      height: 100vh;
      background-color: #E5E5E5;
      z-index: 100;
      padding: 12vw 22.667vw 20.267vw 16vw;
      transition: all 1s;
      .burger-logo {
        width: 147px;
        margin-bottom: 115px;
        @media (max-width: $breakpoint-tablet) {
          padding: 0;
          width: 35.733vw;
          position: relative;
        }
      }
      .burger-instagram {
        width: 7.467vw;
      }
      .burger-list {
        list-style: none;
        padding: 0;
        margin-bottom: 94px;
        li {
          padding: 5.333vw 0 2.667vw;
          border-bottom: 1px solid #EF0311;
          font-size: clamp(20px, 8vw, 40px);
          font-weight: bold;
        }
      }
      div {
        text-align: center;
      }
    }

    .burger-button {
        position: relative;
        height: 30px;
        width: 32px;
        display: block;
        z-index: 999;
        border: 0;
        border-radius: 0;
        background-color: transparent;
        pointer-events: all;
        transition: transform .6s cubic-bezier(.165,.84,.44,1);
    }

    .burger-bar {
        background-color: #EF0311;
        position: absolute;
        top: 50%;
        right: 6px;
        left: 6px;
        height: 2px;
        width: auto;
        margin-top: -1px;
        transition: transform .6s cubic-bezier(.165,.84,.44,1),opacity .3s cubic-bezier(.165,.84,.44,1),background-color .6s cubic-bezier(.165,.84,.44,1);
    }

    .burger-bar--1 {
        -webkit-transform: translateY(-6px);
        transform: translateY(-6px);
    }

    .burger-bar--2 {
        transform-origin: 100% 50%;
        transform: scaleX(.8);
    }

    .burger-button:hover .burger-bar--2 {
        transform: scaleX(1);
    }

    .no-touchevents .burger-bar--2:hover {
        transform: scaleX(1);
    }

    .burger-bar--3 {
        transform: translateY(6px);
    }

    #burger.active .burger-button {
        transform: rotate(-180deg);
    }

    #burger.active .burger-bar {
        background-color :#EF0311;
    }

    #burger.active .burger-bar--1 {
        transform: rotate(45deg)
    }

    #burger.active .burger-bar--2 {
        opacity: 0;
    }

    #burger.active .burger-bar--3 {
        transform: rotate(-45deg)
    }
</style>