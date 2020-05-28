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
        <div class="row mt-5">
            <div class="col-6 pl-0 pr-4" style="margin-top: 350px">
                <div class="project-wrapper px-3">
                    <div
                        class="project left row py-4 pl-4"
                        v-view="viewHandler"
                        section="2"
                    >
                        <div class="col-6 info">
                            <h2 style="color:#519291">Belushop</h2>
                            <hr style="border-color:#519291" />
                            <p>2020</p>
                            <p class="desc my-1">Personal project</p>
                            <p class="tag">#vue #javascript #firebase #axios</p>
                        </div>
                        <div class="col-6">
                            <img src="@/assets/belushop2.png" />
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-6 pr-0 pl-4" style="">
                <div class="project-wrapper px-3">
                    <div class="project right row py-4 pl-4">
                        <div class="col-6 info">
                            <h2 style="color:#4c5388">
                                What can I <br />cook today?
                            </h2>
                            <hr style="border-color:#4c5388" />
                            <p>2020</p>
                            <p class="desc my-1">Personal project</p>
                            <p class="tag">#vue #javascript #firebase #axios</p>
                        </div>
                        <div class="col-6">
                            <img src="@/assets/whatcan2.png" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="row" style="margin-top: 80px">
            <div class="col-6 pl-0 pr-4" style="margin-top: 350px">
                <div class="project-wrapper px-3">
                    <div
                        class="project left row py-4 pl-4"
                        v-view="viewHandler"
                        section="2"
                    >
                        <div class="col-6 info">
                            <h2 style="color: #eab757">ScaleUp Institute</h2>
                            <hr style="border-color:#eab757" />
                            <p>2019</p>
                            <p class="dec my-1">Built at Bladonmore</p>
                            <p class="tag">#vue #javascript #firebase #axios</p>
                        </div>
                        <div class="col-6">
                            <img src="@/assets/project-scaleup.png" />
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-6 pr-0 pl-4" style="margin-top: 0">
                <div class="project-wrapper px-3">
                    <div class="project right row py-4 pl-4">
                        <div class="col-6 info">
                            <h2 style="color:#00806a">Flash Pack</h2>
                            <hr style="border-color:#00806a" />
                            <p>2019</p>
                            <p class="desc my-1">Built at Flash Pack</p>
                            <p class="tag">#php #wordpress #vue</p>
                        </div>
                        <div class="col-6">
                            <img src="@/assets/flashpack.png" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
        <div class="row" style="margin-top: 80px">
            <div class="col-6 pl-0 pr-4" style="margin-top: 350px">
                <div class="project-wrapper px-3">
                    <div
                        class="project left row py-4 pl-4"
                        v-view="viewHandler"
                        section="2"
                    >
                        <div class="col-6 info">
                            <h2 style="color: #608bbf">Baring Vostok</h2>
                            <hr style="border-color:#608bbf" />
                            <p>2019</p>
                            <p class="desc my-1">Built at Bladonmore</p>
                            <p class="tag">#php #wordpress</p>
                        </div>
                        <div class="col-6">
                            <img src="@/assets/baring.png" />
                        </div>
                    </div>
                </div>
            </div>
            <div class="col-6 pr-0 pl-4" style="margin-top: 0">
                <div class="project-wrapper px-3">
                    <div class="project right row py-4 pl-4">
                        <div class="col-6 info">
                            <h2 style="color:#3b5988">
                                Caledonia Private Capital
                            </h2>
                            <hr style="border-color:#3b5988" />
                            <p>2019</p>
                            <p class="desc my-1">Built at Bladonmore</p>
                            <p class="tag">#php #wordpress</p>
                        </div>
                        <div class="col-6">
                            <img src="@/assets/project-caledonia.png" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Home',
    data() {
        return {
            role: ''
        }
    },
    methods: {
        viewHandler(e) {
            console.log(e)
            // if (e.type == 'enter' || e.type == 'progress') {
            //     var elem = e.target.element
            //     var x = elem.getAttribute('section')
            //     console.log(x)
            //     this.min_offset = (x - 1) * 100
            //     this.max_offset = -((5 - x) * 100)
            //     console.log(this.min_offset)
            //     console.log(this.max_offset)
            // }
        },
        randomString(len, charSet) {
            charSet = charSet || 'fvltrndpErote '
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
.project-wrapper {
    align-items: center;
    .project {
        background: #f3f3f3;
        transition: transform 0.8s;
        transform: rotate(0deg);

        &.left {
            &:hover {
                cursor: pointer;
                transition: transform 0.8s;
                transform: perspective(900px) rotateZ(0deg) rotateX(-10deg)
                    rotateY(-15deg);
            }
        }

        &.right {
            &:hover {
                cursor: pointer;
                transition: transform 0.8s;
                transform: perspective(900px) rotateZ(0deg) rotateX(-10deg)
                    rotateY(15deg);
            }
        }
    }
    .info {
        width: 280px;
        padding-right: 20px;
        h2 {
            line-height: 33px;
            font-weight: bold;
        }
        p {
            margin-bottom: 0;
        }
        hr {
            width: 150px;
            margin: 8px 0 20px 0;
            border-top: 2px solid #2c3e50;
        }
    }

    img {
        position: relative;
        top: -70px;
        width: 115%;
    }

    .desc {
        font-style: italic;
    }

    .tag {
        font-family: monospace;
    }
}
</style>
