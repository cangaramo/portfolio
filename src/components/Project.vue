<template>
    <div class="project-wrapper">
        <div :class="`row project ${direction}`">
            <div class="col-6 info">
                <h2 :style="`color:${project.color}`">{{ project.title }}</h2>
                <hr :style="`border-color: ${project.color}`" />
                <p>{{ project.year }}</p>
                <p class="desc my-1">{{ project.description }}</p>
                <p class="tag">{{ project.tags }}</p>
            </div>
            <div class="col-6">
                <img :src="path" />
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        project: Object
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
.project-wrapper {
    align-items: center;
    padding-left: 1rem !important;
    padding-right: 1rem !important;
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
