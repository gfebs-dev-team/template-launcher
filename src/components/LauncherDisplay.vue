<script setup>

    import CourseButton from "./CourseButton.vue";
    import LauncherHeader from "./LauncherHeader.vue";

</script>

<template>
    <body id="launcher-body">
        <LauncherHeader/>

        <div id="launcher-names">
            <p id="school-name" class="text-margins"> Financial Management School </p>
            <p id="course-name" class="text-margins"> GFEBS L210E Financials Process Overview </p>
        </div>

        <img id="course-icon" src="./icons/Shield-01.png">

        <div id="launcher-notes">
            <p id="next-steps" class="text-margins"> After completing this course, review all the modules and
             test for the <br> GFEBS L210E Financials Process Overview Post Assessment. </p>
            <p id="note" class="text-margins"> Note: This will launch module content and take you to an external .Mil website. </p>
        </div>

        <div id="button-grid">
            <CourseButton/>
            <CourseButton/>
            <CourseButton/>
            <CourseButton/>
            <CourseButton/>
            <CourseButton/>
        </div>
    </body>
</template>

<style scoped>

#launcher-body {
    width: 70%;
    height: 95%;
    margin: auto;
    background: teal;
    justify-content: center;
}

#course-icon {
    display: block;
    margin: auto;
    width: 25%;
    height: 25%;
}

#button-grid {
    display: grid;
    grid-template-columns: 250px 250px;
    justify-content: center;
    align-items: center;
    text-align: center;
    align-content: center;
    padding: 30px 0px 30px 0px;
 }

#launcher-names {
    font-family: sans-serif;
    font-weight: bold;
    text-align: center;
}

.text-margins {
    margin: 5px auto 5px auto;
}

#school-name {
    font-size: 32px;
    color: white;
}

#course-name {
    font-size: 24px;
    color: gold;
}

#launcher-notes {
    font-family: sans-serif;
    text-align: center;
}

#next-steps {
    font-size: 16px;
    color: white;
}

#note {
    font-size: 12px;
    font-weight: bold;
    color:gold;
}

</style>
