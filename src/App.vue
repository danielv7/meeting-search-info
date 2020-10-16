<template>
  <div id="app" class="small-container">
    <h1 class="vertical-center">Search Upcoming Meeting Information</h1>

    <SearchField v-on:search-value="searchInput($event)"/>
    <SearchResult v-bind:slacks="slacks" />
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
        slacks: [
          {
            id: "12345",
            channel: "chatter",
            author: "alice",
            message: "Who's up for lunch right now?",
            timestamp: "2019-02-26 11:00:00",
          },
          {
            id: "12346",
            channel: "chatter",
            author: "bob",
            message: "I am up for lunch!",
            timestamp: "2019-02-26 11:00:01",
          },
          {
            id: "12347",
            channel: "chatter",
            author: "carol",
            message: "Me too @alice!",
            timestamp: "2019-02-26 11:00:02",
          },
        ],
        stringValue: '',
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
