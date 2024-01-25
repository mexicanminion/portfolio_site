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
                    class="btn btn-outline-secondary btn-lg" 
                    @click.prevent="false"
                >Projects</button>
                <button
                    class="btn btn-outline-secondary btn-lg" 
                    @click.prevent="false"
                >About Me</button>
                <button
                    class="btn btn-outline-secondary btn-lg" 
                    @click.prevent="false"
                >Contact</button>
            </div>
        </div>
    </section>
    
</template>

<script>

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
}

</style>