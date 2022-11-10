<script>

export default {
    props: {
        winner: {
            type: String,
            default: ""
        },
        premio: {
            type: String,
            default: ""
        }
    },
    data() {
        return {
            countdown: true,
            time: 3
        }
    },
    mounted() {
        setInterval(() => this.setTime(), 1000);
    },
    methods: {
        close() {
            this.$emit('close')
        },
        setTime() {
            if (this.time > 1) {
                this.time--
            } else {
                this.countdown = false
            }
        }
    }
}
</script>

<template>
    <div id="result">

        <div id="close" v-if="!countdown" class="text-center">
            <button class="btn btn-danger" @click="close()">
                <em class="fa fa-times"></em>
            </button>
        </div>

        <div v-if="countdown">

            <h2 class="loader-text"> {{ time }} </h2>
            <div class="loader" id="loader">
            </div>
        </div>
        <div v-else class="text-center winannounce">
            <h1 class="data">El/La Ganador/a es</h1>
            <h1>{{ winner }}</h1>
            <h1 class="data">y se lleva</h1>
            <h1 class="premio">{{ premio }}</h1>
        </div>

    </div>
</template>

<style scoped>
#result {
    position: fixed;
    top: 20px;
    left: 20px;
    bottom: 20px;
    right: 20px;
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(5px);
    border-radius: var(--border-radius);
    padding: 70px;
}

#close {
    position: fixed;
    top: 30px;
    right: 30px;
}

.btn-danger {
    border-radius: var(--border-radius);
}

body {
    overflow: hidden !important;
}

.winannounce{
    padding-top: 100px;
}

.winannounce h1{
    font-size: 150px;
}

.winannounce .data{
    font-size: 70px;
    color: white !important;
}
.winannounce .premio{
    font-size: 100px;
}

.loader {
    font-size: 10px;
    margin: calc(50vh - 150px) auto;
    text-indent: -9999em;
    width: 11em;
    height: 11em;
    border-radius: 50%;
    background: #ffffff;
    background: -moz-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -webkit-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -o-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: -ms-linear-gradient(left, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    background: linear-gradient(to right, #ffffff 10%, rgba(255, 255, 255, 0) 42%);
    position: relative;
    -webkit-animation: load3 1.4s infinite linear;
    animation: load3 1.4s infinite linear;
}

.loader-text {
    font-size: 70px;
    font-weight: bold;
    color: #ffffff;
    text-align: center;
    position: fixed;
    left: calc(50% - 20px);
    z-index: 999;
    margin-top: 12px;
}

.loader:before {
    width: 50%;
    height: 50%;
    background: #FFF;
    border-radius: 100% 0 0 0;
    position: absolute;
    top: 0;
    left: 0;
    content: '';
}

.loader:after {
    background: var(--accent-color);
    width: 75%;
    height: 75%;
    border-radius: 50%;
    margin: auto;
    position: absolute;
    content: '';
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
}

@-webkit-keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }

    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}

@keyframes load3 {
    0% {
        -webkit-transform: rotate(0deg);
        transform: rotate(0deg);
    }

    100% {
        -webkit-transform: rotate(360deg);
        transform: rotate(360deg);
    }
}
</style>