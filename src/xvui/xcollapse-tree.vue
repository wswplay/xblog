<template>
  <div class='xcollapseTree'>
    <Xcollapse v-for="item in list" :key="item.path" :info="item" />
    <!-- <Xcollapse2 :list="list" /> -->
  </div>
</template>

<script>
import Xcollapse from './xcollapse'
import Xcollapse2 from './xcollapse2'
export default {
  name: 'XcollapseTree',
  props: ['list'],
  components: { Xcollapse, Xcollapse2 },
  data() {
    return {}
  },
}
</script>

<style lang='less' scoped>

</style>