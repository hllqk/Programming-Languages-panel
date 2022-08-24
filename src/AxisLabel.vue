<script>
import { valueToPoint } from './util.js'

export default {
  props: {
    stat: Object,
    index: Number,
    total: Number
  },
  computed: {
    point: function () {
      return valueToPoint(+this.stat.value + 15, this.index, this.total)
    }
  }
}
</script>

<template>
  <text style='font-size: 10px;fill: #666;' :x="point.x-10" :y="point.y+5">{{stat.label}}</text>
	
</template>