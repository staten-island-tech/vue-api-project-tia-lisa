<template>
    <div>
       <ul class="featured-list">
            <li class="featured-list-item">testingggg</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: "FeaturedPage",

    data() {
        return{
            animes:[]
        };
    },


    methods: {
        fetchAnime: async function(){
            try{
                const result = await fetch(
                    "https://api.jikan.moe/v3/search/anime?order_by=score"
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
