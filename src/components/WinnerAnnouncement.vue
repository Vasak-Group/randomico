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
            time: 5
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
            if (this.time > 0) {
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
            <h1>{{ time }}</h1>
        </div>
        <div v-else>
            <h1>El Ganador es</h1>
            <h1>{{ winner }}</h1>
            <h2>y se lleva</h2>
            <h2>{{ premio }}</h2>
        </div>

    </div>
</template>

<style scoped>
#result {
    position: relative;
    top: 20px;
    left: 20px;
    bottom: 20px;
    right: 20px;
    background: rgba(0, 0, 0, 0.5);
    backdrop-filter: blur(5px);
    border-radius: var(--border-radius);
}

#close {
    position: fixed;
    top: 30px;
    right: 30px;
    padding: 70px;
}

.btn-danger{
    border-radius: var(--border-radius);
}

body {
    overflow: hidden !important;
}
</style>