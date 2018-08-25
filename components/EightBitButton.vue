<template>
<section>
    <a href="javascript:void(0)" class="eightbit-btn" @click="$emit('clicked')">{{ buttonText }}</a>
</section>
</template>

<script>
export default {
    props: ['title'],
    data: function() {
        return {
            buttonText: this.title
        }
    }
}
</script>

<style scoped>
.eightbit-btn {
    background: #92CD41;
    display: inline-block;
    position: relative;
    text-align: center;
    font-size: 30px;
    padding: 20px;
    font-family: 'Press Start 2P', cursive;
    text-decoration: none; 
    color: white;
    box-shadow: inset (-4px) (-4px) 0px 0px #4AA52E;
    width: 150px;
}
.eightbit-btn:hover,
.eightbit-btn:focus {
    background: #A2dd51;
    box-shadow: inset (-6px) (-6px) 0px 0px #4AA52E;
}

.eightbit-btn:active {
    background: #92CD41;
    box-shadow: inset 4px 4px 0px 0px #3A951E;
}

.eightbit-btn:before,
.eightbit-btn:after {
    content: '';
    position: absolute;
    width: 100%;
    height: 100%;
    box-sizing: content-box;
}

.eightbit-btn:before {
    top: -6px;
    left: 0;
    border-top: 6px black solid;
    border-bottom: 6px black solid;
}

.eightbit-btn:after {
    left: -6px;
    top: 0;
    border-left: 6px black solid;
    border-right: 6px black solid;
}
</style>