<template>
    <div>
        <div :class=" `modal ${showModal}`">
          <slot></slot>
        </div>
    </div>
</template>

<script>
export default {
    name: 'theCreateUser',
    props: {
      showModal: {
        type: String
      }
    }
}
</script>

<style scoped>

</style>