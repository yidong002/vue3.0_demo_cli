<template>
  <div class="about">
    <h1>This is an about page</h1>
    <el-button type="primary" @click="btEvent">el-button</el-button>
    <el-timeline>
      <el-timeline-item
        v-for="item in timeLineData"
        :key="item.id"
        :timestamp="item.time"
      >
        {{ item.name }}
      </el-timeline-item>
    </el-timeline>
  </div>
</template>

<script>
import { reactive, ref } from '@vue/reactivity'
export default {
  name: 'About',
  setup() {
    let timeLineData = reactive([
      {
        id: 1,
        time: '2020-11-01',
        name: '评审开始',
      },
      {
        id: 1,
        time: '2020-11-02',
        name: '评审进行中',
      },
      {
        id: 1,
        time: '2020-11-03',
        name: '评审结束',
      },
    ])
    let { btEvent } = aboutEvent()
    return {
      btEvent,
      timeLineData,
    }
  },
}
function aboutEvent() {
  function btEvent() {
    alert('vue3.0,使用element-plus,成功')
  }
  return {
    btEvent,
  }
}
</script>
