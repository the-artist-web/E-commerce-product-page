<template>
    <div class="overflow" data-overflow></div>
</template>

<script lang="ts">
export default {
    name: "Overflow",
    data() {
        return {};
    }
}
</script>

<style scoped>
    .overflow {
        position: fixed;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        width: 100%;
        height: 100vh;
        background-color: var(--Black);
        z-index: 11;
        visibility: hidden;
        opacity: 0;    
        transition: .6s;
    }
    .overflow.active {
        opacity: 0.7;
        visibility: visible;
        transition: .6s;
    }

    /*--------------------------------------------*\
      #MEDIA
    \*--------------------------------------------*/

    /**
     * FIT SIZE 992PX
     */
     @media screen and (min-width: 992px) { .overflow { display: none; } }
</style>