<script setup>

</script>

<template>
    <header>
        <button><div>X</div><div>EXIT</div></button>
    </header>
</template>

<style scoped lang="scss">

header {
    background: var(--color-background);
    width: 100%;
    //height: 7%;
    display: flex;
   // align-items: center;
    justify-content: end;
    //margin: auto;
    //text-align: right;
    //font-size: 2em;
    //font-weight: bold;
    //font-family: sans-serif;
}
header button {
    display: flex;
    text-wrap: wrap;
    gap: 10px;
    margin: 1rem 3rem;
    background-color: var(--color-background-dark);
    border-radius: 5px;
    border-style: none;
    color: white;
    padding: 7px 20px;
    

}

p {
    margin: 2% 5% 2% 0%;
    color: white;
}

</style>