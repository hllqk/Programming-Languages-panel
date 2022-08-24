<!--
跟 Vue 说 Hello World！
-->
<script>
import PolyGraph from './PolyGraph.vue'
export default {
  components: {
    PolyGraph
  },
  data: () => ({
    newLabel: '',
    stats: [
      { label: 'Python', value: 100 },
      { label: 'Java', value: 100 },
      { label: 'HTML', value: 100 },
      { label: 'PHP', value: 100 },
      { label: 'CSS', value: 100 },
      { label: 'C++', value: 100 }
    ]
  }),
  methods: {
    add(e) {
      e.preventDefault()
      if (!this.newLabel) return
      this.stats.push({
        label: this.newLabel,
        value: 100
      })
      this.newLabel = ''
    },
    remove(stat) {
      if (this.stats.length > 3) {
        this.stats.splice(this.stats.indexOf(stat), 1)
      } else {
        alert("Can't delete more!")
      }
    }
  }
}
</script>

<template>
	<center>
			<div id="colorPicker">
  </div>
  <svg width="200" height="200">
    <PolyGraph style='fill:#42b983;opacity:0.75' :stats="stats"></PolyGraph>
  </svg>

  <!-- 控件 -->
  <div v-for="stat in stats">
    <label style='padding-bottom:2px;margin-right:15px'>{{stat.label}}</label>
    <input type="range" v-model="stat.value" min="0" max="100">
    <span>{{stat.value}}</span>
    <button @click="remove(stat)" class="remove">X</button>
  </div>
	<br>
  <form id="add">
    <input name="newlabel" v-model="newLabel">
    <button @click="add">Add a Language</button>
  </form>
  </center>
</template>
<style>

label {
  display: inline-block;
  margin-left: 10px;
  width: 20px;
}

#raw {
  position: absolute;
  top: 0;
  left: 300px;
}
</style>