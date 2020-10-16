<template>
  <div id="slack-result">
    <h5 class="vertical-left">Slack Content</h5>
    <table>
      <thead>
        <tr>
          <th>Channel</th>
          <th>Message</th>
          <th>Date</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="slack in slacks" :key="slack.id">
          <td>{{ slack.channel }}</td>
          <td><strong>{{ slack.author }}</strong>-{{ slack.message }}</td>
          <td>{{ slack.timestamp }}</td>
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
}
</script>

<style scoped></style>