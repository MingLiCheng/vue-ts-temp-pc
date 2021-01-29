<template>
  <ConfigProvider :locale="locale">
    <div id="app">
      <PageView />
    </div>
  </ConfigProvider>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { ConfigProvider } from 'ant-design-vue'
import zhCN from 'ant-design-vue/es/locale/zh_CN'
import PageView from '@/components/layout/PageView.vue'
@Component({
  components: { PageView, ConfigProvider }
})
export default class App extends Vue {
  locale = zhCN
  created() {
    console.log('this', this)
  }
}
</script>

<style lang="less">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
