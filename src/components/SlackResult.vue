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
          <td>{{ slack.timestamp }}</td>
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
  mounted() {
    this.formatDate() 
  },
  methods: {
    formatDate() {
      console.log("mounted")

    },


  },

}
</script>

<style scoped></style>