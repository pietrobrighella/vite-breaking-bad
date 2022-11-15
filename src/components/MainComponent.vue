<template>
    <section class="container">
        <div class="text-center" v-if="store.loading">
            <img src="../assets/img/loading.gif" alt="loading...">
            <h5 class="text-secondary fw-regular">Sto caricando caxxo ...</h5>
        </div>
        <div class="row m-auto px-0" v-if="!store.loading">
            <div class="col-12 col-sm-6 col-md-4 col-lg-3 mb-5" v-for="(item, index) in store.characterList" :key="item.char_id">
                <CardComponent :character="item" />
            </div>
        </div>
    </section>
</template>

<script>
import { store } from '../store';
import CardComponent from './CardComponent.vue';
    export default {
    components: { CardComponent },
    data() {
        return {
            store,
            created() {
                console.log('ciao')
            }
        }
    }
}
</script>

<style lang="scss" scoped>

</style>