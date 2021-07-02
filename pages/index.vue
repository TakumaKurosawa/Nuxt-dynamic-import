<template>
  <div>
    <button @click="clickA">A</button>
    <button @click="clickB">B</button>
    <button @click="clickC">C</button>
    <button @click="clickD">D</button>
    <button @click="clickE">E</button>
    <button @click="clickF">F</button>
    <button @click="clickG">G</button>
    <component :is="componentName"/>
  </div>
</template>

<script>
export default {
  // components: {
  //   A: () => import('@/components/A.vue'),
  //   B: () => import('@/components/B.vue'),
  //   C: () => import('@/components/C.vue'),
  //   D: () => import('@/components/D.vue'),
  //   E: () => import('@/components/E.vue'),
  //   F: () => import('@/components/F.vue'),
  //   G: () => import('@/components/G.vue'),
  // },
  data() {
    return {
      componentName: 'A'
    }
  },
  methods: {
    clickA() {
      this.componentName = 'A'
    },
    clickB() {
      this.componentName = 'B'
    },
    clickC() {
      this.componentName = 'C'
    },
    clickD() {
      this.componentName = 'D'
    },
    clickE() {
      this.componentName = 'E'
    },
    clickF() {
      this.componentName = 'F'
    },
    clickG() {
      this.componentName = 'G'
    },
  }
}
</script>
