<template>
  <div>
    <p class="tip">
      可编辑渲染 <table-column-api-link prop="edit-render"/>，查看 <a class="link" href="https://github.com/x-extends/vxe-table/tree/master/examples/plugins/xtable/renderer">示例的源码</a><span class="red">（具体请自行实现，该示例仅供参考）</span><br>
      配置参数：<br>
      autofocus 自动聚焦的类名<br>
      renderHeader (h, renderOpts, <vxe-tooltip content="{ column, columnIndex, columnIndex, $rowIndex, $table }" enterable><i class="fa fa-question-circle"></i></vxe-tooltip>params) 表头<br>
      renderEdit (h, renderOpts, <vxe-tooltip content="{ row, rowIndex, $rowIndex, column, columnIndex, $columnIndex, $table }" enterable><i class="fa fa-question-circle"></i></vxe-tooltip>params) 表内容-编辑<br>
      renderCell (h, renderOpts, <vxe-tooltip content="{ row, rowIndex, $rowIndex, column, columnIndex, $columnIndex, $table }" enterable><i class="fa fa-question-circle"></i></vxe-tooltip>params) 表内容-显示<br>
      renderFooter (h, renderOpts, <vxe-tooltip content="{ column, columnIndex, $columnIndex, $rowIndex, _columnIndex, items, $table }" enterable><i class="fa fa-question-circle"></i></vxe-tooltip>params) 表尾<br>
      editCellExportMethod (<vxe-tooltip content="{ row, column }" enterable><i class="fa fa-question-circle"></i></vxe-tooltip>params) 单元格导出函数<br>
      footerCellExportMethod (<vxe-tooltip content="{ items, _columnIndex }" enterable><i class="fa fa-question-circle"></i></vxe-tooltip>params) 表尾单元格导出函数<br>
    </p>

    <vxe-table
      border
      show-overflow
      :data="tableData"
      :edit-config="{trigger: 'click', mode: 'row'}">
      <vxe-table-column type="seq" width="60"></vxe-table-column>
      <vxe-table-column field="address2" title="简单输入框" :edit-render="{name: 'MyInput'}"></vxe-table-column>
      <vxe-table-column field="name" title="下拉表格" :edit-render="{name: 'EditDownTable', props: {checkField: 'name'}}"></vxe-table-column>
      <vxe-table-column field="nickname" title="Nickname" :edit-render="{name: 'EditPopupModal'}"></vxe-table-column>
      <vxe-table-column field="address" title="文本域" :edit-render="{name: 'EditDownTextarea'}"></vxe-table-column>
      <vxe-table-column field="role" title="复杂渲染" :edit-render="{name: 'EditDownModal', props: {checkField: 'role'}}"></vxe-table-column>
    </vxe-table>

    <p class="demo-code">{{ $t('app.body.button.showCode') }}</p>

    <pre>
      <code class="javascript">{{ demoCodes[0] }}</code>
      <code class="xml">{{ demoCodes[1] }}</code>
      <code class="javascript">{{ demoCodes[2] }}</code>
    </pre>
  </div>
</template>

<script>
import hljs from 'highlight.js'

export default {
  data  () {
    return {
      tableData: [],
      demoCodes: [
        `
        // 创建一个简单输入框渲染
        VXETable.renderer.add('MyInput', {
          // 可编辑激活模板
          renderEdit (h, renderOpts, { row, column }) {
            return [
              <input class="my-cell" text="text" v-model={ row[column.property] } />
            ]
          },
          // 可编辑显示模板
          renderCell (h, renderOpts, { row, column }) {
            return [
              <span>{ row[column.property] }</span>
            ]
          }
        })
        `,
        `
        <vxe-table
          border
          show-overflow
          :data="tableData"
          :edit-config="{trigger: 'click', mode: 'row'}">
          <vxe-table-column type="seq" width="60"></vxe-table-column>
          <vxe-table-column field="address2" title="简单输入框" :edit-render="{name: 'MyInput'}"></vxe-table-column>
          <vxe-table-column field="name" title="下拉表格" :edit-render="{name: 'EditDownTable', props: {checkField: 'name'}}"></vxe-table-column>
          <vxe-table-column field="nickname" title="Nickname" :edit-render="{name: 'EditPopupModal'}"></vxe-table-column>
          <vxe-table-column field="address" title="文本域" :edit-render="{name: 'EditDownTextarea'}"></vxe-table-column>
          <vxe-table-column field="role" title="复杂渲染" :edit-render="{name: 'EditDownModal', props: {checkField: 'role'}}"></vxe-table-column>
        </vxe-table>
        `,
        `
        export default {
          data () {
            return {
              tableData: []
            }
          },
          created () {
            this.tableData = window.MOCK_DATA_LIST.slice(0, 6)
          }
        }
        `
      ]
    }
  },
  created () {
    this.tableData = window.MOCK_DATA_LIST.slice(0, 6)
  },
  mounted () {
    Array.from(this.$el.querySelectorAll('pre code')).forEach((block) => {
      hljs.highlightBlock(block)
    })
  }
}
</script>
