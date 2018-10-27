<template>
    <section class="articles">
        <div class="content-wrapper center-div">
            <h2 class="articles-heading">Articles</h2>
            <input type="text" v-model="searchString" placeholder="Search articles">

            <article v-for="(article, index) in articles" :key=index class="article-card">
                <img :src="article.imgUrl" alt="">
                <div class="article-text">
                    <h3>{{ article.title }}</h3>
                    <h4>{{ article.datePosted }}</h4>
                    <p>{{ article.shortText }}</p>
                </div>
            </article>
        </div>
    </section>
</template>

<script>
export default {
    name: 'Articles',
    data() {
        return {
            searchString: '',
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
    }
}
</script>

<style scoped>

    section.articles {
        background: #000;
    }

    .article-card {
        background: #FFF;
        display: flex;
        flex-flow: row nowrap;
        padding: 10px;
    }

    .article-text {
        padding: 0 10px;
        text-align: left;
    }





</style>
