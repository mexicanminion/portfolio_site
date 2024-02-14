<template>
    <section class="projectStyle">
        <button
            class="btn btn-outline-secondary btn-lg" 
            @click.prevent="this.$emit('change-page', 0)"
        >Home</button>
    </section>
</template>

<script>
export default {
        props: [''],
        data() {
            return {
            }
        },
        methods: {
            setPage(page){
                this.$emit('change-page', page)
            }
        }
    }
</script>

<style>
.projectStyle {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 96vh;
    width: 100%;
}

</style>