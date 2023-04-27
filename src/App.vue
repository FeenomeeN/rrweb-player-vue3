<script setup lang="ts">
import { ref, onMounted, nextTick } from "vue";
import Player from "./../lib/components/Player.vue";
import events from "./../dev/data";

const _events = ref<any[]>(events);

onMounted(async () => {
  if (_events.value) {
    await nextTick()
    const _iframe = document.querySelector('iframe') as HTMLIFrameElement
    if (_iframe) {
      _iframe.setAttribute('allow', 'autoplay')
      _iframe.setAttribute('crossorigin', 'anonymous')
      _iframe.setAttribute('title', 'is-rrweb-player')
      
      console.log(': ', _iframe)
    }
  }
})
</script>

<template>
  <div>
    <!-- <Player :events="_events" :width="900" :height="350" :auto-play="true" /> <br /> -->
    <Player
      :events="_events"
      :width="800"
      :height="350"
      :go-to="15000"
      :auto-play="true"
    />
  </div>
</template>
