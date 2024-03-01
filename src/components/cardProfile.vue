<template>
    <div id="container-card">
        <div class="card">
            <div class="content-card" >
                <img class="content-img" src="../assets/reed-richards.png" alt="bachelor" width="100%" height="100%">
                <h2 class="content-title">Reed Richards</h2>
            </div>
            <div class="glow" @mousemove="cardAnime(), glowAnime()">

            </div>
        </div>
    </div>
    
</template>

<script>




    export default {
        data(){
            return {
                
            }
        },

        methods: {
            cardAnime(){
                const card = document.querySelector('.card');
                
                const X = (event.offsetX ) / card.offsetWidth;
                const Y = (event.offsetY) / card.offsetHeight;
        
                console.log((X - 0.5) * -60 +' et '+ (Y - 0.5 - Y) * -60);

                 card.style.transform = 'rotateX('+ (X - 0.5) * 60 +'deg) rotateY('+(Y - 0.5) * -60 +'deg)';
                 

      
      
                

                 card.style.opacity = 1;
                    
            },
            glowAnime(){
              
                const glow = document.querySelector('.glow');
                const X = (event.offsetX) / glow.offsetWidth;
                const Y = (event.offsetY) / glow.offsetHeight;
        
                console.log(( X - 0.5) * -60 +' et g '+ (Y - 0.5 - Y) * -60);

                 glow.style.transform = 'rotateX('+ (X - 0.5)  +'deg) rotateY('+(Y - 0.5)  +'deg)';

      
      
                 

                 
            }
            
            
        },

        computed: {

        },

        mounted() {
        }
        
    }
</script>

<style scoped>

#container-card {
    width: 100%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    align-content: center;
}
.card {
    width: 20%;
    height: 350px;
    display: flex;
    flex-direction: column;
    justify-content: start;
    perspective: 500px;
}

.content-card {
    width: 100%;
    height: 100%;
    overflow: hidden;
    border-radius: 25px;
    transition:  all 0.15s ease-out;
}

.content-img{
    width: 100%;
    height: 80%;
    object-fit: cover;
    margin: none;
}

.content-title{
    width: 100%;
    height: 30%;
    object-fit: cover;
    background-color: rgb(0, 89, 255);
    color: rgba(250, 235, 215, 0.952);
    margin: 0;
    text-align: center;
    padding-top: 20px;
}

.glow {
    border-radius: 25px;
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    transition:  all 0.15s ease-out;
    mix-blend-mode: hard-light;
    background: radial-gradient(circle at 50% 0%, rgb(184, 196, 211), transparent);
    perspective: 500px;
}

</style>