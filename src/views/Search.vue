<template>
  <div class="wrapper">
    <Claim/>
    <SearchInput v-model="searchValue" @input="handleInput"/>
  </div>
</template>

<script>
// @ is an alias to /src

import axios from 'axios';
import debounce from 'lodash.debounce';
import Claim from '../components/Claim.vue';
import SearchInput from '../components/SearchInput.vue';

const API = 'https://images-api.nasa.gov';

export default {
  name: 'Search',
  components: {
    SearchInput,
    Claim,
  },
  data() {
    return {
      searchValue: '',
      results: [],
    };
  },
  methods: {
    // eslint-disable-next-line
    handleInput: debounce(function () {
      axios.get(`${API}/search?q=${this.searchValue}&media_type=image`)
        .then((response) => {
          this.results = response.data.collection.items;
        })
        .catch((error) => {
          console.log(error);
        });
    }, 500),
  },
};
</script>

<style lang="scss" scoped>
  .wrapper {
    margin: 0;
    width: 100%;
    height: 100vh;
    padding: 30px;

    display: flex;
    align-items: center;
    justify-content: center;
    flex-direction: column;

    color: white;
    background-image: url("../assets/heroimage.jpg");
    background-repeat: no-repeat;
    background-size: cover;
    background-position: 50% 0%;
  }
</style>
