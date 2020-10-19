<template>
  <div id="contact-result">
    <h5 v-if="contacts.length" class="vertical-left">Contact Information</h5>
    <table class="striped-table">
      <thead v-if="contacts.length">
        <tr>
          <th>Name</th>
          <th>Company</th>
          <th>Email Address</th>
          <th>Phone Number(s)</th>
          <th>Last Contact</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="contact in contacts" :key="contact.id">
          <td>{{ contact.name }}</td>
          <td>{{ contact.company }}</td>
          <td>{{ emailFormat(contact.emails) }}</td>
          <td>{{ phoneFormat(contact.phones) }}</td>
          <td>{{ dateFormat(contact.last_contact) }}</td>
          <td>
            <button class="full-button" @click="$emit('delete-contact', contact.id)">Delete</button>
            <button class="full-button" @click="$emit('toggle-contactpin', [contact.pin, contact.id])">Pin</button>
          </td>
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
  methods: {
    dateFormat(date) {
      date = String(date)
      date = new Date(date)
      date = date.toLocaleDateString()
      return date
    },
    emailFormat(email) {
      email = email.join(", ");
      return email
    },
    phoneFormat(phoneNum) {
      phoneNum = phoneNum.join(" | ")
      return phoneNum
    },

  },
}
</script>

<style scoped></style>