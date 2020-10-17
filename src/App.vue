<template>
  <div id="app" class="small-container">
    <h1 class="vertical-center">Search Upcoming Meeting Information</h1>

    <SearchField v-on:search-value="searchInput($event)"/>
    <SlackResult v-bind:slacks="slacks" />
    <ContactResult v-bind:contacts="contacts" />
    <CalendarResult v-bind:calendars="calendars" />
    <DropboxResult v-bind:dropboxs="dropboxs" />
    <TweetResult v-bind:tweets="tweets" />

    {{stringValue}}
  </div>
</template>

<script>
  import SearchField from '@/components/SearchField.vue'  
  import SlackResult from '@/components/SlackResult.vue'
  import ContactResult from '@/components/ContactResult.vue'
  import CalendarResult from '@/components/CalendarResult.vue'
  import DropboxResult from '@/components/DropboxResult.vue'
  import TweetResult from '@/components/TweetResult.vue'
  
  import { slackData } from './assets/slackData'
  import { contactData } from './assets/contactData'
  import { calendarData } from './assets/calendarData'
  import { dropboxData } from './assets/dropboxData'
  import { tweetData } from './assets/tweetData'

  export default {
    name: 'app',
    components: {
      SearchField,
      SlackResult,
      ContactResult,
      CalendarResult,
      DropboxResult,
      TweetResult,

    },
    data() {
      return {
        slacks: slackData.slack,  
        contacts: contactData.contacts,
        calendars: calendarData.calendar,
        dropboxs: dropboxData.dropbox,
        tweets: tweetData.tweet,
        stringValue: '',
      }
    },



    methods: {
      searchInput(searchString) {
        this.stringValue = searchString
        this.slacks = ''
        },

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
