<template>
    <div class="project-wrapper" v-view="viewHandler">
        <transition name="topLeft">
            <div v-if="show">
                <div :class="`row project ${direction}`">
                    <div class="col-6 info">
                        <div>
                            <div v-if="show" class="swing">
                                <h2 :style="`color:${project.color}`">
                                    {{ project.title }}
                                </h2>
                            </div>
                            <hr :style="`border-color: ${project.color}`" />
                            <p>{{ project.year }}</p>
                            <p class="desc my-1">{{ project.description }}</p>
                            <p class="tag">{{ project.tags }}</p>
                        </div>
                    </div>
                    <div class="col-6">
                        <img :src="path" />
                    </div>
                </div>
            </div>
        </transition>
    </div>
</template>

<script>
export default {
    props: {
        project: Object
    },
    data() {
        return {
            show: false
        }
    },
    methods: {
        viewHandler(e) {
            if (e.type == 'enter') {
                this.show = true
            }
        }
    },
    computed: {
        direction() {
            let direction
            if (this.project.id % 2 == 0) {
                direction = 'project-left'
            } else {
                direction = 'project-right'
            }
            return direction
        },
        path() {
            return require('../assets/' + this.project.image)
        }
    }
}
</script>

<style lang="scss">
.topLeft-enter-active,
.topLeft-leave-active {
    animation: fadeInTopLeft 1.5s forwards;
    -webkit-animation: fadeInTopLeft 1.5s forwards;
}

.topLeft-enter, .topLeft-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
}

.swing {
    -webkit-animation: swing-in-left-bck 2.5s
        cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
    animation: swing-in-left-bck 2.5s cubic-bezier(0.175, 0.885, 0.32, 1.275) forwards;
}

@-webkit-keyframes fadeInTopLeft {
    from {
        opacity: 0;
        -webkit-transform: translate3d(-100%, -100%, 0);
        transform: translate3d(-100%, -100%, 0);
    }
    to {
        opacity: 1;
        -webkit-transform: translate3d(0, 0, 0);
        transform: translate3d(0, 0, 0);
    }
}
@keyframes fadeInTopLeft {
    from {
        opacity: 0;
        -webkit-transform: translate3d(-100%, -100%, 0);
        transform: translate3d(-100%, -100%, 0);
    }
    to {
        opacity: 1;
        -webkit-transform: translate3d(0, 0, 0);
        transform: translate3d(0, 0, 0);
    }
}

@-webkit-keyframes swing-in-left-bck {
    0% {
        -webkit-transform: rotateY(-70deg);
        transform: rotateY(-70deg);
        -webkit-transform-origin: left;
        transform-origin: left;
        opacity: 0;
    }
    20% {
        -webkit-transform: rotateY(-70deg);
        transform: rotateY(-70deg);
        -webkit-transform-origin: left;
        transform-origin: left;
        opacity: 0;
    }
    100% {
        -webkit-transform: rotateY(0);
        transform: rotateY(0);
        -webkit-transform-origin: left;
        transform-origin: left;
        opacity: 1;
    }
}
@keyframes swing-in-left-bck {
    0% {
        -webkit-transform: rotateY(-70deg);
        transform: rotateY(-70deg);
        -webkit-transform-origin: left;
        transform-origin: left;
        opacity: 0;
    }
    20% {
        -webkit-transform: rotateY(-70deg);
        transform: rotateY(-70deg);
        -webkit-transform-origin: left;
        transform-origin: left;
        opacity: 0;
    }
    100% {
        -webkit-transform: rotateY(0);
        transform: rotateY(0);
        -webkit-transform-origin: left;
        transform-origin: left;
        opacity: 1;
    }
}

.project-wrapper {
    align-items: center;
    padding-left: 1rem !important;
    padding-right: 1rem !important;
    min-height: 10px;
    min-width: 10px;
    .project {
        background: #f3f3f3;
        transition: transform 0.8s;
        transform: rotate(0deg);
        padding-top: 1.5rem !important;
        padding-left: 1.5rem !important;
        padding-bottom: 1.5rem !important;
        &.project-left {
            &:hover {
                cursor: pointer;
                transition: transform 0.8s;
                transform: perspective(900px) rotateZ(0deg) rotateX(-10deg)
                    rotateY(-15deg);
            }
        }
        &.project-right {
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
            width: 80px;
            margin: 8px 0 20px 0;
            border-top: 3px solid #2c3e50;
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
