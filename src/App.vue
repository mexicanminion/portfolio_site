<template>
    <div id="mainColor" class="main-color">
        <div v-if="mainPage == 0 && pages.length > 0">
            <IntroPage
            :page="pages"
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
            this.setPageTitle();
        },
        props: [],
        data() {
            return {
                mainPage: 0,
                pages:[{
                    pageTitle: `Home`,
                    number: 0
                },
                {
                    pageTitle: `Projects`,
                    number: 1
                },
                {
                    pageTitle: `About Me`,
                    number: 2
                },
                {
                    pageTitle: `Contact`,
                    number: 3
                }]
            }
        },
        methods: {
            async getPages() {
                let res = await fetch(`pages.json`);
                let data = await res.json();

                this.pages = data;
            },
            setPageTitle(){
                document.title = `Javier Moncada - ${this.pages[this.mainPage].pageTitle}`;
            },
            changeBgColor(){
                let defaultColor = "#2db451";
                let color = document.getElementById("mainColor").style.backgroundColor;
                console.log(defaultColor,color);
                if (color == '') {
                    document.getElementById("mainColor").style.backgroundColor = defaultColor;
                }
                else if (color == defaultColor) {
                    document.getElementById("mainColor").style.backgroundColor = "black";
                } else {
                    document.getElementById("mainColor").style.backgroundColor = "#2db451";
                }
            },
        },
        watch: {
            mainPage(oldPage) {
                if (this.mainPage == oldPage) {
                    this.setPageTitle(this.pages[0]);
                }
            },
        }
    }

    /*function changeBgColor() {
        let defaultColor = "#2db451";
        let color = document.getElementById("mainColor").style.backgroundColor;
        console.log(defaultColor,color);
        if (color == '') {
            document.getElementById("mainColor").style.backgroundColor = defaultColor;
        }
        else if (color == defaultColor) {
            document.getElementById("mainColor").style.backgroundColor = "black";
        } else {
            document.getElementById("mainColor").style.backgroundColor = "#2db451";
        }
    }

    setInterval(function() {
        changeBgColor();    
    }, 200)
    */
</script>

<style scoped>

.main-color {
    background-color: #2db451;
    height: 100vh;
}
</style>