<template class="flex">
    <section class="main-color">
        <section>
            <div>
                <div v-if="mainPage == 0">
                    <IntroPage
                    :page="pages"
                    @change-page="changePage($event), isNavBold($event)"
                    />
                </div>
                <div v-if="mainPage == 1">
                    <ProjectsPage
                    @change-page="changePage($event), isNavBold($event)"
                    />
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
        </section>

        <nav v-show="!initLoad" class="myTest">
            <a id="home" class="itemNav" @click="changePage(0), isNavBold(0)">Home</a>
            <a id="projects" class="itemNav" @click="changePage(1), isNavBold(1)">Projects</a>
            <a id="about me" class="itemNav" @click="changePage(2), isNavBold(2)">About Me</a>
            <a id="contact" class="itemNav" @click="changePage(3), isNavBold(3)">Contact</a>
        </nav>
    </section>
</template>

<script>
    import IntroPage from './components/IntroPage.vue';
    import ProjectsPage from './components/ProjectsPage.vue';
    export default {
        components: {
            IntroPage,
            ProjectsPage 
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
                }],
                initLoad: true
            }
        },
        methods: {
            async getPages() {
                let res = await fetch(`pages.json`);
                let data = await res.json();

                this.pages = data;
            },
            setPageTitle(){
                document.title = `Javier Moncada | ${this.pages[this.mainPage].pageTitle}`;
            },
            isNavBold(page){
                for (let i = 0; i < this.pages.length; i++) {
                    document.getElementById(this.pages[i].pageTitle.toLowerCase()).classList.remove("bold");
                }
                if (this.mainPage == page) {
                    document.getElementById(this.pages[page].pageTitle.toLowerCase()).classList.add("bold");
                }
            },
            changePage(page){
                this.initLoad = false;
                this.mainPage = page;
            }
        },
        watch: {
            mainPage(oldPage) {
                if (this.mainPage == oldPage) {
                    this.setPageTitle(this.pages[0]);
                }
            }
        }
    }
</script>

<style>

.itemNav {
    color: #FFFFFF;
    background: none;
    font-size: 1.5rem;
    display: inline-block;
    padding: 10px;
    transition-duration: .5s;
    text-decoration: none;
}

.item{
    color: #FFFFFF;
    background: none;
    font-size: 2rem;
    font-weight: bold;
    display: inline-block;
    padding: 15px;
    transition-duration: .5s;
    border: none ;
}

.bold {
    font-weight: bold;
}

.item:hover{
    color: black;
    cursor: pointer;
    background: #ffffff74;
    border-radius: 2rem;
}

.itemNav:hover{
    color: black;
    cursor: pointer;
}

.myTest{
    display: flex;
    flex-direction: column;
    position: absolute;
    top: 5px;
    left: 5px;
    width: 10vw;
    pointer-events: all;
}

.main-color {
    background-color: #2db451;
    height: 100vh;
    animation-name: colour-loop;
    animation-duration: 5s;
}

@keyframes colour-loop{
  0%{
    background-color: #269142;
  }
  25%{
    background-color: #3fc462;
  }
  75%{
    background-color: #3dad5b;
  }
  100%{
    background-color: #2db451;
   }
}
</style>