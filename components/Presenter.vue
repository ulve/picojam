<template>
    <div>
        <h1>{{themeTitle}}</h1>
        <h2>{{themeValue}}</h2>
        <button @click="$emit('presented')">Titta</button>
    </div>
</template>

<script>
export default {
    props: ['value', 'title'],
    data: function() {
        return {
            themeTitle: this.title,
            themeValue: this.value
        }
    }
}
</script>
