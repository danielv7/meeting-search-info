<template>
  <div id="app" class="small-container">
    <h1 class="vertical-center">Search Upcoming Meeting Information</h1>

    <SearchField v-on:search-value="searchInput($event)"/>
    <SlackResult v-bind:slacks="slacks" />
    <ContactResult v-bind:contacts="contacts" />
    <CalendarResult v-bind:calendars="calendars" />
    {{stringValue}}
  </div>
</template>

<script>
  import SearchField from '@/components/SearchField.vue'  
  import SlackResult from '@/components/SlackResult.vue'
  import ContactResult from '@/components/ContactResult.vue'
  import CalendarResult from '@/components/CalendarResult.vue'

  import { contactData } from './assets/contactData'
  import { slackData } from './assets/slackData'
  import { calendarData } from './assets/calendarData'

  export default {
    name: 'app',
    components: {
      SearchField,
      SlackResult,
      ContactResult,
      CalendarResult,

    },
    data() {
      return {
        slacks: slackData.slack,  
        contacts: contactData.contacts,
        calendars: calendarData.calendar,
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
  max-width: 700px;
}
</style>
