<template>
    <aside class="aside" data-aside>
        <button class="close-menu" @click="hiddenMenu()">
            <img src="../assets/images/icon-close.svg" alt="icon-close">
        </button>

        <ul class="aside-list">
            <li class="aside-item">
                <a href="#" class="aside-link">Collections</a>
            </li>
            <li class="aside-item">
                <a href="#" class="aside-link">Men</a>
            </li>
            <li class="aside-item">
                <a href="#" class="aside-link">Women</a>
            </li>
            <li class="aside-item">
                <a href="#" class="aside-link">About</a>
            </li>
            <li class="aside-item">
                <a href="#" class="aside-link">Contact</a>
            </li>
        </ul>
    </aside>
</template>

<script lang="ts">
export default {
    name: "Aside",
    data() {
        return {};
    },
    methods: {
        hiddenMenu: function () {
            const aside: any = document.querySelector("[data-aside]");
            const overflow: any = document.querySelector("[data-overflow]");

            aside.classList.remove("active");
            overflow.classList.remove("active");
        }
    }
}
</script>

<style scoped>
    .aside {
        width: 250px;
        position: fixed;
        top: 0;
        left: -1000px;
        bottom: 0;
        z-index: 12;
        padding: 25px 20px;
        background-color: var(--White);
        display: flex;
        flex-direction: column;
        gap: 40px;
        transition: .6s;
    }
    .aside.active {
        left: 0;
        transition: .6s;
    }
    .aside .aside-list {
        display: flex;
        flex-direction: column;
        gap: 30px;
    }
    .aside .aside-list .aside-item .aside-link {
        font-size: 1.2rem;
        font-weight: 700;
        transition: .4s;
    }
    .aside .aside-list .aside-item .aside-link:hover {
        color: var(--Dark-grayish-blue);
        transition: .4s;
    }

    /*--------------------------------------------*\
      #MEDIA
    \*--------------------------------------------*/

    /**
     * FIT SIZE 992PX
     */
     @media screen and (min-width: 992px) { .aside { display: none; } }
</style>