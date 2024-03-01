<template>
    <div id="container-card">
        <div class="card">
            <div class="content-card" >
                <img class="content-img" src="../assets/reed-richards.png" alt="bachelor" width="100%" height="100%">
                <h2 class="content-title">Reed Richards</h2>
            </div>
            <div class="glow" @mousemove="cardAnime(), glowAnime()" @mouseleave="moveOut()">

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
                
                const X = event.offsetX  / card.offsetWidth - 0.5;
                const Y = 0.5 - event.offsetY / card.offsetHeight;

                const rotateX = X*60;
                const rotateY = Y*60;
                console.log(-rotateX+ ' '+ -rotateY);

                card.style.transform = 'rotateX('+ rotateX +'deg) rotateY('+rotateY+'deg)';
                card.style.boxShadow = -rotateX/1.4 + 'px '+ rotateY/1.4 +'px red';
                card.style.opacity = 1;
            },
            glowAnime(){
              
                const glow = document.querySelector('.glow');
                const X = event.offsetX  / glow.offsetWidth - 0.5;
                const Y = 0.5 - event.offsetY / glow.offsetHeight;

                let glowX = (X -0.5) * 100;
                let glowY = (Y -0.5) * 100;
                const rotateX = X*60;
                const rotateY = Y*60;
                console.log('radial-gradient(circle at'+glowX+'% '+glowY+'%, rgb(184, 196, 211), transparent)');
                glow.style.transform = 'rotateX('+ (X - 0.5)  +'deg) rotateY('+(Y - 0.5)  +'deg)';
                glow.style.background= 'radial-gradient(circle at '+glowY+'% '+ -glowX+'%, rgb(185, 106, 3), transparent)';
                glow.style.boxShadow = -rotateX/1.8 + 'px '+ rotateY/1.8 +'px rgba(0,0,0,0.28)';
            },

            moveOut(){
                const card = document.querySelector('.card');
                const glow = document.querySelector('.glow');

                card.style.transform = 'rotateX('+ 0 +'deg) rotateY('+0+'deg)';
                card.style.boxShadow = '';
                glow.style.transform = 'rotateX('+ 0  +'deg) rotateY('+ 0 +'deg)';
                glow.style.background= 'radial-gradient(circle at '+50+'% '+ 0+'%, rgb(185, 106, 3), transparent)';
                glow.style.boxShadow = '';
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
    height: 500px;
    display: flex;
    flex-direction: column;
    justify-content: start;
    perspective: 500px;
    border-radius: 25px;
    
}

.content-card {
    width: 100%;
    height: 100%;
    overflow: hidden;
    border-radius: 25px;
    transition:  all 0.15s ease-out;
    border: 3px red solid;
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
    background: radial-gradient(circle at 50% 0%, rgb(185, 106, 3), transparent);
    perspective: 500px;
}

</style>