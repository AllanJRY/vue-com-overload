<template>
  <div id="app">
    <TheSideNav :items="items" @item-selected="handleItemSelection" />
    <MasterView :item="selectedItem" />
  </div>
</template>

<script>
import TheSideNav from "@/components/TheSideNav";
import MasterView from "@/components/MasterView";

export default {
  name: 'App',
  components: {
    MasterView,
    TheSideNav
  },
  data() {
    return {
      selectedItem: null,
      items: [
        {
          id: 5468,
          name: 'App Escrime',
          licenceTypeChoices: [
            {
              label: 'Licence "Tireur"',
              value: 'tireur',
            },
          ],
          disciplineChoices: [
            {
              label: 'Épée',
              value: 'epee',
            },
          ],
          licences: [
            {
              LicenceType: "tireur",
              disciplines: ["epee"],
            },
            {
              LicenceType: "tireur",
              disciplines: ["epee"],
            },
          ],
        },
        {
          id: 9936,
          name: 'App Lutte',
          licenceTypeChoices: [
            {
              label: 'FFLDA',
              value: 'fflda',
            },
          ],
          disciplineChoices: [
            {
              label: 'Lutte',
              value: 'lutte',
            },
            {
              label: 'Grappling',
              value: 'grappling',
            },
            {
              label: 'Sambo',
              value: 'sambo',
            },
          ],
          licences: [
            {
              LicenceType: "fflda",
              disciplines: ["sambo", "grappling"],
            },
            {
              LicenceType: "fflda",
              disciplines: ["lutte"],
            },
          ],
        },
      ],
    };
  },
  methods: {
    handleItemSelection(selectedItem) {
      this.items.forEach(item => {
        if (item === selectedItem) this.selectedItem = selectedItem;
      });
    }
  }
}
</script>

<style lang="scss">
:root {
  --primary-color: #3F3F37;
  --secondary-color: #DE541E;
  --tertiary-color: #D6D6B1;
  --quaternary-color: #878472;
  --quinary-color: #BFBFBF;
  --danger-color: #be0000;

  --light-text-color: #f1f1f1;
}

body {
  height: 100vh;
  background-color: var(--quaternary-color);

  #app {
    height: 100%;
    display: grid;
    grid-template-columns: 250px auto;
    grid-template-rows: 100%;
    gap: 0.5rem;
    padding: 0.5rem;

    .nothing-selected {
      width: 100%;
      height: 100%;
      display: flex;
      justify-content: center;
      align-items: center;
    }
  }
}

button, input[type="submit"], input[type="button"] {
  border: 0;
  color: var(--light-text-color);
  padding: 0.5rem 1rem;
  border-radius: 7px;
  background-color: var(--secondary-color);
}
</style>
