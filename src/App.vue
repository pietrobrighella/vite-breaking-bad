<template>
  <main>
    <div class="container d-flex justify-content-between align-items-center">
      <h1 class="my-5">Breacking Bad Api</h1>
      <div class="d-flex">
        <select v-model="store.category" @change="getCharacters(store.category)" class="form-select h-50 w-100">
          <option value="">All category</option>
          <option :value="status" v-for="(status, index) in statusOptions" :key="index">{{status}}</option>
        </select>
      </div>
    </div>
    <MainComponent />
  </main>
</template>

<script>
import axios from 'axios';
import MainComponent from './components/MainComponent.vue';
import { store } from './store';

  export default {
    data() {
        return {
            store,
            endPoint: "characters",
            statusOptions: [
              'Breaking Bad',
              'Better Call Saul'
            ]
          }
      },
    methods: {
        setFilter() {
          store.category = this.status
        },

        getCharacters(filter) {
            store.loading = true;
            if (store.category === '') {
              const apiUrl = store.apiURL + this.endPoint
              axios.get(apiUrl).then((res) => {
                  store.characterList = res.data;
                  store.loading = false;
                  console.log(apiUrl)
              });
            } else {
              const apiUrl = store.apiURL + this.endPoint + '?category=' + store.category
              axios.get(apiUrl).then((res) => {
                  store.characterList = res.data;
                  store.loading = false;
                  console.log(apiUrl)
              });
            }

            // const apiUrl = store.apiURL + this.endPoint
            // axios.get(apiUrl).then((res) => {
            //     store.characterList = res.data;
            //     store.loading = false;
            //     console.log(apiUrl)
            // });
        }
    },
    created() {
        this.getCharacters();
    },
    components: { MainComponent }
  }
</script>

<style lang="scss" scoped>

</style>