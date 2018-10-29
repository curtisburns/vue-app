<template>
    <section class="articles">
        <div class="content-wrapper center-div">
            <h2 class="articles-heading">Articles</h2>
            <div class="input-container">
                <input type="text" v-model="searchString" placeholder="Search articles">
                <span @click="listView" :class="['list-view', view === 'list' ? 'active' : 'inactive']"><img src="../assets/list-view.png" alt="list-view"/></span>
                <span @click="gridView" :class="['grid-view', view === 'grid' ? 'active' : 'inactive']"><img src="../assets/grid-view.png" alt="grid-view"/></span>
            </div>
       

            <p v-if='searchString && !pageOfArticles.length' class="no-results">No results for ' {{searchString}} '</p>
            <transition-group name="changeView" tag="div" :class="['article-container', view === 'grid' ? 'article-container-grid' : '']">
                <div v-for="(article, index) in pageOfArticles" :key=index :class="[view === 'list' ? 'article-card-list' : 'article-card-grid', pageTurn && 'turning']">
                    <article :class="[view === 'list' ? 'article-card-list' : 'article-card-grid']">
                        <img :src="article.imgUrl" alt="">
                        <div class="article-text">
                            <h3>{{ article.title }}</h3>
                            <h4>{{ article.datePosted }}</h4>
                            <hr />
                            <p>{{ article.shortText }}</p>
                        </div>
                    </article>
                </div>
            </transition-group>

            <div class="page-number-container">
                <a v-for="(page, index) in numberOfPages" :key=index @click="selectPage" :class="{'highlight': highlightPageNumber(page)}">{{ page }}</a>
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
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                 {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                },
                {   
                    imgUrl: require('../assets/bluerock.png'),
                    title: 'Bizarre, Blue Space Rock Even Weirder Than Astronomers Thought',
                    datePosted: 'October 24, 2018 | Article | 12 min read',
                    shortText: 'A bizarre, blue asteroid that acts like a comet and appears to be responsible for the annual Geminid meteor shower made a close flyby of Earth last year, giving astronomers an opportunity to study the object in unprecedented detail.'
                },
                {   
                    imgUrl: require('../assets/nebula.png'),
                    title: 'Space Pirates Take Warning: This \'Skull and Crossbones Nebula\' Is Full of Gas and Baby Stars',
                    datePosted: 'October 24, 2018 | Article | 15 min read',
                    shortText: 'The constellation NGC 2467 looks like a skull and crossbones.'
                }
               
            ],
            searchedArticles: [],
            articlesPerPage: 6,
            currentPage: 1,
            pageTurn: ''
        }
    },
    methods: {
        gridView() {
            this.view = "grid"
        },
        listView() {
            this.view = "list"
        },
        initArticles() {
            if (!this.searchedString) {
                this.searchedArticles = this.articles;
            }
        },
        selectPage({target: { innerText }} ) {
            if (innerText !== this.currentPage) {
                this.pageTurn = 'turning';
                setTimeout(() => {
                    this.currentPage = innerText;
                    this.pageTurn = '';
                }, 400);
            }
        },
        highlightPageNumber: function(page) {
            return page === parseInt(this.currentPage,10);
        }
    },
    watch: {
        searchString: function(string) {
            this.searchedArticles = this.articles.filter(article => article.title.toLowerCase().includes(string.toLowerCase()));
        }
    },
    mounted() {
        this.initArticles();
    },
    computed: {
        pageOfArticles: function() {
            const startingIndex = (this.currentPage - 1) * this.articlesPerPage;
            return this.searchedArticles.slice(startingIndex, (this.articlesPerPage + startingIndex));
        },
        numberOfPages: function() {
            const count = Math.ceil(this.searchedArticles.length / this.articlesPerPage);
            const pages = [];
            for (let i = 1; i <= count; i++) {
                pages.push(i);
            }
            return pages;
        }
    }
}
</script>

<style scoped>

    section.articles {
        position: relative;
        background: #000;
        text-align: left;
        min-height: 1300px;
        background: url('../assets/article-background.jpg') center center/cover no-repeat;
    }

    section.articles::after {
        content: ' ';
        height: 100%;
        width: 100%;
        background: linear-gradient(top, #000000 0%, #00000090 90%, #00000050 100%);
        position: absolute;
        top: 0;
        z-index: 0;
    }

    .articles-heading {
        font-family: 'Roboto Condensed', sans-serif;
        color: #FFF;
        padding: 20px 0;
        text-transform: uppercase;
        position: relative;
        z-index: 2;
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
        z-index: 3;
        color: #0E0E0E;
    }

    input:focus {
        outline: none;
        box-shadow: 0 0 10px #FFF;
    }

    .article-container {
        width:100%;
        min-height: 1080px;
        position: relative;
        z-index: 1;
    }

    .article-container-grid {
        display: flex;
        flex-flow: row wrap;
        min-height: 840px;
    }

    div.article-card-list {
        display: flex;
        flex-flow: row nowrap;
        padding: 10px 0;
        box-sizing: border-box;
    }

    div.article-card-grid {
        padding: 10px 0;
        width: 33%;
        box-sizing: border-box;
        
    }

    article.article-card-list {
        background: #FFF;
        display: flex;
        flex-flow: row nowrap;
        padding: 10px;
        box-sizing: border-box;
    }

    article.article-card-grid {
        background: #FFF;
        padding: 10px;
        width: 95%;
        box-sizing: border-box;
        min-height: 400px;
    }

    hr {
        width: 25%;
        display: inline-block;
    }

    article.article-card-list img {
        max-height: 140px;
    }

    article.article-card-grid img {
        width: 100%;
    }

    .article-text {
        padding: 0 10px;
        text-align: left;
    }

    h3 {
        margin-bottom: 5px;
    }

    article.article-card-grid h3 {
        font-size: .9em;
    }

    h4 {
        line-height: 1.6em;
        font-size: .9em;
    }

     article.article-card-grid h4 {
        font-size: .7em;
    }

    p {
        font-size: .9em;
    }

    article.article-card-grid p {
        font-size: .7em;
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
        z-index: 2;
        opacity: .8;
        transition: all .4s;
    }

    .grid-view.inactive, .list-view.inactive  {
        width: 20%;
        background: #FFF;
        position: absolute;
        z-index: 1;
        opacity: .5;
        transition: all .4s;
    }

    .no-results {
        font-size: 1.2em;
        color: #FFF;
    }

    .changeView-move {
        transition: transform 1s;
    }

    .page-number-container {
        text-align: center;
        transition: all .4s;
        position: relative;
        z-index: 1;
        background: #00000080;
    }

    .page-number-container a{
        margin: 0 5px;
        color: #FFFFFF80;
        cursor: pointer;
        font-size: 1.2em;
    }

    .turning {
        transition: all .4s;
        transform: translateX(-2000px);
    }

    .page-number-container a.highlight, a:hover {
        color: #FFF;
    }

    



</style>
