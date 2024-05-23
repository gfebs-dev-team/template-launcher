<script setup>

    import CourseButton from "./CourseButton.vue";
    import LauncherHeader from "./LauncherHeader.vue";

</script>

<template>

        
        <div class="container">
            <LauncherHeader />     
            <div class="content">      
                <img src="../assets/icons/crest.svg">
                <div> 
                    <p class="school text-margins"> FINANCIAL MANAGEMENT SCHOOL </p>
                    <p class="course text-margins"> GFEBS L210E Financials Process Overview </p>
                    <p class="next-steps text-margins"> After completing this course, review all the modules and
                        test for the GFEBS L210E Financials Process Overview Post Assessment. </p>
                    <p id="note" class="text-margins"> Note: This will launch module content and take you to an external .Mil website. </p>
                </div></div>
                    
                <div class="button-container">
                    <div class="button-grid">

                    <CourseButton class="large-button"/>
                    <div class="smaller-buttons"><CourseButton/>
                    <CourseButton/>
                    <CourseButton/>
                    <CourseButton/>
                </div>  
                </div>
            </div>
            </div>

              

</template>

<style scoped lang="scss">


.container{
   
    
    //display: flex;
   // justify-content: center;
    width: 100vw;
    height: auto;
  
 
}

.content {

    display: flex;
    justify-content: center;
    align-items: center;
    text-align: center;  
    //flex-wrap: wrap;
padding:0 2rem;
  //  margin: 3rem;
}
.content img  {

 height: 250px;
 margin: 2rem;
}



.button-container {
   height: 100%;
    width: 100%;
    display: flex;

    //align-items: center;
    justify-content: center;
   // flex-wrap: wrap;
}

.button-grid {
   display: grid;
    grid-template-columns: 1fr;
    gap: 1rem;
 }

 .large-button{

 }

.smaller-buttons {

}

.text-margins {
    margin: 5px auto 5px auto;
}

.school {
    font-size: 32px;
    color: white;
}

.course {
    font-weight: bold;
    font-size: 24px;
    color: var(--color-accent);
    line-height: 120%;
}

.next-steps {
    font-size: 16px;
    color: white;
}

#note {
    font-size: 12px;
    font-weight:100;
    color: --color-accent;
    line-height: 250%;
}

</style>
//git orgin merge