<template>
  <div id="app" class="small-container">
    <h1 class="vertical-center">Search Upcoming Meeting Information</h1>

    <SearchField v-on:search-value="searchInput($event)"/>
    <SlackResult v-bind:slacks="slacks" />
    <ContactResult v-bind:contacts="contacts" />
    {{stringValue}}
  </div>
</template>

<script>
  import SearchField from '@/components/SearchField.vue'  
  import SlackResult from '@/components/SlackResult.vue'
  import ContactResult from '@/components/ContactResult.vue'

  export default {
    name: 'app',
    components: {
      SearchField,
      SlackResult,
      ContactResult,

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
        contacts: [
          {
            id: "12345",
            name: "John Doe",
            company: "Acme Inc",
            emails: [
              "john@acme.co",
              "doe@gmail.com"
            ],
            phones: [
              "650-555-5555",
              "+44 171 5555 5555"
            ],
            last_contact: "2019-02-26"
          },
          {
            id: "31456",
            name: "Robert Roe",
            company: "Acme Inc",
            emails: [
              "bob@acme.co"
            ],
            phones: [
              "+44 171 6666 5555"
            ],
            last_contact: "2019-02-29"
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
