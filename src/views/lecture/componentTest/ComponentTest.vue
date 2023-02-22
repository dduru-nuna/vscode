<template>
  <v-container>
    <global-component :initial-test="counter" :increment-value="incValue1"/><br/>
    <global-component :initial-test="start" :increment-value="incValue2"/><br/>
    <!--global-component v-bind:initial-test="counter" :increment-value="incValue3"/><br/  v-bind가 생략되어있는것-->
    
    <local-component :initial-value="num"/><br/>
    <button @click="plus">클릭해봐!</button>
  </v-container>
</template>

<script>

import LocalComponent from '@/components/lecture/componentTest/LocalComponent.vue'

export default {
    name: "ComponentTest",
    components: {
      'local-component': LocalComponent
    },
    data () {
        return {
            counter: 0,
            start: 100,
            incValue1: 1,
            incValue2: 2,
            num: 33,
        }
    },
    methods: {
      plus () {
        this.num++
      }
    }
}
</script>

<style>

</style>