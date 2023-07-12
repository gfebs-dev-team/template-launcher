<script setup>

function launchLesson () {

    const windowFeatures ="resizable=0, width=1024, height=800";

    window.open("", "_blank", windowFeatures);
}

</script>

<template>
    <button id="course-button" @click="launchLesson"> 
    Sample Course Name
    </button>
</template>

<style scoped>

#course-button {
    color:white;
    background: cadetblue;
    justify-self: center;
    text-align: center;
    font-family: sans-serif;
    font-size: 16px;
    font-weight: bold;
    height: 32px;
    width: 230px;
    border: none;
    border-radius: 10px;
    padding: 10px 0px 10px 0px;
    margin: 10px;
}

</style>