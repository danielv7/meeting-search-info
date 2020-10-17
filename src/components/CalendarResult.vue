<template>
  <div id="calendar-result">
    <h5 v-if="calendars.length" class="vertical-left">Calendar Content</h5>
    <table>
      <thead v-if="calendars.length">
        <tr>
          <th>Meeting Title</th>
          <th>Meeting Invitees</th>
          <th>Meeting Date & Time</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="calendar in calendars" :key="calendar.id">
          <td>{{ calendar.title }}</td>
          <td>{{ calendar.invitees}}</td>
          <td>{{ calendar.date }}</td>
          <td>
            <button @click="$emit('delete-calendar', calendar.id)">Delete</button>
          </td>
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