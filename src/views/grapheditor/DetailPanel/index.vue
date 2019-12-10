<template>
  <div class="detailPanel" :style="{'height':height+'px'}">
    <UserTaskDetail v-if="model.clazz === 'userTask'" :model="model" :on-change="onChange" :read-only="readOnly" :users="users" :groups="groups" />
    <ScriptTaskDetail v-else-if="model.clazz === 'scriptTask'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <JavaTaskDetail v-else-if="model.clazz === 'javaTask'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <ReceiveTaskDetail v-else-if="model.clazz === 'receiveTask'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <MailTaskDetail v-else-if="model.clazz === 'mailTask'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <TimerEventDetail v-else-if="model.clazz === 'timerStart' || model.clazz === 'timerCatch'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <SignalEventDetail v-else-if="model.clazz === 'signalStart' || model.clazz === 'signalCatch'" :model="model" :on-change="onChange" :read-only="readOnly" :signal-defs="signalDefs" />
    <MessageEventDetail v-else-if="model.clazz === 'messageStart' || model.clazz === 'messageCatch'" :model="model" :on-change="onChange" :read-only="readOnly" :message-defs="messageDefs" />
    <GatewayDetail v-else-if="model.clazz === 'gateway' || model.clazz === 'exclusiveGateway' || model.clazz === 'parallelGateway' || model.clazz === 'inclusiveGateway'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <FlowDetail v-else-if="model.clazz === 'flow'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <StartEventDetail v-else-if="model.clazz === 'start'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <EndEventDetail v-else-if="model.clazz === 'end'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <ProcessDetail v-else-if="model.clazz === 'process'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <DecisionTreeModel v-else-if="model.clazz === 'decisionTreeModel'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <DecisionTreePredict v-else-if="model.clazz === 'decisionTreePredict'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <NaiveBayesModel v-else-if="model.clazz === 'naiveBayesModel'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <NaiveBayesPredict v-else-if="model.clazz === 'naiveBayesPredict'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <RandomForestModel v-else-if="model.clazz === 'randomForestModel'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <RandomForestPredict v-else-if="model.clazz === 'randomForestPredict'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <LinearRegressionModel v-else-if="model.clazz === 'linearRegressionModel'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <LinearRegressionPredict v-else-if="model.clazz === 'linearRegressionPredict'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <LogisticRegressionModel v-else-if="model.clazz === 'logisticRegressionModel'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <LogisticRegressionPredict v-else-if="model.clazz === 'logisticRegressionPredict'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <Count v-else-if="model.clazz === 'count'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <Sum v-else-if="model.clazz === 'sum'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <Max v-else-if="model.clazz === 'max'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <Min v-else-if="model.clazz === 'min'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <Avg v-else-if="model.clazz === 'avg'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <Union v-else-if="model.clazz === 'union'" :model="model" :on-change="onChange" :read-only="readOnly" />
    <CountDistinct v-else-if="model.clazz === 'countDistinct'" :model="model" :on-change="onChange" :read-only="readOnly" />
  </div>
</template>
<script>
import UserTaskDetail from './UserTaskDetail'
import JavaTaskDetail from './JavaTaskDetail'
import ScriptTaskDetail from './ScriptTaskDetail'
import ReceiveTaskDetail from './ReceiveTaskDetail'
import MailTaskDetail from './MailTaskDetail'
import TimerEventDetail from './TimerEventDetail'
import SignalEventDetail from './SignalEventDetail'
import MessageEventDetail from './MessageEventDetail'
import GatewayDetail from './GatewayDetail'
import FlowDetail from './FlowDetail'
import StartEventDetail from './StartEventDetail'
import EndEventDetail from './EndEventDetail'
import ProcessDetail from './ProcessDetail'
import DecisionTreeModel from './DecisionTreeModel'
import DecisionTreePredict from './DecisionTreePredict'
import NaiveBayesModel from './NaiveBayesModel'
import NaiveBayesPredict from './NaiveBayesPredict'
import RandomForestModel from './RandomForestModel'
import RandomForestPredict from './RandomForestPredict'
import LinearRegressionModel from './LinearRegressionModel'
import LinearRegressionPredict from './LinearRegressionPredict'
import LogisticRegressionModel from './LogisticRegressionModel'
import LogisticRegressionPredict from './LogisticRegressionPredict'
import Count from './Count'
import Sum from './Sum'
import Max from './Max'
import Min from './Min'
import Avg from './Avg'
import Union from './Union'
import CountDistinct from './CountDistinct'
export default {
  inject: ['i18n'],
  components: {
    CountDistinct,
    Avg,
    Union,
    Min,
    Max,
    Sum,
    Count,
    LogisticRegressionPredict,
    LogisticRegressionModel,
    LinearRegressionPredict,
    LinearRegressionModel,
    RandomForestPredict,
    RandomForestModel,
    NaiveBayesPredict,
    NaiveBayesModel,
    DecisionTreePredict,
    DecisionTreeModel,
    UserTaskDetail,
    ScriptTaskDetail,
    JavaTaskDetail,
    ReceiveTaskDetail,
    MailTaskDetail,
    TimerEventDetail,
    SignalEventDetail,
    MessageEventDetail,
    GatewayDetail,
    FlowDetail,
    StartEventDetail,
    EndEventDetail,
    ProcessDetail
  },
  props: {
    height: {
      type: Number,
      default: 800
    },
    model: {
      type: Object,
      default: () => ({})
    },
    users: {
      type: Array,
      default: () => ([])
    },
    groups: {
      type: Array,
      default: () => ([])
    },
    signalDefs: {
      type: Array,
      default: () => ([])
    },
    messageDefs: {
      type: Array,
      default: () => ([])
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
<style lang="scss">
    .detailPanel {
        height: 100%;
        background: #f0f2f5;
        flex: 0 0 auto;
        float: left;
        width: 20%;
        border-right: 1px solid #E9E9E9;
        border-bottom: 1px solid #E9E9E9;
        .panelTitle {
            text-align: left;
            height: 32px;
            padding-left: 12px;
            color: #000;
            line-height: 28px;
            background: #EBEEF2;
            border-bottom: 1px solid #DCE3E8;
        }

        .panelBody {
            .panelRow {
                text-align: left;
                display: inline-block;
                font-size: 12px;
                width: 100%;
                padding: 5px 12px;
            }
        }
    }
</style>
