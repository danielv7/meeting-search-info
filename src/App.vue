<template>
  <div id="app" class="medium-container">
    <h1 class="vertical-center">Search Upcoming Meeting Information</h1>

    <SearchField 
      v-on:search-value="searchInput($event)"
    />
    <SlackResult 
      v-bind:slacks="slacks" 
      v-on:delete-slack="deleteSlack($event)"
      v-on:toggle-slackpin="toggleSlackPin($event)"
    />
    <ContactResult 
      v-bind:contacts="contacts"
      v-on:delete-contact="deleteContact($event)"
      v-on:toggle-contactpin="toggleContactPin($event)" 
    />
    <CalendarResult 
      v-bind:calendars="calendars"
      v-on:delete-calendar="deleteCanendar($event)"  
      v-on:toggle-calendarpin="toggleCalendarPin($event)"
    />
    <DropboxResult 
      v-bind:dropboxs="dropboxs"
      v-on:delete-dropbox="deleteDropbox($event)" 
      v-on:toggle-dropboxpin="toggleDropboxPin($event)"
    />
    <TweetResult 
      v-bind:tweets="tweets" 
      v-on:delete-tweet="deleteTweet($event)" 
      v-on:toggle-tweetpin="toggleTweetPin($event)"
    />

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
        slacks: [],  
        contacts: [],
        calendars: [],
        dropboxs: [],
        tweets: [],
        stringValue: '',
      }
    },

    methods: {
      searchInput(searchString) {
        this.stringValue = searchString

        this.slacks = slackData.slack
        this.slacks = this.slacks.filter(slack => 
        slack.matching_terms.includes(searchString))

        this.contacts = contactData.contacts
        this.contacts = this.contacts.filter(contact =>
        contact.matching_terms.includes(searchString))

        this.calendars = calendarData.calendar
        this.calendars = this.calendars.filter(calendar =>
        calendar.matching_terms.includes(searchString))

        this.dropboxs = dropboxData.dropbox
        this.dropboxs = this.dropboxs.filter(dropbox =>
        dropbox.matching_terms.includes(searchString))

        this.tweets = tweetData.tweet
        this.tweets = this.tweets.filter(tweet =>
        tweet.matching_terms.includes(searchString))
        },
      deleteSlack(id) {
        this.slacks = this.slacks.filter(
          slack => slack.id !== id
        )
      },
      deleteContact(id) {
        this.contacts = this.contacts.filter(
          contact => contact.id !== id
        )
      },
      deleteCanendar(id) {
        this.calendars = this.calendars.filter(
          calendar => calendar.id !== id
        )
      },
      deleteDropbox(id) {
        this.dropboxs = this.dropboxs.filter(
          dropbox => dropbox.id !== id
        )
      },
      deleteTweet(id) {
        this.tweets = this.tweets.filter(
          tweet => tweet.id !== id
        )
      },
      toggleSlackPin(pinid) {
        console.log(pinid[0])
        console.log(pinid[1])
        for (const slack of this.slacks) {
          if (slack.id === pinid[1]) {
            slack.pin = !pinid[0]
            this.fillterSlacks()
          }
        }
      },
      fillterSlacks() {
        this.slacks = this.slacks.sort((x,y) => Number(y.pin) - Number(x.pin))
      },
      toggleContactPin(pinid) {
        for (const contact of this.contacts) {
          if (contact.id === pinid[1]) {
            contact.pin = !pinid[0]
            this.fillterContacts()
          }
        }
      },
      fillterContacts() {
        this.contacts = this.contacts.sort((x,y) => Number(y.pin) - Number(x.pin))
      },
      toggleCalendarPin(pinid) {
        for (const calendar of this.calendars) {
          if (calendar.id === pinid[1]) {
            calendar.pin = !pinid[0]
            this.fillterCalendars()
          }
        }
      },
      fillterCalendars() {
        this.calendars = this.calendars.sort((x,y) => Number(y.pin) - Number(x.pin))
      },
      toggleDropboxPin(pinid) {
        for (const dropbox of this.dropboxs) {
          if (dropbox.id === pinid[1]) {
            dropbox.pin = !pinid[0]
            this.fillterDropboxs()
          }
        }
      },
      fillterDropboxs() {
        this.dropboxs = this.dropboxs.sort((x,y) => Number(y.pin) - Number(x.pin))
      },
      toggleTweetPin(pinid) {
        for (const tweet of this.tweets) {
          if (tweet.id === pinid[1]) {
            tweet.pin = !pinid[0]
            this.fillterTweets()
          }
        }
      },
      fillterTweets() {
        this.tweets = this.tweets.sort((x,y) => Number(y.pin) - Number(x.pin))
      },
    },
  }

</script>

<style>
button {
  background: #38d8a3;
  border: 1px solid #38d8a3;
  margin: 2px;
  
}
button:hover {
  background-color: rgb(77, 82, 78); 
  border: 1px solid rgb(77, 82, 78);
}

.medium-container {
  max-width: 1000px;
}

.small-container {
  max-width: 700px;
}

.error-message {
    color: #d33c40;
  }
</style>
