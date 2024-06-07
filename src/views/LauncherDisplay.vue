<script setup>
import CourseButton from '/src/components/CourseButton.vue'
import LauncherHeader from '/src/components/LauncherHeader.vue'

defineEmits(['exit', 'openWindow'])

// COURSE NAME AND LAUNCHERS ADDED BELOW
const buttons = [
  { id: 1, courseName: '1. INTRODUCTION', link: '' },
  { id: 2, courseName: '2. COURSE NAME', link: '' },
  { id: 3, courseName: '3. COURSE NAME', link: '' },
  { id: 4, courseName: '4. COURSE NAME', link: '' },
  { id: 5, courseName: '5. COURSE NAME', link: '' },
  { id: 6, courseName: '6. COURSE NAME', link: '' }
]
</script>

<template>
  <div class="container">
    <LauncherHeader isexit="true" @exit="$emit('exit')" />

    <div class="content">
      <img src="../assets/icons/crest.svg" />
      <div class="text-container">
        <p class="school">FINANCE AND COMPTROLLER SCHOOL</p>
        <!-- CHANGE COURSE NAME/CODE BELOW -->
        <p class="course">GFEBS TEMPLATE LAUNCHER</p>
        <p class="next-steps">
          After completing this course, review all the modules and test for the GFEBS L210E
          Financials Process Overview Post Assessment.
        </p>
        <p class="note">
          Note: This will launch module content and take you to an external .Mil website.
        </p>
      </div>
    </div>

    <div class="button-container">
      <CourseButton
        v-for="button in buttons"
        :key="button.id"
        v-bind="button"
        @openWindow="$emit('openWindow', button.id, button.link)"
      ></CourseButton>
    </div>
  </div>
</template>

<style scoped lang="scss">
.container {
  width: 100vw;
  height: 100vh;
  overflow-x: hidden;
  overflow-y: auto;
}
.content {
  display: flex;
  justify-content: center;
  margin: 5rem 5rem 0 5rem;
  @media only screen and (max-width: 550px) {
    flex-direction: column;
    margin: 3rem 5rem 0 5rem;
  }
}
.content img {
  height: 250px;
  margin-top: 2rem;
  margin-bottom: 1rem;
  @media only screen and (max-width: 550px) {
    margin: 0 0 1em 0;
  }
}
.text-container {
  text-align: center;
  margin: 2rem 0 2rem 1rem;
  max-width: 100%;
  @media only screen and (max-width: 550px) {
    margin: 0 0 1rem 0;
    width: 100vw;
  }
}

.button-container {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  grid-gap: 10px;
  align-items: center;
  margin: 0 auto;
  max-width: 900px;

  @media only screen and (max-width: 1024px) {
    display: flex;
    flex-wrap: wrap;
    justify-content: center;
    width: 100vw;
    margin-bottom: 2rem;
  }
  @media only screen and (max-width: 550px) {
    margin-bottom: 2rem;
  }
}

.school {
  font-size: $m4;
  color: white;
  line-height: 1.2;
  margin-bottom: 1rem;
  font-weight: 700;
  @media only screen and (max-width: 1024px) {
    font-size: $m3;
  }
  @media only screen and (max-width: 550px) {
    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;
  }
}
.course {
  font-weight: bold;
  font-size: $m2;
  color: var(--color-accent);
  line-height: 1.2;
  margin-bottom: 1rem;
  @media only screen and (max-width: 1024px) {
    font-size: $m1;
  }
}
.next-steps {
  font-size: $m0;
  color: white;
  margin-bottom: 1rem;
  @media only screen and (max-width: 1024px) {
    font-size: $m-1;
  }
}
.note {
  font-size: $m-2;
  font-weight: 100;
  line-height: 1.5;
}
</style>
