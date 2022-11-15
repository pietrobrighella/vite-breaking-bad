<template>
    <div>
        <div class="my-card">
            <img class="img-thumbnail" :src="character.img" :alt="character.name">
        </div>
        <h4 class="pt-3">{{ character.name }}</h4>
        <h6 class="text-secondary fw-light pb-2">{{character.nickname}}</h6>
        <p class="fw-bold"><mark>{{ character.status }}</mark></p>
    </div>
</template>

<script>
    export default {
        props: {
            character: Object
        }
    }
</script>

<style lang="scss" scoped>
.my-card {
    img {
        width: 100%;
    }
}
</style>