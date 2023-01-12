<template>
    <div>
        <div :class=" `modal ${showModal}`">
            <slot></slot>    
        </div>
    </div>
</template>

<script>
export default {
    name: 'theModal',
    props: {
        dadosUser: {
            type: Object
        },
        showModal: {
            type: String
        }
    },
}
</script>

<style scoped>
</style>