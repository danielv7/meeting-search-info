<template>
  <div id="search-result">
    <table>
      <thead>
        <tr>
          <th>Channel</th>
          <th>Author</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="employee in employees" :key="employee.id">
          <td>{{ employee.name }}</td>
          <td>{{ employee.email }}</td>
        </tr>
      </tbody>
    </table>
    
  </div>
</template>

<script>
  export default {
  name: 'search-result',
  props: {
    employees: Array,
  },
}
</script>

<style scoped></style>