<template>
  <div id="seach-field" class="small-container">
    <form @submit.prevent="handleSubmit">
      <input :class="{ 'has-error': error }" v-model="searchString" type="text" placeholder="Search..."/>
      <button class="full-button">Search</button>
    </form>
    <h5 v-if="stringContent && !error" class="vertical-center">Search Results for "{{stringContent}}"</h5>
    <h5 v-if="error" class="error-message vertical-center">❗Please enter a word you would like to search❗</h5>

  </div>
</template>

<script>
  export default {
    name: 'search-field',
    data() {
      return {
          searchString: '',
          stringContent: '',
          error: false,
      }
    },
    methods: {
      handleSubmit() {
        if (this.searchString) {
          this.stringContent = this.searchString;
          this.searchString = this.lowerString
          this.$emit('search-value', this.searchString)
          this.error = false
          }
        if (this.searchString === '') {
          this.error = true
          this.searchString = '';
        }
          this.searchString = '';
        }, 
       
    },
    computed: {
      lowerString() {
        return this.searchString.toLowerCase()
      }
    },
  }
</script>

<style scoped>
  form {
    margin-top: 2rem;
    margin-bottom: 2rem;
  }
  button {
    background: #38d8a3;
    border: 1px solid #38d8a3;
  
  }
  .button:hover {
    background-color: rgb(77, 82, 78); 
    border: 1px solid rgb(77, 82, 78);
  }
</style>