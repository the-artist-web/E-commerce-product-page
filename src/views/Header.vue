<template>
    <!-- #HEADER -->
    <header class="header">
        <div class="container">
            <div class="box-logo">
                <button class="menu" @click="showMenu()">
                    <img src="../assets/images/icon-menu.svg" alt="icon-menu">
                </button>

                <a href="#" class="logo">
                    <img src="../assets/images/logo.svg" alt="logo">
                </a>
            </div>

            <nav class="navbar">
                <ul class="navbar-list">
                    <li class="navbar-item">
                        <a href="#" class="navbar-link">Collections</a>
                    </li>
                    <li class="navbar-item">
                        <a href="#" class="navbar-link">Men</a>
                    </li>
                    <li class="navbar-item">
                        <a href="#" class="navbar-link">Women</a>
                    </li>
                    <li class="navbar-item">
                        <a href="#" class="navbar-link">About</a>
                    </li>
                    <li class="navbar-item">
                        <a href="#" class="navbar-link">Contact</a>
                    </li>
                </ul>

                <div class="box-right">
                    <button class="btn-cart" @click="toggleCart()">
                        <img src="../assets/images/icon-cart.svg" alt="icon-cart">
    
                        <span class="number" data-number-cart>0</span>
                    </button>
    
                    <img src="../assets/images/image-avatar.png" alt="image-avatar" class="avatar">
                </div>
            </nav>

            <div class="position-cart" data-position-cart>
                <div class="header-position-card">
                    <p class="title">Cart</p>
                </div>

                <p class="text" data-cart-empty>Your cart is empty</p>

                <div class="position-cart-list" data-position-cart-list>
                    <div class="position-cart-box">
                        <img src="../assets/images/image-product-1-thumbnail.jpg" alt="image-product-1-thumbnail" class="img-cart img-cover">

                        <div class="position-cart-box-content">
                            <p class="text-content">Fall Limited Edition Sneakers</p>
                            <div class="number">
                                $125.00 x<span class="number-2" data-number>0</span> <span class="number-bold" data-number-x>$125.00</span>
                            </div>
                        </div>

                        <button class="delete" @click="deleteCart()">
                            <i class="fa-solid fa-trash-can"></i>
                        </button>
                    </div>

                    <button class="btn-primary" @click="hiddenCart()">Checkout</button>
                </div>
            </div>
        </div>
    </header>

    <!-- #ASIDE -->
    <Aside />
    <Overflow />
</template>

<script lang="ts">
import Aside from '@/views/Aside.vue'
import Overflow from '@/components/Overflow.vue'

export default {
    name: "Header",
    data() {
        return {};
    },
    components: {
        Aside,
        Overflow
    },
    methods: {
        showMenu: function () {
            const aside: any = document.querySelector("[data-aside]");
            const overflow: any = document.querySelector("[data-overflow]");

            aside.classList.add("active");
            overflow.classList.add("active");
        },
        toggleCart: function () {
            const positionCart:any = document.querySelector("[data-position-cart]");

            positionCart.classList.toggle("active");
        },
        hiddenCart: function () {
            const positionCart:any = document.querySelector("[data-position-cart]");

            positionCart.classList.remove("active");
        },
        deleteCart: function () {
            const positionCartList:any = document.querySelector("[data-position-cart-list]");
            const cartEmpty: any = document.querySelector("[data-cart-empty]");
            const numberCart: any = document.querySelector("[data-number-cart]");
            
            numberCart.classList.remove("active");
            cartEmpty.classList.remove("active");
            positionCartList.classList.remove("active");
        }
    }
}
</script>

