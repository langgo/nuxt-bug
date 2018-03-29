<template>
  <div class="products-content">
    <products-row :data="row" @hoverItem="hoverItem" @hoverChildItem="hoverItem"
    ></products-row>
  </div>
</template>

<script>
import productsRow from './productsRow.vue'

export default {
  components: { productsRow },
  data () {
    return {
      row: [
        {
          title: 'Title A'
          // active: true, // Note： If active is set at the beginning, It's not going to happen
        },
        {
          title: 'Title B'
        },
        {
          title: 'Title C'
        },
        {
          title: 'Title D'
        }
      ]
    }
  },
  created () {
    if (this.row.length > 0) {
      this.hoverItem(this.row[0])
    }
  },
  methods: {
    hoverItem (_item) {
      console.log('The execution time of hoverItem: ', (new Date()).getTime())

      this.row.forEach((item) => {
        if (item === _item) {
          this.$set(item, 'active', true)
        } else {
          this.$set(item, 'active', false)
        }
      })
    }
  }
}
</script>

<style scoped>
.products-content {
  margin-top: 60px;
  border: solid 1px red;
}
</style>
