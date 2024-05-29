<script setup>
    import CourseButton from "./CourseButton.vue";
    import LauncherHeader from "./LauncherHeader.vue";
    import { ref } from "vue";

const buttons = ref([
    { id: 1, courseName: 'INTRODUCTION' },
    { id: 2, courseName: 'MANAGE GENERAL LEDGER ACCOUNTS' },
    { id: 3, courseName: 'PROCESSING JOURNAL VOUCHERS' },
    { id: 4, courseName: 'PERFORM CASH BALANCING' },
    { id: 5, courseName: 'PERFORM PERIOD-END CLOSE' },
    { id: 6, courseName: 'PERFORM YEAR-END CLOSE' },
])




</script>

<template>
        <div class="container">
            <LauncherHeader />     
            <div class="content">      
                <img src="../assets/icons/crest.svg">
                <div class="text-container"> 
                    <p class="school text-margins"> FINANCIAL MANAGEMENT SCHOOL </p>
                    <p class="course text-margins"> GFEBS L210E Financials Process Overview </p>
                    <p class="next-steps text-margins"> After completing this course, review all the modules and
                        test for the GFEBS L210E Financials Process Overview Post Assessment. </p>
                    <p class="note text-margins"> Note: This will launch module content and take you to an external .Mil website. </p>
                </div>
            </div>
           
            <div class="button-container"> 
            <CourseButton v-for="button in buttons"
                :key="button.id"
                :courseName="button.courseName"
                :class="{ 'top-button': button.id === 1 }"
            ></CourseButton>     
            </div>
         </div> 
</template>

<style scoped lang="scss">

.container{
    width: 100vw;
    height: 100vh;
    overflow: auto;
}
.content {
    display: flex;
    justify-content: center;    
    margin: 5rem 5rem 0 5rem;
}
.content img  {
    height: 250px;
    margin-top: 2rem;
    margin-bottom: 1rem;

  
}
.text-container{
    text-align: center;
    margin: 2rem 0 2rem 1rem;
    max-width: 50%;
}
.top-button {
    grid-column: 1 / span 2;
    justify-self: center;
    margin: 0 2rem 1rem;
    padding: 0 10rem;
        @media only screen and (max-width: 1024px) {
            display: flex;
            align-items: center;
            justify-content: center;
            padding: .7rem 2rem;
            margin: 0;
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
display:flex;
flex-wrap: wrap;
justify-content: center;
width: 100vw;

    }
  
}
.button-group {  
    grid-column: 1; 
    grid-row: 2;   


}
.text-margins {
    margin: 5px auto 5px auto;
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
}
.course {
    font-weight: bold;
    font-size: $m1;
    color: var(--color-accent);
    line-height: 1.2;
    margin-bottom: 1rem;
    @media only screen and (max-width: 1024px) {
    font-size: $m0;
  }
}
.next-steps {
    font-size: $m-1;
    color: white;
    margin-bottom: 1rem;
    @media only screen and (max-width: 1024px) {
    font-size: $m-2;
  }
}
.note {
    font-size: $m-3;
    font-weight: 100;
    line-height: 1.5;


}
</style>
