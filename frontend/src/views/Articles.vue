<template>
    <div>
        <h2>Articles : </h2>
        <div class="article" v-for="item in articles" :key="item.id">
            <h3>{{item.title}}</h3>
            <p>{{item.body}}</p>
        </div>
    </div>
</template>

<script>
    import axios from 'axios'
    export default {
        name: "Articles",
        data(){
            return{
                articles:null,
            }
        },
        created(){
            this.getArticles();
        },
        methods:{
            getArticles(){
                axios
                    .get('/api/articles')
                    .then( res =>{
                        const {data:{data}} = res
                        this.articles = data
                        console.log("TEST")
                    })
            }
        }
    }
</script>

<style scoped>

</style>