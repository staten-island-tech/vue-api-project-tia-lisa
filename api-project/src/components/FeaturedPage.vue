<template>
    <div>
       <ul class="featured-list">
            <li class="featured-list-item" v-for="anime in animes" :key="anime.title">
                {{anime.title}}
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
