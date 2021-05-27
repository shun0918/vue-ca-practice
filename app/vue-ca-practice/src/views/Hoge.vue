<template>
  <div>
    <h1>hogehoge</h1>
    <button @click="increment()">+1</button>
    <p>state.count: {{state.count}}</p>
    <p>refCount: {{refCount}}</p>
    <p>{{ isOdd ? '奇数' : '偶数'}}</p>
    <p>watchCountTwice: {{ watchCountTwice }}</p>
  </div>
</template>
import { defineComponent } from 'vue'
import HelloWorld from '@/components/HelloWorld.vue'-

<script lang="ts">
import { computed, defineComponent, reactive, ref, watch } from 'vue'

interface State {
  count: number;
}

export default defineComponent({
  name: 'Hoge',
  setup () {
    const state = reactive<State>({
      count: 0
    })
    const refCount = ref(0)
    const increment = () => {
      state.count++
      refCount.value++
    }
    const isOdd = computed(() => state.count % 2 === 1)
    let watchCountTwice = 0

    watch(refCount, () => {
      console.log(state)
      watchCountTwice = state.count * 2
    })

    // ここでリターンしたやつだけ使える
    return {
      state,
      refCount,
      increment,
      isOdd,
      watchCountTwice
    }
  }
})
</script>
