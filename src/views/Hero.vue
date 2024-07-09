<template>
    <!-- #HERO -->
    <section class="hero section">
        <div class="hero-images-mobile">
            <button class="btn btn-img-1" @click="prevSlide">
                <img src="../assets/images/icon-previous.svg" alt="icon-previous" />
            </button>
            <div class="image-container">
                <div
                v-for="(image, index) in images"
                :key="index"
                class="image-item"
                :class="{ active: currentSlide === index }"
                :data-slider="index + 1"
                >
                <img :src="image" class="img-cover" :alt="'image-product-' + (index + 1) + '-thumbnail'" />
                </div>
            </div>
            <button class="btn btn-img-2" @click="nextSlide">
                <img src="../assets/images/icon-next.svg" alt="icon-next" />
            </button>
        </div>

        <div class="hero-images-desctop">
          <img src="../assets/images/image-product-1.jpg" alt="image-product-1" class="img-hero-desctop img-cover" data-img-hero-desctop>

          <div class="image-list">
            <img src="../assets/images/image-product-1-thumbnail.jpg" alt="image-product-1-thumbnail" class="image-box img-cover active" data-image-box>
            <img src="../assets/images/image-product-2-thumbnail.jpg" alt="image-product-2-thumbnail" class="image-box img-cover" data-image-box>
            <img src="../assets/images/image-product-3-thumbnail.jpg" alt="image-product-3-thumbnail" class="image-box img-cover" data-image-box>
            <img src="../assets/images/image-product-4-thumbnail.jpg" alt="image-product-4-thumbnail" class="image-box img-cover" data-image-box>
          </div>
        </div>

        <div class="hero-body">
            <p class="text-title">Sneaker Company</p>
            <h1 class="title">Fall Limited Edition<br> Sneakers</h1>
            <p class="text">
                These low-profile sneakers are your perfect casual wear companion. Featuring a 
                durable rubber outer sole, they’ll withstand everything the weather can offer.
            </p>
            <div class="number-list">
                <h1 class="number-bold">
                    $125.00
                    <span class="an-offer">50%</span>
                </h1>
                <p class="discount">$250.00</p>
            </div>
            <div class="hero-body-bottom">
                <div class="minus-plus">
                    <button class="btn-minus-plus" @click="minusNumber()">
                        <img src="../assets/images/icon-minus.svg" alt="minus">
                    </button>

                    <span class="number">{{ counter }}</span>

                    <button class="btn-minus-plus" @click="plusNumber()">
                        <img src="../assets/images/icon-plus.svg" alt="plus">
                    </button>
                </div>

                <BtnPrimary @click="pushElement() "/>
            </div>
        </div>
    </section>

    <!-- #OVERFLOW -->
    <Overflow />
  </template>
  
<script lang="ts">
import { defineComponent } from 'vue';
import BtnPrimary from '@/components/BtnPrimary.vue'
import Overflow from '@/components/Overflow.vue'
  
export default defineComponent({
  name: 'Hero',
  data() {
    return {
      counter: 0,
      currentSlide: 0,
      images: [
        require('../assets/images/image-product-1.jpg'),
        require('../assets/images/image-product-2.jpg'),
        require('../assets/images/image-product-3.jpg'),
        require('../assets/images/image-product-4.jpg')
      ]
    };
  },
  components: {
    BtnPrimary,
    Overflow
  },
  methods: {
    nextSlide() {
        this.currentSlide = (this.currentSlide + 1) % this.images.length;
    },
    prevSlide() {
        this.currentSlide = (this.currentSlide - 1 + this.images.length) % this.images.length;
    },
    plusNumber() {
        this.counter += 1;
    },
    minusNumber() {
        if (this.counter > 0) {
            this.counter -= 1;
        };
    },
    pushElement() {
        const positionCart: any = document.querySelector("[data-position-cart]");
        const cartEmpty: any = document.querySelector("[data-cart-empty]");
        const positionCartList: any = document.querySelector("[data-position-cart-list]");
        const numberCart: any = document.querySelector("[data-number-cart]");
        const number: any = document.querySelector("[data-number]");
        const number_x: any = document.querySelector("[data-number-x]");

        let total: any = this.counter * 125.00;
        let roundedTotal: any = Math.round(total * 100) / 100;

        if (this.counter > 0) {
            cartEmpty.classList.add("active");
            positionCartList.classList.add("active");
            numberCart.classList.add("active");
            numberCart.innerHTML = this.counter;
            number.innerHTML = this.counter;
            number_x.innerHTML = roundedTotal;
        } else {
            numberCart.classList.remove("active");
            positionCart.classList.add("active");
            cartEmpty.classList.remove("active");
            positionCartList.classList.remove("active");
        }
    },
    imgList() {
      const imageBox = document.querySelectorAll<HTMLImageElement>("[data-image-box]");
      const imgHeroDesctop = document.querySelector<HTMLImageElement>("[data-img-hero-desctop]");

      if (imgHeroDesctop) {
        imageBox.forEach((ele) => {
          ele.addEventListener("click", () => {
            imageBox.forEach((item) => {
              item.classList.remove("active");
            });
            ele.classList.add("active");

            imgHeroDesctop.src = ele.src;
          });
        });
      } else {
        console.error('Element imgHeroDesctop not found');
      }
    }
  },
  mounted() {
    this.imgList();
  }
});
</script>
  
