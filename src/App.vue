<script setup>
import CourseButton from './components/CourseButton.vue'
import AppHeader from './components/AppHeader.vue'
import { SCORM, debug } from 'pipwerks-scorm-api-wrapper'
import { onMounted, reactive, ref, onBeforeUnmount } from 'vue'
import config from '/gfebs.config.js'

const courseData = config.data.course
const sessionTime = reactive({
  start: 0,
  end: 0
})
const clicked = reactive({
  1: false,
  2: false,
  3: false,
  4: false,
  5: false,
  6: false
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

let url

const terminationEvent = 'onpagehide' in self ? 'pagehide' : 'unload'
onMounted(() => {
  debug.isActive = false
  url = window.location.href
  SCORM.init()
  setSession('start')
  SCORM.set('cmi.location', '0')
  /*console.log(SCORM.get('cmi.location'))
  if (SCORM.get('cmi.location')) {
    openWindow(SCORM.get('cmi.location'))
  }
  window.addEventListener(terminationEvent, quit)

  window.addEventListener('message', function (event) {
    console.log(event.data)
    let location = event.data.GFEBS_LOCATION
    SCORM.set('cmi.location', location)
  })*/
})

function openWindow(id, link) {
  clicked[id] = true
  const windowFeatures = 'resizable=0, width=1024, height=800'
  const popup = window.open(link, '_blank', windowFeatures)
  setTimeout(() => {
    popup.postMessage({ launcher: url }, link)
  }, 2000)
}

const quit = () => {
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
  SCORM.set('cmi.session_time', session_time)
  const completion = ref(true)
  for (let value in clicked) {
    if (clicked[value] == false) {
      completion.value = false
    }
  }

  if (!completion.value) {
    SCORM.set('cmi.completion_status', 'incomplete')
    SCORM.set('cmi.success_status', 'unknown')
    SCORM.set('cmi.exit', 'suspend')
    SCORM.set('adl.nav.request', 'suspendAll')
  } else {
    SCORM.set('cmi.completion_status', 'completed')
    SCORM.set('cmi.success_status', 'passed')
    SCORM.set('cmi.exit', 'normal')
    SCORM.set('adl.nav.request', 'exit')
  }

  SCORM.save()
  SCORM.quit()
}

onBeforeUnmount(() => {
  SCORM.set('cmi.completion_status', 'incomplete')
  SCORM.set('adl.nav.request', 'suspendAll')
  quit()
})

const buttons = [
  {
    id: 1,
    courseName: 'introduction',
    link: 'http://localhost:5174'
  },
  {
    id: 2,
    courseName: 'Lorem ipsum dolor',
    link: 'https://stackoverflow.com/questions/6264907/check-if-a-popup-window-is-closed'
  },
  {
    id: 3,
    courseName: 'consectetuer adipiscing elit',
    link: 'http://192.168.0.27:5173/'
  },
  {
    id: 4,
    courseName: ' Rutrum quam montes phasellus',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/4PerformCashBalancing/index.html'
  },
  {
    id: 5,
    courseName: 'consectetur euismod eu ullamcorper',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/5PerformingPeriodEndClose/index.html'
  },
  {
    id: 6,
    courseName: 'Congue donec primis penatibus',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/6PerformingYearEndClose/index.html'
  }
]
</script>

<template>
  <section class="flex h-full md:h-dvh flex-col bg-oxfordblue md:gap-0">
    <AppHeader :isexit="true" @exit="quit()" :courseData="courseData"></AppHeader>
    <!--PAGE CONTENT-->
    <div
      class="flex h-full flex-col justify-center gap-6 scroll-auto bg-oxfordblue p-2 md:w-screen md:items-center md:gap-8"
    >
      <div
        class="space-y-4 h-full gap-4 md:h-auto p-2 justify-center flex flex-col md:flex-row md:max-w-screen-lg items-center"
      >
        <img
          class="w-1/2 md:h-0 md:min-h-full md:block pt-4 md:p-0"
          src="/assets/crest.svg"
          alt="crest"
        />
        <div class="flex flex-col items-center justify-center gap-4 md:gap-2 p-4">
          <h1
            class="uppercase text-lg md:text-2xl font-bold text-aliceblue tracking-wider text-balance text-center"
          >
            Financial Management School
          </h1>
          <h2
            class="uppercase text-sm md:text-lg font-bold text-saffron tracking-wider text-balance text-center"
          >
            GFEBS {{ courseData.title }} Course
          </h2>
          <p class="text-sm text-center text-aliceblue md:text-base">
            After completing this course, review all the modules and test for the GFEBS{{
              courseData.code ? ` ${courseData.code}` : ''
            }}
            {{ courseData.title }} Post Assessment.
          </p>
          <p class="md:text-sm text-center text-xs font-bold text-coolgrey">
            NOTE: This will launch module content and take you to an external .Mil website.
          </p>
        </div>
      </div>
      <div class="grid md:grid-cols-2 h-full md:h-auto items-center flex-wrap gap-4">
        <CourseButton
          v-for="button in buttons"
          :className="
            button.id == 1 || (buttons.length % 2 == 0 && button.id == buttons.length)
              ? 'md:col-span-2 md:w-1/2 justify-self-center'
              : ''
          "
          :key="button.id"
          v-bind="button"
          @openWindow="openWindow(button.id, button.link)"
        />
      </div>
    </div>
  </section>
</template>
