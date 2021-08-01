<template>
  <div class="stack">
      <div
        class="stack-item"
        v-for="item in cateArr"
        :key="item.id"
        :class="{active: item.id==curId}"
        @click="changeAction(item.id)"
        ref="nanzhi"
      >{{item.name}}</div>
      <HelloWorld ref="world" />
  </div>
</template>

<script>
import HelloWorld from './HelloWorld'
export default {
  name: 'Stack',
  components: { HelloWorld},
  data() {
    return {
      cateArr: [
        {id: 1, name: 'one'},
        {id: 2, name: 'two'},
        {id: 3, name: 'three'},
      ],
      curId: 1
    }
  },
  created() {
  },
  methods: {
    changeAction(id) {
      this.curId = id

      // 如果ref不绑定变量，那么for中，就是一个数组
      this.$refs.nanzhi[0].innerText = '我是谁，我在哪儿'

      // world
      // console.log('this.refs', this.$refs)
      this.$refs.world.sayChina()

      // $el
      // console.log('$el', this.$el)
      this.$el.innerText = '沈从文是最棒的！！！'
    }
  }
}
</script>

<style lang="less" scoped>
.stack {
  text-align: left;
  // color: #fff;
  // font-size: 50px;
  // line-height: 300px;
  // background-color: rgb(224, 204, 178);
  // .cate-list {
  //   width: 200px;
  // }
  .stack-item {
    line-height: 50px;
    border: 1px solid #aaa;
    &.active {
      background-color: burlywood;
    }
  }
}
</style>