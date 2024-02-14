<template>
    <section class="introStyle">
        <div class="container align-items-center justify-content-center myRowGap">
            <div class="flex">
                <h1 class="my-name">Javier Moncada</h1>
            </div>
            <div class="">
                <h3 class="my-title">Software Engineer</h3>
            </div>
            <div class="d-flex flex-row p-2 just justify-content-evenly align-items-center myColGap">
                <button
                    class="item" 
                    @click.prevent="setPage(1)"
                >Projects</button>
                <button
                    class="item" 
                    @click.prevent="setPage(2)"
                >About Me</button>
                <button
                    class="item" 
                    @click.prevent="setPage(3)"
                >Contact</button>
            </div>
        </div>
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
.introStyle {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 96vh;
    width: 100%;
}
.myRowGap{
    display: flex;
    flex-direction: column;
    row-gap: 1rem;
}
.myColGap {
    display: flex;
    flex-direction: row;
    column-gap: 0.5rem;
}

.my-title {
    display: flex;
    color: #FFFFFF;
    text-align: center;
    justify-content: center;
    align-items: center;
    border-radius: 15px;
    margin: 0%;
}

.my-name {
    display: flex;
    padding: 5rem;
    font-size: 5rem;
    color: #FFFFFF;
    text-align: center;
    justify-content: center;
    align-items: center;
    border: 8px solid #FFFFFF;
    border-radius: 15px;
    width: 800px;
    height: 300px;
    max-width: 800px;
    min-width: 300px;
    margin: 0%;
    width: inherit;
}

</style>