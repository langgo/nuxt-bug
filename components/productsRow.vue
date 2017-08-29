<template>
  <div class="vue-content">
    <div class="content">
      <ul class="products">
        <template v-for="item in data">
          <li :key="item.data"
              :class="[item.active ? 'active': '']"
              :active="item.active ? 'true': 'false' "
              :time="(new Date()).getTime()"
              @mouseover="onHoverItem(item)"
          >
            <div>
              <img src=""
                   :alt="item.active ? 'active: true': 'active: false'"
                   :active="item.active ? 'true': 'false' "
                   :time="(new Date()).getTime()"
              >
            </div>
            <h3>{{item.title}}</h3>
          </li>
        </template>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    data: Array
  },
  methods: {
    onHoverItem (item) {
      this.$emit('hoverItem', item)
    }
  }
}
</script>

<style scoped>
.content {
  width: 1200px;
  margin: 0 auto;
}

li {
  list-style: none;
}

ul.products {
  display: flex;
  justify-content: space-between;
}

ul.products li {
  border: solid 1px #42b983;
  width: 80px;
  text-align: center;
  cursor: pointer;
}

ul.products li h3 {
  margin-top: 20px;
  margin-bottom: 20px;
}
</style>
