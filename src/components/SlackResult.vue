<template>
  <div id="slack-result">
    <h5 v-if="slacks.length" class="vertical-left">Slack Content</h5>
    <table class="striped-table">
      <thead>
        <tr v-if="slacks.length">
          <th>Channel</th>
          <th>Message</th>
          <th>Date</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="slack in slacks" :key="slack.id">
          <td>{{ slack.channel }}</td>
          <td><strong>{{ slack.author }}</strong>-{{ slack.message }}</td>
          <td>{{ dateFormat(slack.timestamp) }}</td>
          <td>
            <button @click="$emit('delete-slack', slack.id)">Delete</button>
            <button @click="$emit('toggle-slackpin', [slack.pin, slack.id])">Pin</button>
          </td>
        </tr>
      </tbody>
    </table>


  </div>
</template>

<script>
  export default {
  name: 'slack-result',
  props: {
    slacks: Array,
  },
  methods: {
    dateFormat(date) {
      date = String(date)
      date = new Date(date)
      date = date.toLocaleDateString(undefined, {hour:'numeric', minute: '2-digit' })
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