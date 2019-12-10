<template>
  <div class="itemPanel" :style="{'height': height+'px'}">
    <el-collapse v-model="activeNames">
      <el-collapse-item :title="i18n['start']" name="1">
        <img
          data-item="{clazz:'start',size:'30*30',label:''}"
          :src="require('../../assets/flow/start.svg')"
          style="width:42px;height:42px"
        >
        <div>{{ i18n['startEvent'] }}</div>
        <img
          data-item="{clazz:'timerStart',size:'30*30',label:''}"
          :src="require('../../assets/flow/timer-start.svg')"
          style="width:42px;height:42px"
        >
        <div>{{ i18n['timerEvent'] }}</div>
        <img
          data-item="{clazz:'messageStart',size:'30*30',label:''}"
          :src="require('../../assets/flow/message-start.svg')"
          style="width:42px;height:42px"
        >
        <div>{{ i18n['messageEvent'] }}</div>
        <img
          data-item="{clazz:'signalStart',size:'30*30',label:''}"
          :src="require('../../assets/flow/signal-start.svg')"
          style="width:42px;height:42px"
        >
        <div>{{ i18n['signalEvent'] }}</div>
      </el-collapse-item>
      <el-collapse-item :title="i18n['classify']" name="2">
        <img
          :data-item="decisionTreeModel"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['decisionTreeModel'] }}</div>
        <img
          :data-item="decisionTreePredict"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['decisionTreePredict'] }}</div>
        <img
          :data-item="naiveBayesModel"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['naiveBayesModel'] }}</div>
        <img
          :data-item="naiveBayesPredict"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['naiveBayesPredict'] }}</div>
        <img
          :data-item="randomForestModel"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['randomForestModel'] }}</div>
        <img
          :data-item="randomForestPredict"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['randomForestPredict'] }}</div>
      </el-collapse-item>
      <el-collapse-item :title="i18n['regression']" name="3">
        <img
          :data-item="linearRegressionModel"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['linearRegressionModel'] }}</div>
        <img
          :data-item="linearRegressionPredict"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['linearRegressionPredict'] }}</div>
        <img
          :data-item="logisticRegressionModel"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['logisticRegressionModel'] }}</div>
        <img
          :data-item="logisticRegressionPredict"
          :src="require('../../assets/flow/script-task.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['logisticRegressionPredict'] }}</div>
      </el-collapse-item>
      <el-collapse-item :title="i18n['aggregation']" name="4">
        <img
          :data-item="count"
          :src="require('../../assets/flow/aggregation.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['count'] }}</div>
        <img
          :data-item="max"
          :src="require('../../assets/flow/aggregation.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['max'] }}</div>
        <img
          :data-item="min"
          :src="require('../../assets/flow/aggregation.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['min'] }}</div>
        <img
          :data-item="sum"
          :src="require('../../assets/flow/aggregation.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['sum'] }}</div>
        <img
          :data-item="union"
          :src="require('../../assets/flow/aggregation.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['union'] }}</div>
        <img
          :data-item="avg"
          :src="require('../../assets/flow/aggregation.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['avg'] }}</div>
        <img
          :data-item="countDistinct"
          :src="require('../../assets/flow/aggregation.svg')"
          style="width:80px;height:44px"
        >
        <div>{{ i18n['countDistinct'] }}</div>
      </el-collapse-item>
      <el-collapse-item :title="i18n['end']" name="5">
        <img
          data-item="{clazz:'end',size:'30*30',label:''}"
          :src="require('../../assets/flow/end.svg')"
          style="width:42px;height:42px"
        >
        <div>{{ i18n['endEvent'] }}</div>
      </el-collapse-item>
    </el-collapse>
  </div>
</template>
<script>
export default {
  inject: ['i18n'],
  props: {
    height: {
      type: Number,
      default: 800
    }
  },
  data() {
    return {
      activeNames: [],
      decisionTreeModel: "{clazz:'decisionTreeModel',size:'150*44',label:'decisionTreeModel'}",
      decisionTreePredict: "{clazz:'decisionTreePredict',size:'150*44',label:'decisionTreePredict'}",
      naiveBayesModel: "{clazz:'naiveBayesModel',size:'150*44',label:'naiveBayesModel'}",
      naiveBayesPredict: "{clazz:'naiveBayesPredict',size:'150*44',label:'naiveBayesPredict'}",
      randomForestModel: "{clazz:'randomForestModel',size:'150*44',label:'randomForestModel'}",
      randomForestPredict: "{clazz:'randomForestPredict',size:'150*44',label:'randomForestPredict'}",
      linearRegressionModel: "{clazz:'linearRegressionModel',size:'150*44',label:'linearRegressionModel'}",
      linearRegressionPredict: "{clazz:'linearRegressionPredict',size:'150*44',label:'linearRegressionPredict'}",
      logisticRegressionModel: "{clazz:'logisticRegressionModel',size:'150*44',label:'logisticRegressionModel'}",
      logisticRegressionPredict: "{clazz:'logisticRegressionPredict',size:'150*44',label:'logisticRegressionPredict'}",
      count: "{clazz:'count',size:'80*44',label:'count'}",
      max: "{clazz:'max',size:'80*44',label:'max'}",
      min: "{clazz:'min',size:'80*44',label:'min'}",
      sum: "{clazz:'sum',size:'80*44',label:'sum'}",
      union: "{clazz:'union',size:'80*44',label:'union'}",
      avg: "{clazz:'avg',size:'80*44',label:'avg'}",
      countDistinct: "{clazz:'countDistinct',size:'80*44',label:'countDistinct'}"
    }
  }
}
</script>

<style lang="scss" >
    .itemPanel {
        float: left;
        width: 10%;
        background: #f0f2f5;
        overflow-y: auto;
        border-left: 1px solid #E9E9E9;
        border-bottom: 1px solid #E9E9E9;
        img{
            width: 92px;
            height: 96px;
            padding: 4px;
            border: 1px solid rgba(0,0,0,0);
            border-radius: 2px;
            &:hover{
                border: 1px solid #ccc;
                cursor: move;
            }
        }
        .el-collapse {
            border: 0;
            .el-collapse-item {
                > div[role=tab] > div {
                    padding-left: 10px;
                    border: 1px solid #E9E9E9;
                    border-left:0;
                }
                &:first-child{
                    > div[role=tab] > div {
                        border-top: 0;
                    }
                }
                &:last-child{
                    > div[role=tab] > div {
                        border-bottom: 1px solid #E9E9E9;
                    }
                }
                .el-collapse-item__wrap{
                    border-top: 0;
                    background: #f0f2f5;
                    text-align: center;
                }
            }
        }

    }
</style>
