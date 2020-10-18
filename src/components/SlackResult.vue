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
      //date = String(date)
      //date = new Date(date)
      //date = date.toLocaleString()
      //return date
    },
  },
 
}
</script>

<style scoped></style>