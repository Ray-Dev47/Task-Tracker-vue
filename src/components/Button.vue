<template>
  <button v-on:click="onClick()" v-bind:style="{ background: color }" class="btn">{{ text }}</button>
  <!-- props consumption -->
</template>



 
<script>
export default {
  name: "Button",
  props: {
    text: String,
    color: String,
  },
  // ladding a method to our btn event
  methods: {
      onClick() {
          this.$emit('btn-click')
    }
}
};
</script>
