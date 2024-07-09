<template>
    <button class="btn-primary">
        <i class="fa-solid fa-cart-shopping"></i>
        <span>Add to cart</span>
    </button>
</template>

<script lang="ts">
export default {
    name: "BtnPrimary",
    data() {
        return {};
    },
    methods: {

    }
}
</script>

<style scoped>
    .btn-primary {
        background-color: var(--Orange);
        padding: 22px 30px;
        width: 100%;
        border-radius: 12px;
        font-size: 1.1rem;
        font-weight: 700;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 10px;
        transition: .4s;
    }
    .btn-primary:hover {
        opacity: 0.7;
        transition: .4s;
    }
</style>