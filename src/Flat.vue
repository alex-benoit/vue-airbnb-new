<template>
  <div class="flat" v-on:click="handleClick">
    <div class="flat-picture" v-bind:style="{backgroundImage: `url('${imageUrl}')` }"></div>
    <div class="flat-title">{{ `${price} € - ${name}` }}</div>
  </div>
</template>

<script>
  export default {
    methods: {
      handleClick() {
        this.$emit('selectedFlatChanged', this.id)
      }
    },
    props: ['id', 'name', 'price', 'imageUrl']
  }
</script>

<style>
  .flat {
    margin: 10px;
    flex-basis: calc(50% - 20px);
  }

  .flat:hover {
    opacity: 0.8;
    cursor: pointer;
  }
  .flat-picture {
    height: 200px;
    background-size: cover;
    background-position: center;
  }
  .flat-title {
    margin-top: 10px;
    font-weight: bold;
  }
</style>
