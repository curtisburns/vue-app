<template>
    <header>
        <div class="hero-container" ref="hero-container">
            <div class="hero-bg">
            </div>
            <div class="hero-fg">
            </div>
            <h1 class="letsTalk" :style="{transform: 'translateY(' + letsTalkYPos + 'px) translateX(-120%)'}"> Let's talk</h1>
            <h1 class="space" :style="{transform: 'translateY(' + spaceYPos + 'px) translateX(-50%)'}">Space</h1>
        </div>
    </header>
</template>

<script>

export default {
    name: 'Landing-Hero',
    data() {
        return {
            letsTalkYPos: 0,
            spaceYPos: 0
        }
    },
    methods: {
        parallaxTitles() {
        const top = this.$refs["hero-container"].getBoundingClientRect().top;
        this.letsTalkYPos = top/10;
        this.spaceYPos = -top/30;
        }

    },
    created() {
        window.addEventListener('scroll', this.parallaxTitles)
    },
    destroyed() {
        window.removeEventListener('scroll', this.parallaxTitles)
    }
}
</script>

<style>
    .hero-container {
        width: 100vw;
        height: 100vh;
        padding: 0;
        margin: 0;
    }

    .hero-bg {
        position: absolute;
        top: 0;
        left: 0;
        min-width: 100%;
        min-height: 100%;
        background: url(../assets/astronaut.jpg) right top/cover no-repeat;
        z-index: 0;
    }

    .hero-fg {
        position: absolute;
        top: 0;
        left: 0;
        min-width: 100%;
        min-height: 100%;
        background: url('../assets/astronaut copy.png') right top/cover no-repeat;
        z-index: 2;
    }

    h1.letsTalk, h1.space {
        font-family: 'Roboto Condensed', sans-serif;
        position: absolute;
        text-transform: uppercase;
        color: #FFF;
        -webkit-backface-visibility: hidden;
    }

    h1.letsTalk {
        right: 0;
        z-index: 3;
        top: 28vh;
        font-size: 9vw;
    }

     h1.space {
        top: 20vh;
        font-size: 9vw;
        right: 0;
        z-index: 1;
        color: #FFFFFF80
    }
</style>