<template>
    <div class="container">
        <h1 class="featured">Featured List</h1>
       <ul class="featured-list">
            <li class="featured-list-item" v-for="anime in animes" :key="anime.title">
                <img :src="anime.image_url" alt="anime-cards" class="img">
                <div>                {{anime.title}}</div>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "FeaturedPage",

    data() {
        return{
            animes:[],
        };
    },

    created: function(){
        this.fetchAnime();
    },


    methods: {
        fetchAnime: async function(){
            try{
                const result = await fetch(
                    "https://api.jikan.moe/v3/search/anime?order_by=score&limit=10"
                );
                 const data = await result.json();
                 this.animes = data.results
                 console.log(data)
            }
            catch(error){
                alert(error)
            }
        }
    }
}
</script>
<style>

.container{
    display: flex;
    align-items: center;
    flex-direction: column;
}

.featured-list{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    width: 90rem;
    border-style: solid;
}

.featured-list-item{
    display: flex;
    flex-direction: column;
    align-items: center;
    background-size: cover;
    height: 20rem;
    width: 14rem;
    margin-top: 2rem;
    margin-bottom: 2rem;
    margin-right: 1rem;
    border-style: solid;
    padding: 1rem;
    padding-bottom: 2rem;

}

.img{
    height: 20rem;
    width: 14rem;
    margin-bottom: .5rem;
}






</style>