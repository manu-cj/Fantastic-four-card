<template>
    <div id="container-card">
        <div class="card" v-for="fantastic in fourFantastic" :key="fantastic">
            <div class="content-card" >
                <img class="content-img" :src="fantastic.image" alt="bachelor" width="100%" height="100%" />
                <div class="glow-title"></div>
                <div class="content-title"><h2>{{ fantastic.name }} </h2></div>
                
            </div>
            <div class="glow" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fantastic.color +', transparent)'}"
             @mousemove="cardAnime(), glowAnime(fantastic.color), moveOut(fantastic.color)">

            </div>
        </div>
    </div>
    
</template>

<script>




    export default {
        data(){
            return {
                fourFantastic: [
                    {
                        'name': 'Reed Richards',
                        'image': 'https://64.media.tumblr.com/36acc53f0eac3056315c5d8cb0d1c6f0/tumblr_pq81asUB4i1ueqxblo1_400.png',
                        'color': 'rgba(0,181,255,1)'
                    },
                    {
                        'name': 'Susan Richards',
                        'image': 'https://64.media.tumblr.com/f75c5403074161aa7f5c22f7fdc6fa9d/tumblr_p8omonFaSt1trp40so1_1280.jpg',
                        'color': 'rgba(0,255,252,0.8211659663865546)'
                    },

                    {
                        'name': 'Johnny Storm',
                        'image': 'https://pbs.twimg.com/profile_images/1208221160787369984/re5-Al9I_400x400.jpg',
                        'color': 'rgba(253,187,45,1)'
                    },

                    {
                        'name': 'Benjamin Grimm',
                        'image': 'https://i.pinimg.com/564x/f6/bc/0d/f6bc0d2bdb161b598aed1506c4408b67.jpg',
                        'color': 'rgba(173,96,66,1)'
                    },
                ]
            }
        },

        methods: {
            cardAnime(){
                const card = document.querySelectorAll('.card');
                
                for (let i = 0; i < card.length; i++) {
                    console.log(i);
                    const X = event.offsetX  / card.item(i).offsetWidth - 0.5;
                    const Y = 0.5 - event.offsetY / card.item(i).offsetHeight;

                    const rotateX = X*60;
                    const rotateY = Y*60;

                    card.item(i).addEventListener('mousemove', () => {
                        card[i].style.transform = 'rotateX('+ rotateX +'deg) rotateY('+rotateY+'deg)';
                        card[i].style.boxShadow = -rotateX/1.4 + 'px '+ rotateY/1.4 +'px rgb(0, 68, 255)';
                        card[i].style.opacity = 1;
                    })  
                }
                
                
            },
            glowAnime(color){
              
                const glow = document.querySelectorAll('.glow');
                for (let i = 0; i < glow.length; i++) {
                    const X = event.offsetX  / glow.item(i).offsetWidth - 0.5;
                    const Y = 0.5 - event.offsetY / glow.item(i).offsetHeight;

                    let glowX = (X -0.5) * 100;
                    let glowY = (Y -0.5) * 100;
                    const rotateX = X*60;
                    const rotateY = Y*60;

                    glow.item(i).addEventListener('mousemove', () => {
                        glow.item(i).style.boxShadow = -rotateX/1.6 + 'px '+ rotateY/1.6 +'px rgba(0,0,0,0.28)';
                        glow.item(i).style.transform = 'rotateX('+ rotateX + 0.5 +'deg) rotateY('+ rotateY + 0.5 +'deg)';
                        glow.item(i).style.background= 'radial-gradient(circle at '+ glowX+'% '+ -glowY+'%, '+ color +', transparent)';
                    })
                    
                    
                }

                
                
            },

            moveOut(color){
                const card = document.querySelectorAll('.card');
                const glow = document.querySelectorAll('.glow');

                for (let i = 0; i < glow.length; i++) {
                    glow.item(i).addEventListener('mouseleave', () => {
                        card[i].style.transform = 'rotateX('+ 0 +'deg) rotateY('+0+'deg)';
                        card[i].style.boxShadow = '';
                        glow[i].style.transform = 'rotateX('+ 0  +'deg) rotateY('+ 0 +'deg)';
                        glow[i].style.background= 'radial-gradient(circle at '+50+'% '+ 0+'%,'+ color +', transparent)';
                        glow[i].style.boxShadow = '';   
                    })
                    
                        
                }
            },
            
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
    gap: 50px;
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
    border: 4px rgb(0, 68, 255) solid;
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
    overflow: hidden;
    background: radial-gradient(circle at 0% 0%, rgb(3, 118, 185), transparent);
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
    
    perspective: 500px;
}

.glow-title {
    position: absolute;
    top: 93%;
    left: 20%;
    width: 20%;
    height: 2%;
    animation-name: titleColor;
    animation-duration: 30s;
    animation-iteration-count: infinite;
    background: radial-gradient(circle at 50% 0%, rgb(185, 106, 3), transparent);
    
}

@keyframes titleColor {
    0% {
        width: 20%;
    }

    25% {
        left: 20%;
        width: 65%;
    }

    40% {
        left: 20%;
        width: 65%;
    }

    50% {
        left: 60%;
        width: 20%;
        
    }

    75%{
        left: 65%;
        width: 20%;

    }

    100% {
        left: 20%;
        width: 20%;
    }
    
}
</style>