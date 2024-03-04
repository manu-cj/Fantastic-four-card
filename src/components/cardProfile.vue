<template>

<div id="carrousel-content">
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
    
            <div class="glow" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fourFantastic[carrouselIndex].color +', transparent)'}" @mousemove="cardAnime(fourFantastic[carrouselIndex].color), glowAnime(fourFantastic[carrouselIndex].color), moveOut(fourFantastic[carrouselIndex].color)">
            </div>
    
        </div>
    
        <div class="button" style="justify-content: end;">
    
            <button id="buttonNext" v-if="carrouselIndex < fourFantastic.length - 1" @mouseover="carrouselNext()" @click="carrouselIndex++">Next</button>
            <div class="border-anim"></div>
        </div>
    
    </div>
    <div id="container-card">
        <div class="card" v-for="fantastic in fourFantastic" :key="fantastic">
            <div class="content-card" :style="{borderColor: fantastic.color}">
                <img class="content-img" :src="fantastic.image" alt="bachelor" width="100%" height="100%" />
                <div class="glow-title" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fantastic.color +', transparent)'}"></div>
                <div class="content-title">
                    <h2 :style="{color : fantastic.color}">{{ fantastic.name }} </h2>
                </div>
            </div>
    
            <div class="glow" :style="{background : 'radial-gradient(circle at 50% 0%,'+ fantastic.color +', transparent)'}" @mousemove="cardAnime(fantastic.color), glowAnime(fantastic.color), moveOut(fantastic.color)">
            </div>
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

                buttonNext.addEventListener('mouseleave', () => {
                    buttonNext.classList.remove("reed");
                    buttonNext.style.backgroundColor = '';
                    buttonNext.style.backgroundImage = '';
                })
            }
            if (this.carrouselIndex === 1) {
                buttonNext.classList.add("susan");

                buttonNext.addEventListener('mouseleave', () => {
                    buttonNext.classList.remove("susan");
                    buttonNext.style.backgroundColor = '';
                    buttonNext.style.backgroundImage = '';
                })
            }
            if (this.carrouselIndex === 2) {
                buttonNext.classList.add("johnny");

                buttonNext.addEventListener('mouseleave', () => {
                    buttonNext.classList.remove("johnny");
                    buttonNext.style.backgroundColor = '';
                    buttonNext.style.backgroundImage = '';
                })
            }
            if (this.carrouselIndex === 3) {
                buttonNext.classList.add("ben");

                buttonNext.addEventListener('mouseleave', () => {
                    buttonNext.classList.remove("ben");
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

#carrousel-content {
    width: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
}

#carrousel-div {
    width: 60%;
    height: 500px;
    background-color: #faf9f969;
    border: 5px rgba(33, 130, 175, 0.658) solid;
    display: flex;
    align-items: center;
    justify-content: space-around;
    gap: 20px;
    padding: 30px;
    border-radius: 30px;
}

.button {
    width: 10%;
    height: 40px;
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: center;
    transition: 0.3s;
    animation: rotateBorderButton 4s linear infinite;
    overflow: hidden;
    position: relative;
    background-color: #fff;
    border-radius: 10px;

}

@property --a {
    syntax: '<angle>';
    inherits: false;
    initial-value: 0deg;
}

@keyframes rotateBorderButton {
    0% {
        --a: 0deg
    }

    100% {
        --a: 360deg
    }

}

.reed {
    animation-name: reed;
    animation-duration: 8s;
    animation-iteration-count: infinite;
    background: repeating-conic-gradient(from var(--a), #0aedf5 0%, #27bbff 5%, transparent 5%, transparent 40%, #27f8ff 50%);
    border: none;
}

@keyframes reed {
    0% {
        border: 2px rgba(0, 0, 255, 0) solid;
        --a: 0deg
    }

    25% {
        border: 2px rgba(0, 0, 255, 0) solid;
    }

    50% {
        border: 2px rgba(0, 0, 255, 0) solid;
    }

    75% {
        border: 2px rgba(0, 0, 255, 0) solid;
    }

    100% {
        border: 2px rgba(0, 0, 255, 0) solid;
        --a: 360deg
    }
}

.susan {
    animation-name: susan;
    animation-duration: 8s;
    animation-iteration-count: infinite;
    background: rgba(0, 174, 255, 0.404);
    border: none;
    box-shadow: 8px 8px 8px 18px rgba(3, 153, 223, 0.88);
}

@keyframes susan {
    0% {

        border: 2px rgba(0, 0, 255, 0.025) solid;
        --a: 0deg
    }

    25% {
        border: 2px rgba(0, 0, 255, 0.125) solid;
    }

    50% {
        border: 2px rgba(0, 0, 255, 0.325) solid;

        --a: -180deg
    }

    75% {
        border: 2px rgba(0, 0, 255, 0.425) solid;
        opacity: 20%;
    }

    100% {
        border: 2px rgba(0, 0, 255, 0.525) solid;
        --a: 180deg
    }
}

#buttonNext {
    width: 100%;
    height: 97%;
    border-radius: 10px;
    cursor: pointer;
    -webkit-text-stroke: 1px #242424;
    z-index: 1;
    border: none;
}


#container-card {
    background-color: #faf9f969;
    border: 5px rgba(33, 130, 175, 0.658) solid;
    width: 60%;
    height: 350px;
    display: flex;
    flex-direction: row;
    flex-wrap: wrap;
    justify-content: space-around;
    align-items: center;
    align-content: center;
    gap: 50px;
    padding: 30px;
    border-radius: 30px;
}

#container-card .card {
    width: 15%;
    height: 300px;
    font-size: smaller;
}

.card {
    width: 25%;
    height: 80%;
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

#container-card .card .glow-title {
    top: 96%;
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
