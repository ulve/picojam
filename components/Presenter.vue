<template>
<section class="section-8-bit">
    <div class="wrapper" :style="{ 'background-color': themeColor }">
        <div class="not-presented" v-if="!presented">
            <h1 class="title">{{themeTitle}}</h1>          
            <button @click="onPresent">Titta</button>
        </div>
        <div class="presented" v-if="presented">
            <h1 class="title">{{themeTitle}}</h1>
            <h2 class="value">{{themeValue}}</h2>
        </div>
    </div>
</section>
    
</template>

<script>
export default {
    props: ['value', 'title', 'color'],
    data: function() {
        return {
            themeTitle: this.title,
            themeValue: this.value,
            themeColor: this.color,
            presented: false
        }
    },
    methods: {
        onPresent: function() {
            this.presented = true;
            this.$emit('presented')
        }
    }
}
</script>

<style scoped>
    .not-presented .title {
        font-family: 'Press Start 2P', cursive;
        font-size: 42px;
    }

    .presented .title {
        font-family: 'Press Start 2P', cursive;
        font-size: 32px;
    }

    .value {
        font-family: 'Press Start 2P', cursive;
        size: 20px;
    }

    .section-8-bit {
        width: 100%; 
        float: left; 
        border-left: 10px solid #FF6600;
        border-right: 10px solid #FF6600;
        position: relative; 
        -webkit-box-sizing: border-box; 
        -moz-box-sizing: border-box; 
    	box-sizing: border-box;
        margin-bottom: 50px;
    }

    .section-8-bit .wrapper {
        display: block;
        color: #FF6600;
        padding: 40px; 
        margin: -10px 0; 
        border-top: 10px solid #FF6600; 
        border-bottom: 10px solid #FF6600; 
        height: 200px;
    }

	.section_8bit::before, 
	.section_8bit::after,
	.section_8bit .wrapper::before, 
	.section_8bit .wrapper::after{ 
        content: ''; 
        width: 10px; 
        height: 10px; 
        display: block; 
        position: absolute;   
        background: #FF6600; 
	}
	.section_8bit::before{ top: -5px; left: -5px; }
	.section_8bit::after{ top: -5px; right: -5px; }
	.section_8bit .wrapper::before{ bottom: -5px; left: -5px; }
	.section_8bit .wrapper::after{ bottom: -5px; right: -5px; }

    .not-presented {
        width: 100%;
        height: 200px;
    }
</style>
