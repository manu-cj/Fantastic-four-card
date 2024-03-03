<template>
<div id="container-card">
    <div id="carrousel-div">
        <div class="button" style="justify-content: start;">
            <button id="buttonPrevious" v-if="carrouselIndex > 0" @mouseover="carrouselPrevious()" @click="carrouselIndex--">Previous</button>
        </div>
        
        <div class="card">
            <div class="content-card" :style="{borderColor: fourFantastic[carrouselIndex].color}">
                <img class="content-img" :src="fourFantastic[carrouselIndex].image" alt="bachelor" width="100%" height="100%" />
                <div class="glow-title" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fourFantastic[carrouselIndex].color +', transparent)'}"></div>
                <div class="content-title">
                    <h2 :style="{color : fourFantastic[carrouselIndex].color}">{{ fourFantastic[carrouselIndex].name }} </h2>
                </div>
            </div>

            <div class="glow" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fourFantastic[carrouselIndex].color +', transparent)'}" 
                @mousemove="cardAnime(fourFantastic[carrouselIndex].color), glowAnime(fourFantastic[carrouselIndex].color), moveOut(fourFantastic[carrouselIndex].color)">
            </div>

        </div>

        <div class="button" style="justify-content: end;">
            <button id="buttonNext" v-if="carrouselIndex < fourFantastic.length - 1" @mouseover="carrouselNext()" @click="carrouselIndex++">Next</button>
        </div>
        
    </div>

    <div class="card" v-for="fantastic in fourFantastic" :key="fantastic">
        <div class="content-card" :style="{borderColor: fantastic.color}">
            <img class="content-img" :src="fantastic.image" alt="bachelor" width="100%" height="100%" />
            <div class="glow-title" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fantastic.color +', transparent)'}"></div>
            <div class="content-title">
                <h2 :style="{color : fantastic.color}">{{ fantastic.name }} </h2>
            </div>
        </div>

        <div class="glow" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fantastic.color +', transparent)'}"
         @mousemove="cardAnime(fantastic.color), glowAnime(fantastic.color), moveOut(fantastic.color)">
        </div>
    </div>
</div>
</template>

