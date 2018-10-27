<template>
    <nav>
        <ul>
            <li><span class="line-container"><span class="line"></span></span> <a>Explore the gallaxy.</a> </li>
        </ul>
    </nav>  
</template>
<script>

export default {
    name: 'Nav'
}

</script>
<style scoped>
    nav {
        width: 100%;
        position: absolute;
        top: 0;
        z-index: 99;
    }

    ul {
        width: 100%;
        margin-block-end: 0;
        margin-block-start: 0;
        padding-inline-end: 0;
        padding-inline-start: 0;
        padding-top: 1vh;
    }

    ul li {
        margin: auto;
        width: 50%;
        list-style: none;
        text-align: right;
        white-space: nowrap;
    }

    ul li a {
        color: #FFFFFF80;
        width: 30%;
        white-space: nowrap;
        font-size: 1.4vw;
        cursor: pointer;
    }

    .line-container {
        width: 70%;
        position: relative;
        display: inline-block;
        margin-right: 2vw;
    }

    .line {
        transform: translateY(-450%);
        width: 0%;
        display: inline-block;
        border-top: .1vw #FFFFFF80 solid;
        position: absolute;
        left: 0;
        animation: caterpillar 3s infinite ease-in-out
    }

    @keyframes caterpillar {
        10% {
            width: 0%;
        }

        20% {
            width: 100%;
        }
        80% {
            width: 100%;
        }
        100% {
            left: auto;
            right: 0;
            width: 0%;
        }
    }


</style>
