<template>
  <div v-if="null === item" class="master-view nothing-selected">
    <h2>Aucune sélection.</h2>
  </div>
  <div v-else class="master-view">
    <div class="master-view-header">
      <h2>{{ item.name }}</h2>
      <div class="actions">
        <button>Supprimer</button>
        <button @click="() => creation = !creation">{{ !creation ? "Nouvelle licence" : "Retour" }}</button>
        <button>Suivant</button>
      </div>
    </div>
    <div class="master-view-body">
      <MasterViewDetails v-if="!creation" :item="item" />
      <SharedForm
          v-else-if="creation"
          :discipline-choices="item.disciplineChoices"
          :licence-type-choices="item.licenceTypeChoices"
      >
      </SharedForm>
    </div>
  </div>
</template>

<script>
import MasterViewDetails from "@/components/MasterViewDetails";
import SharedForm from "@/components/generic-form/SharedForm";
export default {
  name: "MasterView",
  components: {SharedForm, MasterViewDetails},
  props: {
    item: {
      type: Object,
      default: null,
    },
  },
  data() {
    return {
      creation: false,
    };
  },
}
</script>

<style lang="scss" scoped>
.master-view {
  width: 100%;
  height: 100%;
  border-radius: 7px;

  background-color: var(--tertiary-color);
  overflow: hidden;
  .master-view-header {
    background-color: var(--primary-color);
    color: var(--quaternary-color);
    padding: 0.5rem;
    display: flex;
    justify-content: space-between;
    align-items: center;

    .actions {
      button {
        margin-left: 0.5rem;
      }
    }
  }

  .master-view-body {
    padding: 0.5rem;
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }
}
</style>