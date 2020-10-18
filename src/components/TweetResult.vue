<template>
  <div id="tweet-result">
    <h5 v-if="tweets.length" class="vertical-left">Relevant Tweet's</h5>
    <table class="striped-table">
      <thead v-if="tweets.length">
        <tr>
          <th>Username</th>
          <th>Message</th>
          <th>Published</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="tweet in tweets" :key="tweet.id">
          <td>{{ tweet.user }}</td>
          <td>{{ tweet.message }}</td>
          <td>{{ dateFormat(tweet.timestamp) }}</td>
          <td>
            <button @click="$emit('delete-tweet', tweet.id)">Delete</button>
          </td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
  export default {
  name: 'tweet-result',
  props: {
    tweets: Array,
  },
  methods: {
    dateFormat(date) {
      date = String(date)
      date = new Date(date)
      date = date.toLocaleDateString()
      return date
      
    },
  },
}
</script>

<style scoped></style>