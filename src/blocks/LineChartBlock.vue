<template>
  <div style="height:auto ;width: auto; display: flex;flex-direction:column;">
    <vue3-chart-js
        :id="chartConfigs.id"
        :type="chartConfigs.type"
        :data="chartConfigs.data"
        @before-render="beforeRenderLogic"
    ></vue3-chart-js>
  </div>
</template>

<script setup lang="ts">
import Vue3ChartJs from '@j-t-mcc/vue3-chartjs'
import { PropType } from 'vue'
import { types } from '@dashibase/lotion'
const labels = [
    'January',
    'February',
    'March',
    'April',
    'May',
    'June',
  ];

const data = {
  labels: labels,
  datasets: [{
    label: 'My First dataset',
    backgroundColor: 'rgb(255, 99, 132)',
    borderColor: 'rgb(255, 99, 132)',
    data: [0, 10, 5, 2, 20, 30, 45],
  }]
};

const chartConfigs = {
  id: 'line',
  type: 'line',
  data: data,
  options: {}
};

const beforeRenderLogic = (event) => {
  //...
  //if(a === b) {
  //  event.preventDefault()
  //}
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
})
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

