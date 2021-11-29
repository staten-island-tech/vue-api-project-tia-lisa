<template>
  <div>

<section class="gallery-container">
        <div class="gallery" aria-label="image-gallery">
            <ul class="gallery-view">
                <li id="img1" tabindex="0" class="gallery-image">
                    <img class="slide-img" src="@/assets/img-1.jpg" alt="Bar Front">
                    <div class="snapper">
                        <a href="#img5" class="prev">❮</a>
                        <a href="#img2" class="next">❯</a>
                    </div>
                </li>
                <li id="img2" tabindex="0" class="gallery-image">
                    <img class="slide-img" alt="Chef at Work" src="@/assets/img-2.png">
                    <div class="snapper"></div>
                        <a href="#img1" class="prev">❮</a>
                        <a href="#img3" class="next">❯</a>
                </li>
                <li id="img3" tabindex="0" class="gallery-image">
                    <img class="slide-img" alt="Nigiri" src="@/assets/img-3.png">
                    <div class="snapper"></div>
                        <a href="#img2" class="prev">❮</a>
                        <a href="#img4" class="next">❯</a>
                </li>
                                <li id="img4" tabindex="0" class="gallery-image">
                    <img class="slide-img" alt="Nigiri" src="@/assets/img-4.png">
                    <div class="snapper"></div>
                        <a href="#img3" class="prev">❮</a>
                        <a href="#img5" class="next">❯</a>
                </li>
                                <li id="img5" tabindex="0" class="gallery-image">
                    <img class="slide-img" alt="Nigiri" src="@/assets/img-5.png">
                    <div class="snapper"></div>
                        <a href="#img4" class="prev">❮</a>
                        <a href="#img1" class="next">❯</a>
                </li>
            </ul>
        </div>    
</section>        


 
  </div>
</template>

<script>
export default {
  name: "Gallery",
};
</script>

<style>


.gallery-container{
    display: flex;
    align-items: center;
    flex-direction: column;
    justify-content: center;
    height: 100vh;
    width: 100vw;
    background-color: blue;
}

.gallery {
  position: relative;
  height: 70vh;
  width: 60vw;
  display: flex;
  align-items: center;
}

ul, li {
  list-style: none;
  margin: 0;
  padding: 0;
}

.gallery-view {
  display: flex;
  overflow-x: scroll;
  scroll-behavior: smooth; /*smooth transition scroll*/
  scroll-snap-type: x mandatory; /*snaps to image*/
}
 
.gallery-image {
  position: relative;
  flex: 0 0 100%; /* 0 grow, 0 shrink, 100% width*/
  width: 100%;}
   


.slide-img {
  display: block;
  height: 100%;
  width: 100%;
  object-fit: cover; /*images fill container*/
}

.snapper {
  position: absolute;
  bottom: 0rem;
  width: 100%;
  height: 100%;
  scroll-snap-align: center;
}

* {
  box-sizing: border-box;
}

*::-webkit-scrollbar {
  width: 0;
}

* {
  -ms-overflow-style: none;
}



/*position, size of arrows (text turns to arrows*/
.gallery::before,
.gallery::after,
.prev,
.next {
  cursor: pointer;
  position: absolute;
  top: 50%;
  width: auto;
  padding: 16px;
  margin-top: -50px;
  color: black;
  font-weight: bold;
  font-size: 3rem;
  user-select: none;
  -webkit-user-select: none;
}


.prev {
  left: 0rem;
}

.next {
  right: 0rem;
}



.prev:hover,
.next:hover {
  background-color: rgba(0, 0, 0, 0.8);

}
</style>