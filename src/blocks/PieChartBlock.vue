<template>
  <div style="height:300px;width: 300px; display: flex;flex-direction:column;">
    <vue3-chart-js
          :id="doughnutChart.id"
          :type="doughnutChart.type"
          :data="doughnutChart.data"
          @before-render="beforeRenderLogic"
      ></vue3-chart-js>
  </div>
</template>
<script setup lang="ts">
import { PropType } from 'vue'
import { types } from '@dashibase/lotion'
import Vue3ChartJs from '@j-t-mcc/vue3-chartjs'

const chartContainer = ref(null)
const doughnutChart = {
      id: 'doughnut',
      type: 'doughnut',
      data: {
        labels: ['VueJs', 'EmberJs', 'ReactJs', 'AngularJs'],
        datasets: [
          {
            backgroundColor: [
              '#41B883',
              '#E46651',
              '#00D8FF',
              '#DD1B16'
            ],
            data: [40, 20, 80, 10]
          }
        ]
      }
}
const props = defineProps({
  block: {
    type: Object as PropType<types.Block>,
    required: true,
  },
  readonly: {
    type: Boolean,
    default: false,
  },
  hello: {
    type: Object as Record<string, Item>,
    default: {},
  },
})
const beforeRenderLogic = (event) => {
      //...
      //if(a === b) {
      //  event.preventDefault()
      //}
    }
// This is triggered when a user converts any block into this block
// It is called before the blocktype is changed
function onSet () {
}
// This is triggered when a user converts this block into any other block
// It is called before the blocktype is changed
function onUnset () {
}
defineExpose({
  onSet,
  onUnset,
})
</script>


