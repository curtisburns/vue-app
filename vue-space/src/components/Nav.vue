<template>
    <nav>
        <ul>
            <li><span></span> <a>Explore the gallaxy</a> </li>
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
        position: relative;
        z-index: 99;
    }

    ul {
        width: 100%;
        margin-block-end: 0;
        margin-block-start: 0;
        padding-inline-end: 0;
        padding-inline-start: 0;
        padding-top: 5px;
    }

    ul li {
        margin: auto;
        width: 50%;
        list-style: none;
        text-align: right;
    }

    ul li a {
        color: #FFFFFF80;
        width: 30%;
    }

    span {
        margin-right: 10px;
        width: 70%;
        display: inline-block;
        border-top: 1px #FFFFFF80 solid;
        height: .3em;
    }



</style>
