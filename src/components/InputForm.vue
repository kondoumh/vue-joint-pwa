<template>
  <div>
    <div>
      <input type="text" placeholder="new node name" v-model.trim="nodeName" @keyup.enter="add" />
      <input type="button" v-on:click="add" value="add node" />
      <input type="checkbox" id="checkLink" v-model="linkMode" v-on:change="check" />
      <label for="checkLink">link mode</label>
    </div>
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue'

export default defineComponent({
  name: 'InputForm',
  setup(props, {emit}) {
    const nodeName = ref('')
    const linkMode = ref(false)
    const add = () => {
      if (!nodeName.value) {
        return
      }
      emit('addNode', nodeName.value)
      nodeName.value = ''
    }
    const check = () => {
      emit('checkLink', linkMode.value)
    }
    return {
      nodeName,
      linkMode,
      add,
      check
    }
  }
})
</script>