<style scoped>
    .header .container {
        border-bottom: 0.5px solid transparent;
        background-color: var(--Light-grayish-blue);
        height: 70px;
        width: 100%;
        position: fixed;
        top: 0;
        right: 0;
        left: 0;
        display: flex;
        align-items: center;
        gap: 70px;
        z-index: 10;
    }
    .header .container .box-logo {
        display: flex;
        align-items: center;
        gap: 15px;
    }
    .header .container .navbar {
        display: flex;
        align-items: center;
        justify-content: end;
        width: 100%;
    }
    .header .container .navbar .navbar-list {
        display: flex;
        align-items: center;
        gap: 40px;
        display: none;
    }
    .header .container .navbar .navbar-list .navbar-item .navbar-link {
        border-bottom: 4px solid transparent;
        height: 113px;
        width: max-content;
        display: flex;
        align-items: center;
        justify-content: center;
        position: relative;
        transition: .4s;
    }
    .header .container .navbar .navbar-list .navbar-item .navbar-link:hover {
        border-bottom: 4px solid var(--Orange);
        transition: .4s;
    }
    .header .container .navbar .box-right {
        display: flex;
        align-items: center;
        gap: 5px;
    }
    .header .container .navbar .box-right .btn-cart { 
        position: relative; 
        height: 40px;
        width: 40px;
        opacity: 0.7;
        transition: .4s;
    }
    .header .container .navbar .box-right .btn-cart:hover {
        opacity: 1;
        transition: .4s;
    }
    .header .container .navbar .box-right .btn-cart .number {
        background-color: var(--Orange);
        font-size: 10px;
        height: 13px;
        width: 19px;
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 100px;
        color: var(--White);
        position: absolute;
        top: 2px;
        right: 10px;
        display: none;
    }
    .header .container .navbar .box-right .btn-cart .number.active { display: flex; }

    .header .container .navbar .box-right .avatar {
        cursor: pointer;
        border-radius: 100px;
        border: 2px solid transparent;
        width: 50px;
        height: 50px;
        transition: .4s;
    }
    .header .container .navbar .box-right .avatar:hover {
        border: 2px solid var(--Orange);
        transition: .4s;
    }
    .header .container .position-cart {
        box-shadow: 0 5px 20px -15px var(--Black);
        background-color: var(--White);
        position: fixed;
        top: 50px;
        left: 16px;
        right: 16px;
        padding: 0 20px 20px;
        border-radius: 13px;
        opacity: 0;
        visibility: hidden;
        transition: .4s;
    }
    .header .container .position-cart.active {
        top: 70px;
        opacity: 1;
        visibility: visible;
        transition: .4s;
    }
    .header .container .position-cart .header-position-card {
        height: 70px;
        width: 100%;
        display: flex;
        align-items: center;
        position: relative;
        margin-bottom: 20px;
        border-bottom: 1px solid var(--Grayish-blue);
    }
    .header .container .position-cart .header-position-card .title {
        font-size: 1.2rem;
        font-weight: 600;
    }
    .header .container .position-cart .position-cart-list {
        display: flex;
        flex-direction: column;
        gap: 25px;
        display: none;
    }
    .header .container .position-cart .position-cart-list.active { display: flex; }
    
    .header .container .position-cart .text {
        color: var(--Dark-grayish-blue);
        width: 100%;
        height: 175.25px;
        display: flex;
        align-items: center;
        justify-content: center;
        font-size: 1.2rem;
        font-weight: 600;
    }
    .header .container .position-cart .text.active { display: none; }

    .header .container .position-cart .position-cart-list .position-cart-box {
        display: flex;
        align-items: center;
        justify-content: space-between;
        gap: 15px;
    }
    .header .container .position-cart .position-cart-list .position-cart-box .img-cart {
        width: 70px;
        height: 70px;
        border-radius: 6px;
    }
    .header .container .position-cart .position-cart-list .position-cart-box .position-cart-box-content {
        display: flex;
        flex-direction: column;
        gap: 5px;
    }
    .header .container .position-cart .position-cart-list .position-cart-box .position-cart-box-content .text-content {
        color: var(--Dark-grayish-blue);
        font-size: 1.1rem;
        font-weight: 500;
    }
    .header .container .position-cart .position-cart-list .position-cart-box .position-cart-box-content .number {
        display: flex;
        align-items: center;
        gap: 3px;
        color: var(--Dark-grayish-blue);
        font-size: 1rem
    }
    .header .container .position-cart .position-cart-list .position-cart-box .position-cart-box-content .number .number-bold { 
        color: var(--Very-dark-blue);
        font-weight: bold; 
        font-size: 1.1rem;
    } 
    .header .container .position-cart .position-cart-list .position-cart-box .delete {
        font-size: 1.2rem;
        color: var(--Grayish-blue);
        transition: .4s;
    }
    .header .container .position-cart .position-cart-list .position-cart-box .delete:hover {
        color: var(--Orange);
        transition: .4s;
    }
    .header .container .position-cart .position-cart-list .btn-primary {
        background-color: var(--Orange);
        padding: 20px 30px;
        width: 100%;
        border-radius: 12px;
        font-size: 1.1rem;
        font-weight: 600;
        transition: .4s;
    }
    .header .container .position-cart .position-cart-list .btn-primary:hover {
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
        .header .container {
            border-bottom: 0.5px solid var(--Grayish-blue);
            height: 113px; 
            position: relative;
            top: 0;
            right: 0;
            left: 0;
        }
        .header .container .box-logo .menu { display: none; }

        .header .container .navbar { justify-content: space-between; }

        .header .container .navbar .navbar-list { display: flex; }

        .header .container .position-cart {
            top: 80px;
            left: auto;
            right: 120px;
            padding: 0 30px 30px;
        }
        .header .container .position-cart.active { top: 100px; }

        .header .container .position-cart .text { 
            width: 396.71px; 
            height: 155.8px;
        }
    }
</style>