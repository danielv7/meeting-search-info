<template>
  <div id="calendar-result">
    <h5 class="vertical-left">Calendar Content</h5>
    <table>
      <thead>
        <tr>
          <th>Meeting Title</th>
          <th>Meeting Invitees</th>
          <th>Meeting Date & Time</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="calendar in calendars" :key="calendar.id">
          <td>{{ calendar.title }}</td>
          <td>{{ calendar.invitees}}</td>
          <td>{{ calendar.date }}</td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
  export default {
  name: 'calendar-result',
  props: {
    calendars: Array,
  },
}
</script>

<style scoped></style>