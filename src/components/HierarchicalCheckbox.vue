<template>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">
        <input type="checkbox" :checked="item.checked" @change="toggle(item)" />
        {{ item.name }}
        <ul class="secondList" v-if="item.showChildren">
          <li v-for="child in item.children" :key="child.id">
            <HierarchicalCheckbox :items="[child]" @toggle-child="onToggleChild" />
          </li>
        </ul>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'HierarchicalCheckbox',
  props: {
    items: {
      type: Array,
      required: true
    }
  },
  methods: {
    toggle(item) {
      item.checked = !item.checked
      item.showChildren = item.checked
      if (!item.checked) {
        this.deselectChildren(item)
      }
      this.$emit('toggle-child', item)
    },
    deselectChildren(item) {
      if (item.children) {
        item.children.forEach((child) => {
          child.checked = false
          child.showChildren = false
          this.deselectChildren(child)
        })
      }
    },
    onToggleChild(child) {
      this.$emit('toggle-child', child)
    }
  }
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 20px;
}
li {
  margin: 5px 0;
}
</style>
