<template>
    <div>
       <ul class="featured-list">
            <li class="featured-list-item" v-for="anime in animes" :key="anime.title">
                {{anime.title}}
                <img :src="anime.image_url" alt="">
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

.featured-list{
    display: flex;
    flex-wrap: wrap;
    justify-content: space-evenly;
}

.featured-list-item{
    display: flex;
    flex-direction: column;
    align-items: center;
    background-size: cover;
    height: 20rem;
    width: 20rem;
    margin: 2rem;
}




</style>