<template>
  <div id="app">
    <h1>Hierarchical Checkbox Component</h1>
    <HierarchicalCheckbox :items="items" @toggle-child="saveToLocalStorage" />
  </div>
</template>

<script>
import HierarchicalCheckbox from './components/HierarchicalCheckbox.vue'

export default {
  name: 'App',
  components: {
    HierarchicalCheckbox
  },
  data() {
    return {
      items: [
        {
          id: 1,
          name: 'Parent 1',
          checked: false,
          showChildren: false,
          children: [
            {
              id: 2,
              name: 'Child 1.1',
              checked: false,
              showChildren: false,
              children: [
                {
                  id: 3,
                  name: 'Sub-child 1.1.1',
                  checked: false,
                  showChildren: false,
                  children: [
                    {
                      id: 7,
                      name: 'Sub-Sub-child 1.1.1.1',
                      checked: false,
                      showChildren: false
                    },
                    {
                      id: 8,
                      name: 'Sub-Sub-child 1.1.1.2',
                      checked: false,
                      showChildren: false
                    }
                  ]
                }
              ]
            },
            {
              id: 4,
              name: 'Child 1.2',
              checked: false,
              showChildren: false
            }
          ]
        },
        {
          id: 5,
          name: 'Parent 2',
          checked: false,
          showChildren: false,
          children: [
            {
              id: 6,
              name: 'Child 2.1',
              checked: false,
              showChildren: false,
              children: [
                {
                  id: 7,
                  name: 'Sub-child 2.1.1',
                  checked: false,
                  showChildren: false
                },
                {
                  id: 8,
                  name: 'Sub-child 2.1.2',
                  checked: false,
                  showChildren: false
                }
              ]
            },
            {
              id: 9,
              name: 'Child 2.2',
              checked: false,
              showChildren: false,
              children: [
                {
                  id: 10,
                  name: 'Sub-child 2.2.1',
                  checked: false,
                  showChildren: false
                }
              ]
            }
          ]
        },
        {
          id: 11,
          name: 'Parent 3',
          checked: false,
          showChildren: false,
          children: [
            {
              id: 12,
              name: 'Child 3.1',
              checked: false,
              showChildren: false,
              children: [
                {
                  id: 13,
                  name: 'Sub-child 3.1.1',
                  checked: false,
                  showChildren: false
                }
              ]
            },
            {
              id: 14,
              name: 'Child 3.2',
              checked: false,
              showChildren: false
            }
          ]
        }
      ]
    }
  },
  methods: {
    saveToLocalStorage() {
      localStorage.setItem('hierarchicalCheckboxData', JSON.stringify(this.items))
    },
    loadFromLocalStorage() {
      const data = localStorage.getItem('hierarchicalCheckboxData')
      if (data) {
        this.items = JSON.parse(data)
      }
    }
  },
  mounted() {
    this.loadFromLocalStorage()
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 60px;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
</style>
