<template>
  <div>
    <el-button size="small" style="float:right;margin-top:6px;margin-right:6px;" @click="()=>{this.$refs['wfd'].saveToConsole()}">输出到控制台</el-button>
    <!--    <el-button size="small" style="float:right;margin-top:6px;margin-right:6px;" @click="()=>{this.$refs['wfd'].graph.saveXML()}">导出XML</el-button>-->
    <el-button size="small" style="float:right;margin-top:6px;margin-right:6px;" @click="()=>{this.modalVisible=true}">查看流程图</el-button>
    <graph-editor ref="wfd" :data="demoData" :height="600" :users="candidateUsers" :groups="candidateGroups" :lang="lang" />
    <el-dialog title="查看流程图" :visible.sync="modalVisible" width="60%">
      <graph-editor ref="wfd" :data="demoData1" :height="300" is-view />
    </el-dialog>
  </div>
</template>

<script>
// import G6 from '@antv/g6'
import GraphEditor from './GraphEditor'
export default {
  components: { GraphEditor },
  data() {
    return {
      modalVisible: false,
      lang: 'zh',
      demoData: {
        nodes: [
          { id: 'startNode1', x: 50, y: 200, label: '', clazz: 'start' },
          { id: 'startNode2', x: 50, y: 320, label: '', clazz: 'timerStart' },
          { id: 'taskNode1', x: 200, y: 200, label: '主任审批', clazz: 'userTask' },
          { id: 'taskNode2', x: 400, y: 200, label: '经理审批', clazz: 'scriptTask' },
          { id: 'gatewayNode', x: 400, y: 320, label: '金额大于1000', clazz: 'inclusiveGateway' },
          { id: 'taskNode3', x: 400, y: 450, label: '董事长审批', clazz: 'receiveTask' },
          { id: 'catchNode1', x: 600, y: 200, label: '等待结束', clazz: 'signalCatch' },
          { id: 'endNode', x: 600, y: 320, label: '', clazz: 'end' }
        ],
        edges: [
          { source: 'startNode1', target: 'taskNode1', sourceAnchor: 1, targetAnchor: 3, clazz: 'flow' },
          { source: 'startNode2', target: 'gatewayNode', sourceAnchor: 1, targetAnchor: 3, clazz: 'flow' },
          { source: 'taskNode1', target: 'catchNode1', sourceAnchor: 0, targetAnchor: 0, clazz: 'flow' },
          { source: 'taskNode1', target: 'taskNode2', sourceAnchor: 1, targetAnchor: 3, clazz: 'flow' },
          { source: 'taskNode2', target: 'gatewayNode', sourceAnchor: 1, targetAnchor: 0, clazz: 'flow' },
          { source: 'taskNode2', target: 'taskNode1', sourceAnchor: 2, targetAnchor: 2, clazz: 'flow' },
          { source: 'gatewayNode', target: 'taskNode3', sourceAnchor: 2, targetAnchor: 0, clazz: 'flow' },
          { source: 'gatewayNode', target: 'endNode', sourceAnchor: 1, targetAnchor: 2, clazz: 'flow' },
          { source: 'taskNode3', target: 'endNode', sourceAnchor: 1, targetAnchor: 1, clazz: 'flow' },
          { source: 'catchNode1', target: 'endNode', sourceAnchor: 1, targetAnchor: 0, clazz: 'flow' }
        ]
      },
      demoData1: {
        nodes: [
          { id: 'startNode1', x: 50, y: 200, label: '', clazz: 'start' },
          { id: 'startNode2', x: 50, y: 320, label: '', clazz: 'timerStart' },
          { id: 'taskNode1', x: 200, y: 200, label: '主任审批', clazz: 'userTask' },
          { id: 'taskNode2', x: 400, y: 200, label: '经理审批', clazz: 'scriptTask', active: true },
          { id: 'gatewayNode', x: 400, y: 320, label: '金额大于1000', clazz: 'gateway' },
          { id: 'taskNode3', x: 400, y: 450, label: '董事长审批', clazz: 'receiveTask' },
          { id: 'catchNode1', x: 600, y: 200, label: '等待结束', clazz: 'signalCatch' },
          { id: 'endNode', x: 600, y: 320, label: '', clazz: 'end' }
        ],
        edges: [
          { source: 'startNode1', target: 'taskNode1', sourceAnchor: 1, targetAnchor: 3, clazz: 'flow' },
          { source: 'startNode2', target: 'gatewayNode', sourceAnchor: 1, targetAnchor: 3, clazz: 'flow' },
          { source: 'taskNode1', target: 'catchNode1', sourceAnchor: 0, targetAnchor: 0, clazz: 'flow' },
          { source: 'taskNode1', target: 'taskNode2', sourceAnchor: 1, targetAnchor: 3, clazz: 'flow' },
          { source: 'taskNode2', target: 'gatewayNode', sourceAnchor: 1, targetAnchor: 0, clazz: 'flow' },
          { source: 'taskNode2', target: 'taskNode1', sourceAnchor: 2, targetAnchor: 2, clazz: 'flow' },
          { source: 'gatewayNode', target: 'taskNode3', sourceAnchor: 2, targetAnchor: 0, clazz: 'flow' },
          { source: 'gatewayNode', target: 'endNode', sourceAnchor: 1, targetAnchor: 2, clazz: 'flow' },
          { source: 'taskNode3', target: 'endNode', sourceAnchor: 1, targetAnchor: 1, clazz: 'flow' },
          { source: 'catchNode1', target: 'endNode', sourceAnchor: 1, targetAnchor: 0, clazz: 'flow' }
        ]
      },
      candidateUsers: [{ id: '1', name: 'Tom' }, { id: '2', name: 'Steven' }, { id: '3', name: 'Andy' }],
      candidateGroups: [{ id: '1', name: 'Manager' }, { id: '2', name: 'Security' }, { id: '3', name: 'OA' }]
    }
  },
  mounted() {
  }
}
</script>

<style scoped>

</style>
