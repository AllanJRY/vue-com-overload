<template>
  <table class="details-table">
    <tr>
      <th>Nom</th>
      <td>{{item.name}}</td>
    </tr>
    <tr>
      <th>Licences enregistrées</th>
      <td>
        <table class="licence-table">
          <thead>
          <tr>
            <th>Type de licence</th>
            <th>Disciplines</th>
          </tr>
          <tr v-for="licence in item.licences">
            <td>{{ licence.LicenceType }}</td>
            <td>
              {{ licence.disciplines }}
            </td>
          </tr>
          </thead>
        </table>
      </td>
    </tr>
  </table>
</template>

<script>
export default {
  name: "MasterViewDetails",
  props: {
    item: {
      type: Object,
      required: true,
    },
  },
}
</script>

<style lang="scss" scoped>

.details-table {
  th {
    vertical-align: top;
  }

  td, th {
    padding: 0.5rem;
  }

  .licence-table {
    width: 100%;
    border-collapse: collapse;
    border: 1px solid var(--primary-color);
  }
}
</style>