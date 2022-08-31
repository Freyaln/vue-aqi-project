<template>
  <div>
    <button v-for="(value, index) in values" :key="index" >
      <p>{{value}}</p>
    </button>
  </div>
</template>

<script>
export default {
  name: 'button',
  props: {
    values: {
      type: Array,
      required: true,
    },
    action: {
      type: Function,
      required: false
    },
  },
}

</script>

<script setup>
const props = defineProps({
  values: {
    type: Array,
    required: true
  },
  action: {
    type: Function,
    required: false
  },
})


</script>

<style lang="scss">

</style>