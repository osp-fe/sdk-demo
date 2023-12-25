

<template>
  <div id="test"></div>
</template>



<script setup>
import { onMounted, ref } from "vue";
import OSP from 'aai-osp-websdk'
onMounted(() => {
  const container = document.querySelector('#test')
  const osp = OSP.init(container, {
    token: 'bd8885ec-7e06-4a1c-bdcf-c810147765f1', // Obtain the token according to the integration doc
    environment: 'sandbox',
    language: 'en',
    onReady() {
      console.log('onReady')
      osp.open()
    },
    onLoad() {
      console.log('onload')
    },
    onError() {
      console.error('onerror')
    },
    onEvent(data) {
      console.log(`onEvent:${JSON.stringify(data)}`)
    },
    onComplete() {
      console.log('workflow complete!')
    }
  })
})

</script>


<style scoped>
#test {
  width: 100vw;
  height: 100vh;
}
</style>
