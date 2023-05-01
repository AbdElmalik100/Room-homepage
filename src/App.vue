<template>
  <main>
    <div class="top d-flex flex-column flex-md-row">
      <div :class="`overlay ${openMenu ? 'open' : ''}`"></div>
      <div class="left flex-fill position-relative">
        <div id="slider" class="carousel slide" data-bs-ride="carousel">
          <div class="carousel-inner">
            <div class="carousel-item active">
              <img src="/images/desktop-image-hero-1.jpg" class="desk d-block w-100" alt="">
              <img src="/images/mobile-image-hero-1.jpg" class="mobile d-block w-100" alt="">
            </div>
            <div class="carousel-item">
              <img src="/images/desktop-image-hero-2.jpg" class="desk d-block w-100" alt="">
              <img src="/images/mobile-image-hero-2.jpg" class="mobile d-block w-100" alt="">
            </div>
            <div class="carousel-item">
              <img src="/images/desktop-image-hero-3.jpg" class="desk d-block w-100" alt="">
              <img src="/images/mobile-image-hero-3.jpg" class="mobile d-block w-100" alt="">
            </div>
          </div>
        </div>
        <header class="d-flex align-items-center gap-5 p-5 position-absolute">
          <img @click="openMenu = true" class="menu" src="/images/icon-hamburger.svg" alt="">
          <h2 class="logo mb-0">room</h2>
          <ul :class="`d-flex aling-items-center gap-4 ${openMenu ? 'open' : ''}`">
            <img @click="openMenu = false" class="close" src="/images/icon-close.svg" alt="">
            <li>home</li>
            <li>shop</li>
            <li>about</li>
            <li>contact</li>
          </ul>
        </header>
      </div>
      <div class="right position-relative d-flex align-items-center justify-content-center py-5">
        <div class="info">
          <h1 class="fw-bold mb-0">Discover innovative ways to decorate</h1>
          <p class="my-3">We provide unmatched quality, comfort, and style for property owners across the country. Our
            experts combine
            form and function in bringing your vision to life. Create a room in your own style with our collection and
            make your property a reflection of you and what you love.</p>
          <span class="text-uppercase d-flex align-items-center gap-3">Shop now <span class="arrow">&rarr;</span></span>
        </div>
        <div class="butns d-flex aling-items-center position-absolute">
          <div class="flex-fill d-flex align-items-center justify-content-center" type="button" data-bs-target="#slider"
            data-bs-slide="prev">
            <img class="p-4" src="/images/icon-angle-left.svg" alt="">
          </div>
          <div class="flex-fill d-flex align-items-center justify-content-center" type="button" data-bs-target="#slider"
            data-bs-slide="next">
            <img class="p-4" src="/images/icon-angle-right.svg" alt="">
          </div>
        </div>
      </div>
    </div>
    <div class="bottom">
      <div class="d-flex align-items-center justify-content-center flex-column flex-md-row">
        <div class="image">
          <img class="w-100 h-100" src="/images/image-about-dark.jpg" alt="">
        </div>
        <div class="about px-5 p-3">
          <h2 class="mb-3 text-uppercase fw-bold">About our furniture</h2>
          <p class="mb-0">Our multifunctional collection blends design and function to suit your individual taste. Make
            each room
            unique, or pick a cohesive theme that best express your interests and what inspires you. Find the furniture
            pieces you need, from traditional to contemporary styles or anything in between. Product specialists are
            available to help you create your dream space.</p>
        </div>
        <div class="image">
          <img class="w-100 h-100" src="/images/image-about-light.jpg" alt="">
        </div>
      </div>
    </div>
  </main>
</template>
<script setup>
import { ref, watch } from 'vue'

const openMenu = ref(false)

watch(openMenu, newVal => {
  if (newVal) {
    document.body.style.overflow = 'hidden'
  } else document.body.style.overflow = 'visible'
})


</script>
<style lang="scss">
* {
  box-sizing: border-box;
}

:root {
  // ### Primary

  --Dark-Gray: hsl(0, 0%, 63%);
  --Black: hsl(0, 0%, 0%);
  --White: hsl(0, 0%, 100%);
  --Very-Dark-Gray: hsl(0, 0%, 27%);
}

body {
  font-family: 'League Spartan', sans-serif;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

.menu {
  display: none;
}

.close {
  display: none;
}

.mobile {
  display: none !important;
}

main {
  .top {
    .left {
      width: 840px;
      height: 100%;

      header {
        color: var(--White);
        top: 0;
        left: 0;
        width: 100%;

        ul {
          li {
            cursor: pointer;
            position: relative;

            &::before {
              content: '';
              position: absolute;
              bottom: 0;
              left: 50%;
              transform: translateX(-50%);
              height: 2px;
              transition: 0.2s;
              width: 0;
              background-color: var(--White);
            }

            &:hover::before {
              width: 100%;
            }
          }
        }
      }
    }

    .right {
      width: calc(100% - 840px);
      padding-left: 70px;
      padding-right: 70px;

      .info {
        h1 {
          color: var(--Black);
        }

        p {
          color: var(--Dark-Gray);
          font-size: 15px;
        }

        span {
          letter-spacing: 10px;
          color: var(--Black);
          cursor: pointer;
          transition: 0.2s;

          .arrow {
            font-size: 30px;
          }

          &:hover {
            opacity: 0.5;
          }
        }
      }

      .butns {
        bottom: 0;
        left: 0;
        width: 170px;
        user-select: none;
        &>div {
          cursor: pointer;
          background-color: var(--Black);
          transition: 0.2s;

          &:hover {
            background-color: var(--Very-Dark-Gray);
          }

          img {
            pointer-events: none;
          }
        }
      }
    }
  }

  .bottom {
    .image {
      width: 340px;
      height: 266px;
    }
    .about {
      flex: 1;

      h2 {
        color: var(--Black);
        font-size: 18px;
        letter-spacing: 6px;
      }

      p {
        color: var(--Dark-Gray);
        font-size: 15px;
      }
    }
  }

  @media (max-width: 767px) {
    .overlay {
      position: absolute;
      background-color: #00000075;
      width: 100%;
      height: 100%;
      transition: 0.2s;
      top: 0;
      opacity: 0;
      left: 0;
      z-index: -555;

      &.open {
        opacity: 1;
        z-index: 555;
      }
    }
    .desk {
      display: none !important;
    }
    .mobile {
      display: block !important;
    }
    .menu {
      display: block;
      position: absolute;
      left: 50px;
    }

    .close {
      display: block !important;
      position: absolute;
      left: 34px;
      top: 50%;
      transform: translateY(-50%);
    }

    .top {
      .left {
        width: 100% !important;
        header {
          position: relative;
          justify-content: center;

          ul {
            transform: translateY(-100%);
            transition: 0.2s;
            position: fixed;
            padding: 50px;
            z-index: 5555;
            justify-content: flex-end !important;
            width: 100%;
            justify-content: center;
            background: var(--White);
            top: 0;
            color: var(--Black) !important;
            font-weight: bold;

            &.open {
              transform: translateY(0);
            }
          }
        }
      }

      .right {
        width: 100% !important;
        padding-left: 50px !important;
        padding-right: 50px !important;

        .butns {
          top: -72px;
          right: 0;
          left: initial;
          bottom: initial;
        }
      }
    }

    .bottom {
      .image {
        width: 100%;
        height: 100%;
      }
      .about {
        h2 {
          font-size: 15px;
        }

        padding: 50px !important;
      }
    }
  }
}
</style>