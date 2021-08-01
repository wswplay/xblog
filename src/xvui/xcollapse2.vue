<template>
  <div class='xcollapse'>
    <template v-for="item in list">
      <router-link class="link" tag="div" v-if="!item.children" :key="item.path" :to="item.path">{{item.name}}</router-link>
      <div class="text" v-else :key="item.path">
        <div class="title_wrapper" @click="ToggleContent(item)">
          <div class="title">{{item.name||defaultTitle}}</div>
          <span class="icon" :class="{textRotate: item.isSpread}">></span>
        </div>
        <div class="content_wrapper" :class="{close: !item.isSpread}">
          <Xcollapse2 :list="item.children" />
        </div>
      </div>
    </template>
  </div>  
</template>

<script>

export default {
  name: 'Xcollapse2',
  props: ['list'],
  data() {
    return {
      defaultTitle: '面板标题',
      spread: false,
      curPath: 'stack'
    }
  },
  computed: {
    iconText() {
      return this.info.children && this.info.children.length ? '>' : ''
    }
  },
  methods: {
    ToggleContent(item) {
      console.log('item==', item.isSpread)
      item.isSpread = !item.isSpread
    },
    GetItemInfo(path) {
      this.curPath = path
      console.log('this.curPath', this.curPath)
    },
  }
}
</script>

<style lang='less' scoped>
.xcollapse {
  a {
    // text-decoration: none;
    // color: #333;
    // height: 100%;
    // width: 100%;
    &.router-link-exact-active {
      color: #42b983;
    }
  }
  .title_wrapper {
    padding: 16px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    cursor: pointer;
    border-bottom: 1px solid rgba(235, 234, 234, 0.6);
    // transition: all 0.6s;
    &:hover {
      background-color: #eff;
    }
    &.active {
      background-color: #eff;
      // border-bottom: 1px solid rgb(219, 250, 250);
    }
    .icon {
      transition: all 0.6s;
      &.textRotate {
        transform: rotate(90deg);
      }
    }
  }
  .content_wrapper {
    text-align: left;
    transition: all 0.6s;
    overflow: hidden;
    will-change: height;
    &.close {
      height: 0;
    }
    a, .title {
      text-indent: 10px;
    }
    .content_wrapper {
      a, .title {
        text-indent: 20px;
      }
      .content_wrapper {
        a, .title {
          text-indent: 30px;
        }
      }
    }
  }
}
</style>