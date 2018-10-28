<template>
    <section class="articles">
        <div class="content-wrapper center-div">
            <h2 class="articles-heading">Articles</h2>
            <div class="input-container">
                <input type="text" v-model="searchString" placeholder="Search articles">
                <span @click="listView" :class="['list-view', view === 'list' ? 'active' : 'inactive']"><img src="../assets/list-view.png" alt="list-view"/></span>
                <span @click="gridView" :class="['grid-view', view === 'grid' ? 'active' : 'inactive']"><img src="../assets/grid-view.png" alt="grid-view"/></span>
            </div>
        <div :class="['article-container', view === 'grid' ? 'article-container-grid' : '']">
            <article v-for="(article, index) in articles" :key=index :class="[view === 'list' ? 'article-card-list' : 'article-card-grid']">
                <img :src="article.imgUrl" alt="">
                <div class="article-text">
                    <h3>{{ article.title }}</h3>
                    <h4>{{ article.datePosted }}</h4>
                    <hr />
                    <p>{{ article.shortText }}</p>
                </div>
            </article>
        </div>
            
        </div>
    </section>
</template>

<script>
export default {
    name: 'Articles',
    data() {
        return {
            searchString: '',
            view: 'list',
            articles: [
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                }
            ]
        }
    },
    methods: {
        gridView() {
            this.view = "grid"
            console.log(this.view);
        },
        listView() {
            this.view = "list"
            console.log(this.view);
        }
    }
}
</script>

<style scoped>

    section.articles {
        background: #000;
        text-align: left;
    }

    .articles-heading {
        font-family: 'Roboto Condensed', sans-serif;
        color: #FFF;
        padding: 20px 0;
        text-transform: uppercase;
    }

    .input-container {
        margin: auto;
        width: 550px;
        height: 30px;
        position: relative;
        margin-bottom: 20px;
    }

    input {
        font-size: 1.1em;
        width: 80%;
        box-sizing: border-box;
        height: 100%;
        border-radius: 15px;
        padding: 0 10px;
        box-shadow: #00000050 10px 0 10px;
        position: relative;
        z-index: 2;
        color: #0E0E0E;
    }

    input:focus {
        outline: none;
        box-shadow: 0 0 10px #FFF;
    }

    .article-container {
        width:100%;
    }

    .article-container-grid {
        display: flex;
        flex-flow: row wrap;
    }

    .article-card-list {
        background: #FFF;
        display: flex;
        flex-flow: row nowrap;
        padding: 10px;
        margin-bottom: 20px;
        box-sizing: border-box;
    }

    .article-card-grid {
        background: #FFF;
        padding: 10px;
        margin: 20px;
        width: 25%;
        box-sizing: border-box;
    }

    hr {
        width: 25%;
        display: inline-block;
    }

    article img {
        max-height: 140px;
    }

    .article-text {
        padding: 0 10px;
        text-align: left;
    }

    h3 {
        margin-bottom: 5px;
    }

    h4 {
        line-height: 1.6em;
        font-size: .9em;
    }

    p {
        font-size: .9em;
    }

    .list-view, .grid-view {
        box-sizing: border-box;
        display: inline-block;
        height: 100%;
        box-shadow: #00000050 10px 0 10px;
        transform: translateX(-15px);
        border-radius: 0 15px 15px 0;
        text-align: right;
        padding-right: 15px;
    }

    .list-view img, .grid-view img {
        height: 100%;
    }

    .grid-view img {
        height: 75%;
        transform: translateY(15%);
    }

    .list-view img {
        transform: translateX(18%);
    }

    .list-view.active, .grid-view.active {
        width: 11%;
        background: #FFF;
        position: absolute;
        z-index: 1;
        opacity: .8;
        transition: all .4s;
    }

    .grid-view.inactive, .list-view.inactive  {
        width: 20%;
        background: #FFF;
        position: absolute;
        z-index: 0;
        opacity: .5;
        transition: all .4s;
    }




</style>
