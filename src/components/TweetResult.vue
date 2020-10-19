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
            <button @click="$emit('toggle-tweetpin', [tweet.pin, tweet.id])">Pin</button>
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


<style scoped>
button {
  background: #38d8a3;
  border: 1px solid #38d8a3;
  margin: 2px;
}
button:hover {
  background-color: rgb(77, 82, 78); 
  border: 1px solid rgb(77, 82, 78);
}
</style>