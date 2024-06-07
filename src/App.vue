<script setup>
import LauncherDisplay from './views/LauncherDisplay.vue'
import { SCORM } from 'pipwerks-scorm-api-wrapper'
import { onMounted, reactive, ref, onBeforeUnmount } from 'vue'

const sessionTime = reactive({
  start: 0,
  end: 0
})

function setSession(time) {
  if (time == 'start') {
    sessionTime.start = new Date()
  } else if (time == 'end') {
    sessionTime.end = new Date()
  }
}

function getSession(time) {
  if (time == 'start') {
    return sessionTime.start
  } else if (time == 'end') {
    return sessionTime.end
  }
}

const terminationEvent = "onpagehide" in self ? "pagehide" : "unload";

onMounted(() => {
  SCORM.init()
  setSession('start')
  SCORM.set('cmi.success_status', 'passed')
  window.addEventListener(terminationEvent, quit);
})

const lastButtonClicked = ref(null)

function openWindow(id, link) {
  const windowFeatures = 'resizable=0, width=1024, height=800'
  window.open(link, '_blank', windowFeatures)
  lastButtonClicked.value = id
}

const quit = (complete) => {
  setSession('end')
  const totalSeconds = (Math.round((getSession('end') - getSession('start')) / 1000) * 100) / 100
  let seconds = totalSeconds % 60
  let totalMinutes = Math.round((totalSeconds - seconds) / 60)
  let minutes = totalMinutes % 60
  let totalHours = Math.round((totalMinutes - minutes) / 60)
  let session_time =
    'PT' +
    (totalHours > 0 ? totalHours + 'H' : '') +
    (minutes > 0 ? minutes + 'M' : '') +
    (seconds > 0 ? seconds + 'S' : '')
  console.log(session_time)
  SCORM.set('cmi.exit', 'normal')
  SCORM.set('cmi.session_time', session_time)

  SCORM.set('cmi.location', 0)
  
  if (SCORM.get('cmi.completion_status') == 'incomplete') {
    SCORM.set('adl.nav.request', 'suspendAll')
  }
  if(complete) {
    SCORM.set('cmi.completion_status', 'complete');
    SCORM.set('adl.nav.request','exit');
  }
  
SCORM.save()
  SCORM.quit()
}

onBeforeUnmount(() => {
  SCORM.set('cmi.completion_status', 'incomplete')
  SCORM.set('adl.nav.request', 'suspendAll')
  quit()
})
</script>

<template>
  <LauncherDisplay @exit="quit(true)" @openWindow="openWindow" />
</template>