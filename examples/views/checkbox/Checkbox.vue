<template>
  <div>
    <h2>{{ $t('app.aside.nav.checkbox') }}</h2>
    <p class="tip">复选框</p>

    <p>
      <vxe-checkbox v-model="value1">默认尺寸</vxe-checkbox>
      <vxe-checkbox v-model="value2" size="medium">中等尺寸</vxe-checkbox>
      <vxe-checkbox v-model="value3" size="small">小型尺寸</vxe-checkbox>
      <vxe-checkbox v-model="value4" size="mini">超小尺寸</vxe-checkbox>
      <vxe-checkbox v-model="value5" indeterminate>默认尺寸</vxe-checkbox>
      <vxe-checkbox v-model="value6" size="medium" indeterminate>中等尺寸</vxe-checkbox>
      <vxe-checkbox v-model="value7" size="small" indeterminate>小型尺寸</vxe-checkbox>
      <vxe-checkbox v-model="value8" size="mini" indeterminate>超小尺寸</vxe-checkbox>
    </p>

    <p>
      <vxe-checkbox v-model="value9">复选1</vxe-checkbox>
      <vxe-checkbox v-model="value10" disabled>复选2</vxe-checkbox>
      <vxe-checkbox v-model="value11">复选3</vxe-checkbox>
    </p>

    <p>
      <vxe-checkbox-group v-model="value12">
        <vxe-checkbox label="1">HTML</vxe-checkbox>
        <vxe-checkbox label="2">CSS</vxe-checkbox>
        <vxe-checkbox label="3">Javascript</vxe-checkbox>
        <vxe-checkbox label="4">SASS</vxe-checkbox>
        <vxe-checkbox label="5">LESS</vxe-checkbox>
      </vxe-checkbox-group>
    </p>

    <pre>
      <code>
        | Tab | 切换到上一个 |
        | Shift Tab | 切换到下一个 |
        | Spacebar | 按下勾选 |
      </code>
    </pre>

    <p class="demo-code">{{ $t('app.body.button.showCode') }}</p>

    <pre>
      <code class="html">{{ demoCodes[0] }}</code>
      <code class="javascript">{{ demoCodes[1] }}</code>
    </pre>
  </div>
</template>

<script>
import hljs from 'highlight.js'

export default {
  data  () {
    return {
      value1: null,
      value2: null,
      value3: null,
      value4: null,
      value5: false,
      value6: false,
      value7: false,
      value8: false,
      value9: true,
      value10: true,
      value11: false,
      value12: ['3'],
      demoCodes: [
        `
        <p>
          <vxe-checkbox v-model="value1">默认尺寸</vxe-checkbox>
          <vxe-checkbox v-model="value2" size="medium">中等尺寸</vxe-checkbox>
          <vxe-checkbox v-model="value3" size="small">小型尺寸</vxe-checkbox>
          <vxe-checkbox v-model="value4" size="mini">超小尺寸</vxe-checkbox>
          <vxe-checkbox v-model="value5" indeterminate>默认尺寸</vxe-checkbox>
          <vxe-checkbox v-model="value6" size="medium" indeterminate>中等尺寸</vxe-checkbox>
          <vxe-checkbox v-model="value7" size="small" indeterminate>小型尺寸</vxe-checkbox>
          <vxe-checkbox v-model="value8" size="mini" indeterminate>超小尺寸</vxe-checkbox>
        </p>

        <p>
          <vxe-checkbox v-model="value9">复选1</vxe-checkbox>
          <vxe-checkbox v-model="value10" disabled>复选2</vxe-checkbox>
          <vxe-checkbox v-model="value11">复选3</vxe-checkbox>
        </p>

        <p>
          <vxe-checkbox-group v-model="value12">
            <vxe-checkbox label="1">HTML</vxe-checkbox>
            <vxe-checkbox label="2">CSS</vxe-checkbox>
            <vxe-checkbox label="3">Javascript</vxe-checkbox>
            <vxe-checkbox label="4">SASS</vxe-checkbox>
            <vxe-checkbox label="5">LESS</vxe-checkbox>
          </vxe-checkbox-group>
        </p>
        `,
        `
        export default {
          data () {
            return {
              value1: null,
              value2: null,
              value3: null,
              value4: null,
              value5: false,
              value6: false,
              value7: false,
              value8: false,
              value9: true,
              value10: true,
              value11: false,
              value12: ['3']
            }
          }
        }
        `
      ]
    }
  },
  mounted () {
    Array.from(this.$el.querySelectorAll('pre code')).forEach((block) => {
      hljs.highlightBlock(block)
    })
  }
}
</script>
