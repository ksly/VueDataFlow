<template>
  <div :data-clazz="model.clazz">
    <div class="panelTitle">{{ i18n['naiveBayesModel'] }}</div>
    <div class="panelBody">
      <DefaultDetail :model="model" :on-change="onChange" :read-only="readOnly" />
      <div class="panelRow">
        <div>{{ i18n['naiveBayes.label'] }}：</div>
        <el-input
          style="width:90%; font-size:12px"
          :disabled="readOnly"
          :value="model.label"
          @input="(value) => {onChange('label', value)}"
        />
      </div>
      <div class="panelRow">
        <div>{{ i18n['naiveBayes.smoothing'] }}：</div>
        <el-input
          style="width:90%; font-size:12px"
          :disabled="readOnly"
          :value="model.smoothing"
          @input="(value) => {onChange('smoothing', value)}"
        />
      </div>
      <div class="panelRow">
        <div>{{ i18n['naiveBayes.type'] }}：</div>
        <el-input
          style="width:90%; font-size:12px"
          :disabled="readOnly"
          :value="model.type"
          @input="(value) => {onChange('type', value)}"
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
