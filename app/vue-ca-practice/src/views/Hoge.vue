<template>
  <div>
    <h1>hogehoge</h1>
    <button @click="increment()">+1</button>
    <p>{{state.count}}</p>
  </div>
</template>
import { defineComponent } from 'vue'
import HelloWorld from '@/components/HelloWorld.vue'-

<script lang="ts">
import { defineComponent, reactive } from 'vue'

interface State {
  count: number;
}

export default defineComponent({
  name: 'Hoge',
  setup () {
    const state = reactive<State>({
      count: 0
    })
    const increment = () => {
      state.count++
      console.log(state)
    }

    return {
      state,
      increment
    }
  }
})
</script>
