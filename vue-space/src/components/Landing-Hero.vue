<template>
    <header>
        <div class="hero-container">
            <div class="hero-bg">
            </div>
            <div class="hero-fg">
                    <!-- <img src="../assets/astronaut copy.png" alt=""> -->
            </div>
            <h1 class="letsTalk">Let's talk</h1>
            <h1 class="space">Space</h1>
        </div>
    </header>
</template>

<script>

export default {
    name: 'Landing-Hero',
    data() {
        return {
            imgUrl1: '../assets/astronaut.jpg'
        }
    }
}
</script>

<style scoped>
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
        background: url(../assets/astronaut.jpg) right center/cover no-repeat;
        z-index: 0;
    }

    .hero-fg {
        position: absolute;
        top: 0;
        left: 0;
        min-width: 100%;
        min-height: 100%;
        background: url('../assets/astronaut copy.png') right center/cover no-repeat;
        z-index: 2;
    }

    h1.letsTalk, h1.space {
        font-family: 'Roboto Condensed', sans-serif;
        position: absolute;
        text-transform: uppercase;
        font-size: 140px;
        color: #FFF;
    }

    h1.letsTalk {
        right: 600px;
        z-index: 3;
        top: 25vh
    }

     h1.space {
        top: 20vh;
        font-size: 120px;
        right: 130px;
        z-index: 1;
        color: #FFFFFF80
    }
</style>
