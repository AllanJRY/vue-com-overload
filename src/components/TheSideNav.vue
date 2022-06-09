<template>
  <nav class="side-nav">
    <button class="side-nav-item" v-for="(item) in items" :key="item.id" @click.prevent="$emit('item-selected', item)">
      {{ item.name }}
    </button>
  </nav>
</template>

<script>
export default {
  name: "TheSideNav",
  props: {
    items: Array,
  }
}
</script>

<style lang="scss" scoped>
.side-nav {
  height: 100%;
  background-color: var(--primary-color);
  display: flex;
  flex-direction: column;
  overflow: auto;
  border-radius: 7px;

  .side-nav-item {
    min-height: 50px;
    border: 0;
    background-color: transparent;
    color: var(--tertiary-color);
    transition-duration: 0.3s;
    border-radius: 0;

    &:hover {
      background-color: var(--tertiary-color);
      color: var(--quaternary-color);
    }
  }
}
</style>