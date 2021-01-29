<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <Button @click="changeRouter">测试 AntDesignVue</Button>
    <div style="margin-top: 20px">
      <Button type="primary" @click="getHandler"> axios get </Button>
      <Button type="primary" @click="postHandler"> axios post </Button>
    </div>
    <div style="margin-top: 20px">
      <ColorPicker />
    </div>
  </div>
</template>

<script lang="ts">
import { Button, Icon, Upload } from 'ant-design-vue'
import { Component, Prop, Vue } from 'vue-property-decorator'
import ColorPicker from '@/components/ColorPicker/index.vue'
import Api from '@/api'

@Component({
  components: { Button, Upload, Icon, ColorPicker }
})
export default class HelloWorld extends Vue {
  @Prop() private msg!: string
  fileList: Array<any> = []
  uploading = false
  created() {
    console.log('created')
    console.log('Api', Api)
  }
  async postHandler() {
    const res = await Api.test.postProvinceList(
      { a: 'xx', b: 'yyy' },
      { headers: { 'Content-Type': 'application/json' } }
    )
    console.log('res', res)
  }
  async getHandler() {
    const res = await Api.test.getProvinceList({ a: 'xx', b: 'yyy' })
    console.log('res', res)
  }
  changeRouter() {
    this.$router.push('/about')
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="less">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
