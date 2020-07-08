<template>
    <div class="home container pb-5 mb-5">
        <div id="section1" class="section">
            <div class="d-flex align-items-center h-100">
                <div>
                    <h1>
                        Hi, my name is
                        <br class="d-block d-md-none" />
                        <span style="font-weight: bold; color: #c3808c"
                            >Clarisa Angaramo</span
                        >
                    </h1>
                    <h1 class="my-4 my-md-4">
                        I'm a <br class="d-block d-md-none" /><span
                            class="mix"
                            >{{ role }}</span
                        >
                    </h1>
                    <h3>These are some of my projects.</h3>
                </div>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-md-6 left">
                <Project :project="projects[0]"></Project>
            </div>
            <div class="col-md-6 right">
                <Project :project="projects[1]"></Project>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-md-6 left">
                <Project :project="projects[2]"></Project>
            </div>
            <div class="col-md-6 right">
                <Project :project="projects[3]"></Project>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-md-6 left">
                <Project :project="projects[4]"></Project>
            </div>
            <div class="col-md-6 right">
                <Project :project="projects[5]"></Project>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-md-6 left">
                <Project :project="projects[6]"></Project>
            </div>
            <div class="col-md-6 right">
                <Project :project="projects[7]"></Project>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-md-6 left">
                <Project :project="projects[9]"></Project>
            </div>
            <div class="col-md-6 right">
                <Project :project="projects[8]"></Project>
            </div>
        </div>
    </div>
</template>

<script>
import Project from '@/components/Project'
import projects from '@/data/projects.json'

export default {
    name: 'Home',
    data() {
        return {
            role: '',
            projects: projects
        }
    },
    components: {
        Project
    },
    methods: {
        randomString(len, charSet) {
            charSet = charSet || 'fvltDrndFpErote '
            var randomString = ''
            for (var i = 0; i < len; i++) {
                var randomPoz = Math.floor(Math.random() * charSet.length)
                randomString += charSet.substring(randomPoz, randomPoz + 1)
            }
            return randomString
        }
    },
    mounted() {
        var interval = setInterval(() => {
            var randomValue1 = this.randomString(4)
            var randomValue2 = this.randomString(3)
            var randomValue3 = this.randomString(9)
            this.role = randomValue1 + ' ' + randomValue2 + ' ' + randomValue3
        }, 100)
        setTimeout(() => {
            clearTimeout(interval)
            this.role = 'Front End Developer'
        }, 1200)
    }
}
</script>

<style lang="scss">
.section {
    height: 100vh;
}

h1 {
    font-size: 2rem;
    @media (min-width: 576px) {
        font-size: 2.5rem;
    }
}
h2 {
    font-weight: 600;
}
h3 {
    font-size: 1.35rem;
    @media (min-width: 576px) {
        font-size: 1.75rem;
    }
}
.single-margin {
    @media (min-width: 768px) {
        margin-top: 160px;
    }
}
.left {
    margin-top: 40px;
    @media (min-width: 768px) {
        margin-top: 430px;
        padding-left: 0;
        padding-right: 1.5rem;
    }
}
.right {
    margin-top: 40px;
    @media (min-width: 768px) {
        margin-top: 0;
        padding-left: 1.5rem;
        padding-right: 0;
    }
}
</style>
