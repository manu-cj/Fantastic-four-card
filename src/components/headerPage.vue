<template>
    <header>
        
        <div id="title-div">
            <p>Fantastic</p>
            <img src="https://upload.wikimedia.org/wikipedia/commons/c/cd/Fantastic_Four_logo_%28blue_and_white%29.svg" width="13%"/>
        </div>
    </header>
</template>

<script>
    export default {
        data() {
            return {

            }
        }
    }
</script>

<style scoped>
header {
    margin: 50px;
    width: 100%;
    height: 100px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#title-div {
    width: 40%;
    background-color: transparent;
    display: flex;
    align-items: center;
    justify-content: center;
    align-content: space-between;
    gap: 20px;
    flex-direction: row;
    -webkit-text-stroke: 2px #fbfdff;
    color: rgb(62, 130, 231);
    font-size: 50px;
    border-radius: 50px;
    background-color: #faf9f969;
    border: 5px rgba(33, 130, 175, 0.658) solid;
}

#title-div img {
    filter : opacity(80%);
    border-radius: 100%;
    border: 3px white solid;
    background-color: rgb(254, 254, 255);
    background-repeat: no-repeat;
    background-size: 80%;
    animation: flip 8s infinite;
    background-clip: content-box;
}

@keyframes flip {
    0% {
        background-position: -500%;
        transform : rotateY(0deg);
    }

    60% {
        transform : rotateY(0deg);
    }
    
    100% {
        background-position: 500%;
        transform: rotateY(360deg);
    }
}

p {
    position: relative;
    font-family: Impact, sans-serif;
    font-size: 90px;
    letter-spacing: 2px;
    background: linear-gradient(-45deg, rgba(244,247,247,1) 0%, rgb(48, 110, 192) 18%);
    background-repeat: no-repeat;
    background-size: 80%;
    animation: reflect 8s infinite;
    background-clip: text;
    -webkit-text-fill-color: rgba(255, 255, 255, 0);
  }
  @keyframes reflect {
    0% {
        
      background-position: -500%;
    }
    100% {
      background-position: 500%;
    }
  }

</style>