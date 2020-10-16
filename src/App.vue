<template>
  <div id="app" class="small-container">
    <h1 class="vertical-center">Search Upcoming Meeting Information</h1>

    <SearchField @search:input="searchInput"/>
    <SearchResult v-bind:employees="employees" />
    {{stringValue}}
  </div>
</template>

<script>
  import SearchField from '@/components/SearchField.vue'  
  import SearchResult from '@/components/SearchResult.vue'

  export default {
    name: 'app',
    components: {
      SearchField,
      SearchResult,

    },
    data() {
      return {
        employees: [
          {
            id: 1,
            name: 'Richard Hendricks',
            email: 'richard@piedpiper.com',
          },
          {
            id: 2,
            name: 'Bertram Gilfoyle',
            email: 'gilfoyle@piedpiper.com',
          },
          {
            id: 3,
            name: 'Dinesh Chugtai',
            email: 'dinesh@piedpiper.com',
          },
        ],
      }
    },
    methods: {
      searchInput(searchString) {
        this.stringValue = searchString
        }
      }
  }

</script>

<style>
button {
  background: #38d8a3;
  border: 1px solid #38d8a3;
  
  
}
button:hover {
  background-color: rgb(77, 82, 78); 
  border: 1px solid rgb(77, 82, 78);
  
}
.small-container {
  max-width: 680px;
}
</style>
