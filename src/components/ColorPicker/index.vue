<!--
 * @Description:
 * @Author: mlcheng2
 * @Date: 2020-12-09 09:20:45
-->
<template>
  <section id="color-picker-wrapper">
    <SketchPicker
      :presetColors="presetColors"
      :disableFields="true"
      :disableAlpha="true"
      v-model="colors"
      @input="test"
    />
    <Button @click="submitChangeTheme">确定</Button>
  </section>
</template>

<script lang="ts">
import { Vue, Component } from 'vue-property-decorator'
import { Button } from 'ant-design-vue'
import { Sketch } from 'vue-color'
import { SettingsModule } from '@/store/modules/settings'
@Component({
  name: 'ColorPicker',
  components: { SketchPicker: Sketch, Button }
})
export default class ColorPicker extends Vue {
  presetColors = ['#ff4500', '#ff8c00', '#ffd700', '#41b883', '#90ee90', '#00ced1', '#1890ff', '#1e90ff']
  colors: any = '#194d33'
  test(value: any) {
    console.log('value', value)
  }
  submitChangeTheme() {
    console.log('xx', this.colors.hex)
    SettingsModule.ChangeSetting({ key: 'theme', value: this.colors.hex })
  }
}
</script>
