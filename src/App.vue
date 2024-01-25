<template>
    <div class="main-color">
        <IntroPage></IntroPage>
    </div>
    
</template>

<script>
import IntroPage from './components/IntroPage.vue';

    export default {
        components: {
            IntroPage 
        },
        created() {
        },
        data() {
            return {
                
            }
        },
        methods: {
            async getPages() {
                let res = await fetch(`pages.json`);
                let data = await res.json();

                this.pages = data;
            }
        }
    }
</script>

<style scoped>

.main-color {
    background-color: #2db451;
    height: 100vh;
}
</style>