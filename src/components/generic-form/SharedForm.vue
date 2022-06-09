<template>
  <form class="shared-form">
    <div class="fields-group">
      <h3 class="fields-title">Choix de la licence</h3>
      <div class="fields-group-fields">
        <select class="form-select" v-model="newLicence.LicenceType">
          <option disabled value="">Choisissez un type de licence</option>
          <option v-for="licenceType in licenceTypeChoices" :value="licenceType.value" :key="licenceType.value">{{ licenceType.label }}</option>
        </select>
      </div>
    </div>

    <div class="fields-group">
      <h3 class="fields-title">Choix des disciplines</h3>
      <div class="fields-group-fields">
        <div class="form-check" v-for="discipline in disciplineChoices" :key="discipline.value">
          <input class="form-check-input" type="checkbox" :value="discipline.value" :id="`${discipline.value}-checkbox`" v-model="newLicence.disciplines">
          <label class="form-check-label" :for="`${discipline.value}-checkbox`">
            {{ discipline.label }}
          </label>
        </div>
      </div>
    </div>

    <input type="submit" value="Valider" class="mt-5" @click.prevent />
  </form>
</template>

<script>
export default {
  name: "SharedForm",
  props: {
    licenceTypeChoices: {
      type: Array,
      required: true,
    },
    disciplineChoices: {
      type: Array,
      required: true,
    },
  },
  data() {
    return {
      newLicence: {
        LicenceType: "",
        disciplines: [],
      }
    };
  },
}
</script>

<style lang="scss" scoped>
.shared-form {
  display: flex;
  flex-direction: column;
}

.fields-title {
  text-transform: uppercase;
  padding: 1rem;
  border-bottom: 1px solid var(--primary-color);
  margin-bottom: 1rem;
}

.fields-group {
  margin-bottom: 2rem;

  .fields-group-fields {
    padding-left: 2rem;
  }
}
</style>