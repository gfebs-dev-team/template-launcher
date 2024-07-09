<script setup>
import CourseButton from '/src/components/CourseButton.vue'
import AppHeader from '/src/components/AppHeader.vue'

defineEmits(['exit', 'openWindow'])

const buttons = [
  {
    id: 1,
    courseName: '1. INTRODUCTION',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/1IntroductionToFinancials/index.html'
  },
  {
    id: 2,
    courseName: '2. MANAGE GENERAL LEDGER ACCOUNTS',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/2ManageGeneralLedgerAccounts/index.html'
  },
  {
    id: 3,
    courseName: '3. PROCESSING JOURNAL VOUCHERS',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/3ProcessingJournalVouchers/index.html'
  },
  {
    id: 4,
    courseName: '4. PERFORM CASH BALANCING',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/4PerformCashBalancing/index.html'
  },
  {
    id: 5,
    courseName: '5. PERFORM PERIOD-END CLOSE',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/5PerformingPeriodEndClose/index.html'
  },
  {
    id: 6,
    courseName: '6. PERFORM YEAR-END CLOSE',
    link: 'https://ssilrc.army.mil/resources/FMS/GFEBS/2024/L210E/6PerformingYearEndClose/index.html'
  }
]
</script>

<template>
  <section class="flex h-full md:h-dvh flex-col bg-oxfordblue md:gap-0">
    <AppHeader :isexit="true" @exit="$emit('exit')"></AppHeader>
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
            GFEBS Essentials Course
          </h2>
          <p class="text-sm text-center text-aliceblue md:text-base">
            After completing this course, review all the modules and test for the GFEBS L210E
            Financials Process Overview Post Assessment.
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
          @openWindow="$emit('openWindow', button.id, button.link)"
        />

        <!-- <CourseButton v-for="button in buttons" :key="button.id" v-bind="button"></CourseButton> -->
      </div>
    </div>
  </section>
</template>