<style scoped>
  .hero {
    max-width: 1100px;
    margin: 0 auto;
    width: 100%;
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 25px;
  }
  .hero-images-mobile {
    display: flex;
    align-items: center;
    justify-content: center;
    position: relative;
  }
  .image-container {
    display: flex;
    overflow: hidden;
    width: 100%;
    max-width: 600px;
  }
  .image-item {
    display: none;
    flex-shrink: 0;
    width: 100%;
  }
  .image-item.active {
    display: block;
  }
  .img-cover {
    width: 100%;
    height: auto;
  }
  .btn {
    background-color: var(--White);
    cursor: pointer;
    width: 45px;
    height: 45px;
    border-radius: 100px;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  .btn-img-1 {
    position: absolute;
    left: 16px;
  }  
  .btn-img-2 {
    position: absolute;
    right: 16px;
  }
  .hero-images-desctop {
    display: none;
    gap: 25px;
  }
  .hero-images-desctop .img-hero-desctop { border-radius: 12px; }

  .hero-images-desctop .image-list {
    display: flex;
    align-items: center;
    justify-content: space-between;
    gap: 25px;
  }
  .hero-images-desctop .image-list .image-box {
    cursor: pointer;
    border: 3px solid transparent;
    border-radius: 12px;
    width: 100px;
    height: 100px;
    transition: .4s;
  }
  .hero-images-desctop .image-list .image-box:hover {
    opacity: 0.7;
    transition: .4s;
  }
  .hero-images-desctop .image-list .image-box.active {
    border: 3px solid var(--Orange);
    opacity: 0.7;
    transition: .4s;
  }
  .hero .hero-body { padding: 0 16px; }

  .hero .hero-body .text-title {
    font-size: 14px;
    font-weight: 600;
    text-transform: uppercase;
    color: var(--Dark-grayish-blue);
    letter-spacing: 1px;
    margin-bottom: 10px;
  }
  .hero .hero-body .title {
    font-size: 1.8rem;
    font-weight: bold;
    line-height: 1.1;
    letter-spacing: 0;
    margin-bottom: 15px;
  }
  .hero .hero-body .text {
    color: var(--Dark-grayish-blue);
    font-size: 1.1rem;
    font-weight: 600;
    margin-bottom: 20px;
  } 
  .hero .hero-body .number-list {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 20px;
  }
  .hero .hero-body .number-list .number-bold {
    font-size: 1.7rem;
    font-weight: 700;
    display: flex;
    align-items: center;
    gap: 15px;
  }
  .hero .hero-body .number-list .number-bold .an-offer {
    font-size: 1rem;
    padding: 3px 10px;
    border-radius: 6px;
    font-weight: 600;
    background-color: var(--Black);
    color: var(--White);
  }
  .hero .hero-body .number-list .discount {
    text-decoration: line-through;
    font-size: 1.1rem;
    font-weight: 600;
    color: var(--Dark-grayish-blue);
  }
  .hero .hero-body .hero-body-bottom {
    display: grid;
    grid-template-columns: repeat(1, 1fr);
    gap: 20px;
  }
  .hero .hero-body .hero-body-bottom .minus-plus {
    background-color: var(--Pale-orange);
    display: flex;
    align-items: center;
    justify-content: space-between;
    height: 64px;
    width: 100%;
  }
  .hero .hero-body .hero-body-bottom .minus-plus .number {
    font-size: 1.2rem;
    font-weight: 600;
  }
  .hero .hero-body .hero-body-bottom .btn-minus-plus {
    display: flex;
    align-items: center;
    justify-content: center;
    height: 64px;
    width: 84px;
    opacity: 1;  
    transition: .4s;
  }
  .hero .hero-body .hero-body-bottom .btn-minus-plus:hover {
    opacity: 0.7;  
    transition: .4s;
  }

    /*--------------------------------------------*\
        #MEDIA
    \*--------------------------------------------*/

    /**
        * FIT SIZE 992PX
        */
    @media screen and (min-width: 992px) {
        .hero {
            grid-template-columns: repeat(2, 1fr);
            place-content: center;
            align-items: center;
            height: calc(100vh - 113px);
            gap: 100px;
        }
        .hero-images-mobile { display: none; }

        .hero-images-desctop { display: grid; }

        .hero .hero-body { padding: 0 16px; }

        .hero .hero-body .text-title {
            font-size: 1rem;
            margin-bottom: 10px;
        }
        .hero .hero-body .title {
            font-size: 3rem;
            margin-bottom: 35px;
        }
        .hero .hero-body .number-list {
            display: flex;
            flex-direction: column;
            align-items: start;
            justify-content: start;
            margin-bottom: 25px;
        }
        .hero .hero-body .hero-body-bottom { grid-template-columns: 1fr 2fr; }
    }
</style>
