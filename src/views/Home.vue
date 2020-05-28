<template>
    <div class="home container">
        <div id="section1" class="section">
            <div class="d-flex align-items-center h-100">
                <div>
                    <h1>
                        Hi, my name is
                        <span style="font-weight: bold; color: #c3808c"
                            >Clarisa Angaramo</span
                        >
                    </h1>
                    <h1>
                        I am a <span class="mix">{{ role }}</span>
                    </h1>
                    <h3>These are some of my projects.</h3>
                </div>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-6 left">
                <Project :project="projects[0]"></Project>
            </div>
            <div class="col-6 right">
                <Project :project="projects[1]"></Project>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-6 left">
                <Project :project="projects[2]"></Project>
            </div>
            <div class="col-6 right">
                <Project :project="projects[3]"></Project>
            </div>
        </div>
        <div class="row single-margin">
            <div class="col-6 left">
                <Project :project="projects[4]"></Project>
            </div>
            <div class="col-6 right">
                <Project :project="projects[5]"></Project>
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
        viewHandler(e) {
            console.log(e)
        },
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

h2 {
    font-weight: 600;
}

.single-margin {
    margin-top: 80px;
}

.left {
    margin-top: 350px;
    padding-left: 0;
    padding-right: 1.5rem !important;
}

.right {
    padding-left: 1.5rem !important;
    padding-right: 0 !important;
    margin-top: 0;
}
</style>
