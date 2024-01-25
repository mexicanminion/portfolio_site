<template>
    <div class="main-color">
        <div v-if="mainPage == 0">
            <IntroPage
            :page="mainPage"
            @change-page="mainPage = $event"
            />
        </div>
        <div v-if="mainPage == 1">
            <div class="container">
                <div class="row">
                    <div class="col">
                        <h1>projects Site</h1>
                    </div>
                </div>
            </div>
        </div>
        <div v-if="mainPage == 2">
            <div class="container">
                <div class="row">
                    <div class="col">
                        <h1>about Site</h1>
                    </div>
                </div>
            </div>
        </div>
        <div v-if="mainPage == 3">
            <div class="container">
                <div class="row">
                    <div class="col">
                        <h1>contact Site</h1>
                    </div>
                </div>
            </div>
        </div>
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
        props: [],
        data() {
            return {
                mainPage: 0,
                pages:[]
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