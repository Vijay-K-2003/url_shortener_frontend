<script lang="ts">
export default {
    props: {
        minifiedURL: String
    }
}
</script>

<template>
    <div class="output">{{minifiedURL}}</div>
</template>

<style scoped>
.output {
    min-width: 30vw;
    font-size: 48px;
    border-radius: 18px;
    border: none;
    padding: 16px;
    font-family: Inter, system-ui, Avenir, Helvetica, Arial, sans-serif;
}

</style>