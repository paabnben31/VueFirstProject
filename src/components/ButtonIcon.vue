<template>
    <div>
        <button @click="sendText" type="button" class="btn btn-info">
            <span :class="icon"></span> {{ name }}
        </button>
    </div>
</template>

<script>
    export default {
        props:{
            icon:{
                type: String,
                default: 'fa fa-search'
            },
            name:{
                type: String,
                default: 'Search'
            }
        },
        methods: {
            sendText() {
                this.$emit('buttonText',20)
            }
        },
    }
</script>

<style scoped>
</style>