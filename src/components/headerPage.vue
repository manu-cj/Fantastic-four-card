<template>
    <header>
        <div id="title-div">
            <h1>Fantastic </h1><img src="https://upload.wikimedia.org/wikipedia/commons/c/cd/Fantastic_Four_logo_%28blue_and_white%29.svg" width="15%"/>
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
    width: 100%;
    height: 300px;
    display: flex;
    flex-direction: column;
    align-items: center;
}

#title-div {
    width: 50%;
    display: flex;
    align-items: center;
    justify-content: center;
    align-content: space-between;
    gap: 20px;
    flex-direction: row;
    -webkit-text-stroke: 2px #73aed4;
    color: rgb(107, 163, 236);
    font-size: 50px;
}

#title-div img {
    filter : opacity(60%);
    animation-name: flip;
    animation-duration: 8s;
    animation-delay: 5s;
    animation-iteration-count: infinite;
}

@keyframes flip {
    0% {
        transform : rotateY(0deg);
    }

    60% {
        transform : rotateY(0deg);
    }
    100% {
        transform: rotateY(360deg);
    }
}

</style>