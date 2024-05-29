<script setup>
function closeWindow(){
    window.close();
}

</script>

<template>
    <header>
        <button @click="closeWindow" class="exit"><div>X</div><div>EXIT</div></button>
    </header>
</template>

<style scoped lang="scss">

header {
    background: var(--color-background);
    display: flex;
    justify-content: end;
}
.exit {
    display: flex;
    gap: .6rem;
    margin: .8rem 3rem;
    background-color: var(--color-background-dark);
    border-radius: 5px;
    border-style: none;
    color: white;
    padding: 7px 20px;
}
.exit div {
    font-size: .8rem;
}
</style>

