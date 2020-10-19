<template>
  <div id="dropbox-result">
    <h5 v-if="dropboxs.length" class="vertical-left">Dropbox Information</h5>
    <table class="striped-table">
      <thead v-if="dropboxs.length">
        <tr>
          <th>Path</th>
          <th>Title</th>
          <th>Shared With</th>
          <th>Date Created</th>
          <th>Action</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="dropbox in dropboxs" :key="dropbox.id">
          <td>{{ dropbox.path }}</td>
          <td>{{ dropbox.title }}</td>
          <td>{{ emailFormat(dropbox.shared_with) }}</td>
          <td>{{ dateFormat(dropbox.created) }}</td>
          <td>
            <button @click="$emit('delete-dropbox', dropbox.id)">Delete</button>
            <button @click="$emit('toggle-dropboxpin', [dropbox.pin, dropbox.id])">Pin</button>
          </td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
  export default {
  name: 'dropbox-result',
  props: {
    dropboxs: Array,
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
    
  },
}
</script>

<style scoped></style>