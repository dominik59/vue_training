<template>
  <div class="searchInputWrapper">
    <input
      name="search"
      id="search"
      :value="value"
      @input="handleChange"
    >
    <ul>
      <li v-for="result in results" v-bind:key="result.data[0].nasa_id">
        {{result.data[0].title}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'SearchInput',
  props: {
    value: {
      type: String,
      required: true,
    },
  },
  methods: {
    handleChange(e) {
      console.log(e.target.value);
      this.$emit('input', e.target.value);
    },
  },
};
</script>

<style lang="scss" scoped>
  .searchInputWrapper {
    width: 250px;
    display: flex;
    flex-direction: column;

    input {
      height: 30px;
      border: 0;
      border-bottom: 1px solid white;
      font-weight: 300;
      text-align: center;
      background: none;
      transition: box-shadow .3s ease-out;
      color: white;
    }

    input:focus, input:hover {
      outline: none;
      box-shadow: 0 10px 20px -8px rgba(255, 255, 255, .3);
    }

  }
</style>
