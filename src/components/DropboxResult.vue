<template>
  <div id="dropbox-result">
    <h5 v-if="dropboxs.length" class="vertical-left">Dropbox Information</h5>
    <table>
      <thead v-if="dropboxs.length">
        <tr>
          <th>Path</th>
          <th>Title</th>
          <th>Shared With</th>
          <th>Date Created</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="dropbox in dropboxs" :key="dropbox.id">
          <td>{{ dropbox.path }}</td>
          <td>{{ dropbox.title }}</td>
          <td>{{ dropbox.shared_with }}</td>
          <td>{{ dropbox.created }}</td>
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
}
</script>

<style scoped></style>