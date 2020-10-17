<template>
  <div id="tweet-result">
    <h5 class="vertical-left">Relevant Tweet's</h5>
    <table>
      <thead>
        <tr>
          <th>Username</th>
          <th>Message</th>
          <th>Published</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="tweet in tweets" :key="tweet.id">
          <td>{{ tweet.user }}</td>
          <td>{{ tweet.message }}</td>
          <td>{{ tweet.timestamp }}</td>
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
}
</script>

<style scoped></style>