<script>
export default {
    data() {
        return {
            fourFantastic: [{
                    'name': 'Reed Richards',
                    'image': 'https://64.media.tumblr.com/36acc53f0eac3056315c5d8cb0d1c6f0/tumblr_pq81asUB4i1ueqxblo1_400.png',
                    'color': 'rgba(92,196,255,0.7287289915966386)'
                },
                {
                    'name': 'Susan Storm',
                    'image': 'https://64.media.tumblr.com/f75c5403074161aa7f5c22f7fdc6fa9d/tumblr_p8omonFaSt1trp40so1_1280.jpg',
                    'color': 'rgba(167,224,244,0.7287289915966386)'
                },

                {
                    'name': 'Johnny Storm',
                    'image': 'https://pbs.twimg.com/profile_images/1208221160787369984/re5-Al9I_400x400.jpg',
                    'color': 'rgba(255,218,0,0.4743872549019608)'
                },

                {
                    'name': 'Benjamin Grimm',
                    'image': 'https://i.pinimg.com/564x/f6/bc/0d/f6bc0d2bdb161b598aed1506c4408b67.jpg',
                    'color': 'rgba(173,96,66,1)'
                },
                {
                    'name': 'Victor Von Fatalis',
                    'image': 'https://wegotthiscovered.com/wp-content/uploads/2022/05/Doctor-Doom-Fortnite-X-Marvel-1200x900.jpg',
                    'color': 'rgba(0,154,75,0.7287289915966386)'
                },
            ],

            carrouselIndex: 0,
        }
    },

    methods: {
        cardAnime(color) {
            const card = document.querySelectorAll('.card');

            for (let i = 0; i < card.length; i++) {
                console.log(i);
                const X = event.offsetX / card.item(i).offsetWidth - 0.5;
                const Y = 0.5 - event.offsetY / card.item(i).offsetHeight;

                const rotateX = X * 50;
                const rotateY = Y * 50;

                card.item(i).addEventListener('mousemove', () => {
                    card[i].style.transform = 'rotateX(' + rotateX + 'deg) rotateY(' + rotateY + 'deg)';
                    card[i].style.boxShadow = -rotateX / 1.4 + 'px ' + rotateY / 1.4 + 'px ' + color;
                    card[i].style.opacity = 1;
                })
            }

        },
        glowAnime(color) {

            const glow = document.querySelectorAll('.glow');
            for (let i = 0; i < glow.length; i++) {
                const X = event.offsetX / glow.item(i).offsetWidth - 0.5;
                const Y = 0.5 - event.offsetY / glow.item(i).offsetHeight;

                let glowX = (X - 0.5) * 100;
                let glowY = (Y - 0.5) * 100;
                const rotateX = X * 30;
                const rotateY = Y * 30;

                glow.item(i).addEventListener('mousemove', () => {
                    glow.item(i).style.boxShadow = -rotateX / 1.6 + 'px ' + rotateY / 1.6 + 'px rgba(0,0,0,0.28)';
                    glow.item(i).style.transform = 'rotateX(' + rotateX + 0.5 + 'deg) rotateY(' + rotateY + 0.5 + 'deg)';
                    glow.item(i).style.background = 'radial-gradient(circle at ' + glowX + '% ' + -glowY + '%, ' + color + ', transparent)';
                })
            }
        },

        moveOut(color) {
            const card = document.querySelectorAll('.card');
            const glow = document.querySelectorAll('.glow');

            for (let i = 0; i < glow.length; i++) {
                glow.item(i).addEventListener('mouseleave', () => {
                    card[i].style.transform = 'rotateX(' + 0 + 'deg) rotateY(' + 0 + 'deg)';
                    card[i].style.boxShadow = '';
                    glow[i].style.transform = 'rotateX(' + 0 + 'deg) rotateY(' + 0 + 'deg)';
                    glow[i].style.background = 'radial-gradient(circle at ' + 50 + '% ' + 0 + '%,' + color + ', transparent)';
                    glow[i].style.boxShadow = '';
                })
            }
        },

        carrouselNext() {
            let buttonNext = document.querySelector('#buttonNext');
            if (this.carrouselIndex === 0) {
                    buttonNext.classList.add("reed");
                    buttonNext.style.backgroundColor = '#0093E9';
                    buttonNext.style.backgroundImage = 'linear-gradient(160deg, #0093E9 0%, #80D0C7 100%)';
                    
                    buttonNext.addEventListener('mouseleave', () => {
                        buttonNext.classList.remove("reed");
                        buttonNext.style.width = '60%';
                        buttonNext.style.backgroundColor = '';
                        buttonNext.style.backgroundImage = '';
                    })
            }
            if (this.carrouselIndex === 1) {
                    buttonNext.classList.add("susan");
                    
                    
                    buttonNext.addEventListener('mouseleave', () => {
                        buttonNext.classList.remove("susan");
                        buttonNext.style.width = '60%';
                        buttonNext.style.backgroundColor = '';
                        buttonNext.style.backgroundImage = '';
                    })
            }
            if (this.carrouselIndex === 2) {
                    buttonNext.classList.add("johnny");
                    
                    
                    buttonNext.addEventListener('mouseleave', () => {
                        buttonNext.classList.remove("johnny");
                        buttonNext.style.width = '60%';
                        buttonNext.style.backgroundColor = '';
                        buttonNext.style.backgroundImage = '';
                    })
            }
            if (this.carrouselIndex === 3) {
                    buttonNext.classList.add("ben");
                    
                    
                    buttonNext.addEventListener('mouseleave', () => {
                        buttonNext.classList.remove("ben");
                        buttonNext.style.width = '60%';
                        buttonNext.style.backgroundColor = '';
                        buttonNext.style.backgroundImage = '';
                    })
            }
            
            
        },
        carrouselPrevious() {

        

        }
    },

    computed: {

    },

    mounted() {}

}
</script>

<style scoped>
#container-card {
    width: 60%;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: center;
    align-items: center;
    align-content: center;
    gap: 200px;
    padding: 30px;
}

#carrousel-div {
    width: 100%;
    background-color: #faf9f9;
    border: 5px rgba(33, 130, 175, 0.658) solid;
    display: flex;
    align-items: center;
    justify-content: space-around;
    gap: 20px;
    padding: 30px;
    border-radius: 30px;
}

.button {
    width: 25%;
    display: flex;
}

