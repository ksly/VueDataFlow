<template>
  <div :data-clazz="model.clazz">
    <div class="panelTitle">{{ i18n['decisionTreeModel'] }}</div>
    <div class="panelBody">
      <DefaultDetail :model="model" :on-change="onChange" :read-only="readOnly" />
      <div class="panelRow">
        <div>{{ 'LabelColumn' }}：</div>
        <el-input
          style="width:90%; font-size:12px"
          :disabled="readOnly"
          :value="model.labelColumn"
          @input="(value) => {onChange('labelColumn', value)}"
        />
      </div>
    </div>
  </div>
</template>
<script>
import DefaultDetail from './DefaultDetail'
export default {
  inject: ['i18n'],
  components: {
    DefaultDetail
  },
  props: {
    model: {
      type: Object,
      default: () => ({})
    },
    onChange: {
      type: Function,
      default: () => {}
    },
    readOnly: {
      type: Boolean,
      default: false
    }
  }
}
</script>
