<template>
  <div id="contact-result">
    <h5 class="vertical-left">Contacts</h5>
    <table>
      <thead>
        <tr>
          <th>Name</th>
          <th>Company</th>
          <th>Email's</th>
          <th>Phone Number's</th>
          <th>Last Content</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in contacts" :key="contact.id">
          <td>{{ contact.name }}</td>
          <td>{{ contact.company }}</td>
          <td>{{ contact.emails }}</td>
          <td>{{ contact.phones }}</td>
          <td>{{ contact.last_contact }}</td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
  export default {
  name: 'content-result',
  props: {
    contacts: Array,
  },
}
</script>

<style scoped></style>