#buttonNext {
    width: 60%;
    height: 40px;
    border-radius: 10px;
    cursor: pointer;
    -webkit-text-stroke: 1px #242424;
}

.reed {
    animation-name: reed;
    animation-duration: 4s;
}

@keyframes reed {
    0% {
        width: 40%;
    }

    50% {width: 90%;}

    100% {
        width: 60%;
    }
}

.susan {
    animation-name: susan;
    animation-duration: 6s;
    background: radial-gradient(circle at 0% 100%, rgb(68, 159, 196), transparent);
    color: #faf9f9;
    border: none;
    -webkit-text-stroke: 1px #ffffff;
}

@keyframes susan {
    0% {border-color: rgb(0, 153, 255);}
    50% {border-color: rgb(62, 166, 235);
        background: radial-gradient(circle at 0% 100%, rgb(137, 192, 214), transparent);}
    100% {border-color: none;
        background: radial-gradient(circle at 0% 100%, rgb(253, 253, 253), transparent);}
}

.johnny {
    animation-name: johnny;
    animation-duration: 4s;
    animation-iteration-count: infinite;
    border-color: rgb(255, 187, 0);
    background-position: center;
    background-size: 100%;
    color: white;
    -webkit-text-stroke: 1px #ffffff;
    
}

@keyframes johnny {
    0% {
        background-size: 100%;
        background: radial-gradient(circle, rgba(244,81,0,1) 0%, rgba(255,204,92,0.7287289915966386) 100%);

    }
    25% {background-size: 95%;
        background: radial-gradient(circle, rgba(244,81,0,1) 10%, rgba(255,204,92,0.7287289915966386) 100%);}

    35% {background-size: 95%;
        background: radial-gradient(circle, rgba(244,81,0,1) 0%, rgba(255,204,92,0.7287289915966386) 100%);}

    45% {background-size: 95%;
        background: radial-gradient(circle, rgba(244,81,0,1) 5%, rgba(255,204,92,0.7287289915966386) 100%);}
    

    50% {background-size: 100%;
        background: radial-gradient(circle, rgba(244,81,0,1) 0%, rgba(255,204,92,0.7287289915966386) 100%);}

    
    75% {background-size: 95%;
        background: radial-gradient(circle, rgba(244,81,0,1) 20%, rgba(255,204,92,0.7287289915966386) 100%);}

    100% {background-size: 100%;
        background: radial-gradient(circle, rgba(244,81,0,1) 0%, rgba(255,204,92,0.7287289915966386) 100%);}
}


.ben {
    animation-name: ben;
    animation-duration: 4s;
    animation-play-state: paused 100%;
    background-image: url('https://img.freepik.com/premium-vector/cartoon-game-texture-background-rocks-dirt-ground-surface-seamless-pattern_443949-455.jpg');
    background-position: center;
    background-size: 100%;
    -webkit-text-stroke: 1px #ffffff;
}

@keyframes ben {
    0% {opacity: 10%;
        color: black;
    }
    25% {opacity:  25%;
        color: rgb(53, 52, 52);
    }
    50% {opacity:  50%;
        color: rgb(8, 8, 8);
    }
    75% {opacity:  75%;
        color: rgb(204, 200, 200);
        -webkit-text-stroke: 1px #ffffff;
    }
    100% {opacity: 100%;
        color: rgb(255, 255, 255);
        -webkit-text-stroke: 1px #ffffff;
    }
}

.card {
    width: 30%;
    height: 500px;
    display: flex;
    flex-direction: column;
    justify-content: start;
    perspective: 500px;
    border-radius: 25px;
    cursor: pointer;
}

.content-card {
    width: 100%;
    height: 100%;
    overflow: hidden;
    border-radius: 25px;
    transition: all 0.15s ease-out;
    border: 4px solid;
}

.content-img {
    width: 100%;
    height: 80%;
    object-fit: cover;
    margin: none;
}

.content-title {
    width: 100%;
    height: 30%;
    object-fit: cover;
    background-color: rgb(0, 89, 255);
    color: rgba(250, 235, 215, 0.952);
    -webkit-text-stroke: 1px #fff;
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
    left: 4px;
    width: 100%;
    height: 100%;
    transition: all 0.15s ease-out;
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

    75% {
        left: 65%;
        width: 20%;

    }

    100% {
        left: 20%;
        width: 20%;
    }

}
</style>
