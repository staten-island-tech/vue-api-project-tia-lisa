<template>
    <div class="container">
        <div class="featured-container">
            <h1 class="featured">Featured List</h1>
            <ul class="featured-list">
                    <li class="featured-list-item" v-for="anime in animes" :key="anime.title">
                        <img :src="anime.image_url" alt="anime-cards" class="img">
                        <div>                {{anime.title}}</div>
                    </li>
                </ul>
        </div>
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
    background-color: #f4f4f4;
}

.featured-list{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
    width: 67.5rem;
    border-style: solid;
    background-color: black;
}

.featured-list-item{
    display: flex;
    flex-direction: column;
    align-items: center;
    background-color: white;
    height: 15rem;
    width: 10.5rem;
    margin-top: 1rem;
    margin-bottom: 2rem;
    margin-right: .25rem;
    border-style: solid;
    padding: 1rem;
    padding-bottom: 2rem;
    font-size: .8rem;


}

.img{
    height: 15rem;
    width: 10.5rem;
    margin-bottom: .125rem;
}

.featured-container{
    border-style: solid;
}






</style>