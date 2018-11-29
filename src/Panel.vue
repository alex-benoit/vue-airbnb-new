<template>
  <div class="panel" v-if="id">
    <div class="flat-info">
      <h3>{{ name }}</h3>
      <p>{{ price }} € per night</p>
      <button>Book now</button>
    </div>
    <div class="flat-banner" v-bind:style="{ backgroundImage: `url(${imageUrl})` }"></div>
  </div>
</template>

<script>
  export default {
    props: ['id', 'name', 'price', 'imageUrl']
  }
</script>

<style>
  .panel {
    margin: 10px;
    background-color: #eee;
    border-radius: 2px;
    padding: 10px;
  }
  .flat-banner {
    height: 250px;
    background-size: cover;
    background-position: center;
    margin-bottom: 15px;
  }
  .flat-info {
    padding: 10px;
    background-color: #ddd;
    margin-bottom: 15px;
  }
  .flat-info button {
    color: white;
    padding: 8px;
    font-size: 18px;
    cursor: pointer;
    background-color: #FD5C63;
    width: 100%;
  }
</style>
