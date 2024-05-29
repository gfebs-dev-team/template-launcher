<script setup>

defineProps({
    courseName: String,
    activeName: String
  })

function openWindow () {
    const windowFeatures ="resizable=0, width=1024, height=800";
    window.open("", "_blank", windowFeatures);
}

</script>

    <template>
  <button @click="openWindow" :class="{active: courseName == activeName }">{{ courseName }} </button>
</template>

<style scoped lang="scss">

button {
    background: var(--color-background);
    font-weight: bold;
    border: none;
    border-radius: 10px;
    padding: .7rem 2rem;
    margin: .25rem;
    color: var(--color-accent);
    line-height: 1.5;
    min-height: 4rem;
    
        @media only screen and (max-width: 1024px) {
            font-size: $m-2;
            width: 20rem;
  }
}
.top-button {
    grid-column: 1 / span 2;
    justify-self: center;
    margin: 0 2rem .25rem;
    padding: 0 10rem;
        @media only screen and (max-width: 1024px) {
            padding: .7rem 2rem;
            margin: .5rem;
        } 
        @media only screen and (max-width: 550px) {
            margin-bottom: .25em;
        }
}

</style>