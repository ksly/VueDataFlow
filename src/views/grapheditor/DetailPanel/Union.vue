<template>
  <div :data-clazz="model.clazz">
    <div class="panelTitle">{{ i18n['union'] }}</div>
    <div class="panelBody">
      <DefaultDetail :model="model" :on-change="onChange" :read-only="readOnly" />
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
