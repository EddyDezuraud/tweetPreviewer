<script setup>
import Tweet from './components/Tweet.vue'
import { inject } from '@vercel/analytics';
inject();
</script>

<template>
  <Tweet/>
  <a class="twitterLink grey" href="https://twitter.com/eddydsn" target="_blank">
    @eddydsn
  </a>
</template>


<style>

.twitterLink {
  position: absolute;
  bottom: 20px;
  font-weight: 800;
  font-size: 13px;
}

</style>