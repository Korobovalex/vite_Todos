<template>
    <button>
        <slot></slot>
    </button>
</template>

<script>
export default {
    name: "TheButton"
}
</script>

<style lang="scss" scoped>
button {
    padding: 8px 16px;
    border: none;

    &:hover {
        cursor: pointer;
    }
}
</style>