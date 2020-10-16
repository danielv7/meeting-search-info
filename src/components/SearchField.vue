<template>
  <div id="seach-field">
    <form @submit.prevent="handleSubmit">
      <input v-model="searchString" type="text" placeholder="Search..."/>
      <button class="full-button">Search</button>
    </form>
    <h5 v-if="stringContent" class="vertical-center">Search Results for "{{stringContent}}"</h5>

  </div>
</template>

<script>
  export default {
    name: 'search-field',
    data() {
      return {
          searchString: '',
          stringContent: '',
      }
    },
    methods: {
    handleSubmit() {
      if (this.searchString) {
        console.log('testing handleSubmit')
        this.stringContent = this.searchString;
        this.$emit('search-value', this.searchString)
        }
        this.searchString = '';
      },
    },
  }
</script>

<style scoped>
  form {
    margin-top: 2rem;
    margin-bottom: 2rem;
  }
</style>