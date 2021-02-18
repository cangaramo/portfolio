<template>
    <div class="project-wrapper" v-view="viewHandler">
        <transition name="topLeft">
            <div v-if="show">
                <a
                    :href="project.url"
                    target="_blank"
                    rel="noopener noreferrer nofollow"
                >
                    <div :class="`row project ${direction}`">
                        <div class="col-md-6 info">
                            <div>
                                <div v-if="show" class="swing">
                                    <h2 :style="`color:${project.color}`">
                                        {{ project.title }}
                                    </h2>
                                </div>
                                <hr />
                                <p
                                    class="year"
                                    :style="
                                        `border-color:${project.color}; color:${project.color}`
                                    "
                                >
                                    {{ project.year }}
                                </p>
                                <p class="desc">{{ project.description }}</p>
                                <p class="tag">{{ project.tags }}</p>
                            </div>
                        </div>
                        <div class="col-md-6 mt-4 mt-md-0">
                            <img :src="path" />
                        </div>
                    </div>
                </a>
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
@import '@/sass/animation.scss';
.project-wrapper {
    align-items: center;
    padding-left: 1rem !important;
    padding-right: 1rem !important;
    min-height: 10px;
    min-width: 10px;
    a {
        text-decoration: none;
    }
    .project {
        background: #f3f3f3;
        transition: all 0.8s;
        transform: rotate(0deg);
        padding: 2rem 1rem;
        @media (min-width: 768px) {
            padding: 1.5rem;
            padding-right: 0;
            // Hover
            &.project-left {
                &:hover {
                    cursor: pointer;
                    transition: all 0.8s;
                    transform: perspective(900px) rotateZ(0deg) rotateX(-10deg)
                        rotateY(-15deg);
                }
            }
            &.project-right {
                &:hover {
                    cursor: pointer;
                    transition: all 0.8s;
                    transform: perspective(900px) rotateZ(0deg) rotateX(-10deg)
                        rotateY(15deg);
                }
            }
            h2,
            p {
                transition: all 0.5s;
            }
            &:hover {
                h2,
                p {
                    transition: all 0.5s;
                    color: #96989c !important;
                    border-color: #96989c !important;
                }
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
            color: #212121;
        }
        .year {
            font-weight: 600;
            border: 1px solid #3c5887;
            color: #3c5887;
            width: fit-content;
            padding: 2px 8px;
            font-size: 13.5px;
            border-radius: 5px;
        }
        .desc {
            font-style: italic;
            font-size: 14px;
            margin: 12px 0 10px 0;
        }

        .tag {
            font-family: monospace;
            font-size: 12px;
        }
        hr {
            width: 80px;
            margin: 15px 0 15px 0;
            border-top: 3px solid #dad8d8;
        }
    }
    img {
        width: 100%;
        @media (min-width: 768px) {
            position: relative;
            top: -70px;
            width: 115%;
        }
    }
}
</style>
