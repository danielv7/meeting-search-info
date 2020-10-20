<template>
  <div id="calendar-result">
    <h5 v-if="calendars.length" class="vertical-left">Calendar Content</h5>
    <table class="striped-table">
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
          <td>{{ dateFormat(calendar.date) }}</td>
          <td>
            <button @click="$emit('delete-calendar', calendar.id)">Delete</button>
            <button v-if="calendar.pin ===false" @click="$emit('toggle-calendarpin', [calendar.pin, calendar.id])">Pin</button>
            <button v-else @click="$emit('toggle-calendarpin', [calendar.pin, calendar.id])">Un-pin</button>
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