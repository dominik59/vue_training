<template>
  <div class="wrapper">
    <div class="search">
      <label for="search">Search</label>
      <input name="search" id="search" v-model="searchValue" @input="handleInput">
      <ul>
        <li v-for="result in results" v-bind:key="result.data[0].nasa_id">
          {{result.data[0].title}}
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src

import axios from 'axios';
import debounce from 'lodash.debounce';

const API = 'https://images-api.nasa.gov';

export default {
  name: 'Search',
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
    padding: 30px;
    display: flex;
    align-items: center;
    flex-direction: column;
  }

  .search {
    display: flex;
    flex-direction: column;
    width: 250px;

    label {
      font-family: Montserrat, sans-serif;
    }

    input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid black;
    }
  }
</style>
