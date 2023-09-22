<script setup>
import Tweet from './components/Tweet.vue'
import { inject } from '@vercel/analytics';
inject();
</script>

<template>
  <div class="appWrapper">
    <div id="titlePage">
      <h1>X Post Preview</h1>
      <span class="grey">v0.0.1</span>
    </div>
    <Tweet />
    <a class="twitterLink grey" href="https://twitter.com/eddydsn" target="_blank">
      Build by @eddydsn
    </a>
  </div>
</template>


<style>

.appWrapper {
  display: flex;
  height: 100vh;
  justify-content: space-between;
  flex-direction: column;
  min-height: 100vh;
  padding: 20px;
  box-sizing: border-box;
  gap: 20px;
}

#titlePage {
  text-align: center;
  width: 100%;
  left: 0;
  display: flex;
  justify-content: center;
  align-items: baseline;
  gap: 10px;
}

#titlePage h1 {
  margin: 0;
  padding: 0;
  font-size: 20px;
  line-height: 1;
}

#titlePage>span {
  line-height: 1;
  font-size: 12px;
  font-weight: 700;
}

.twitterLink {
  font-weight: 800;
  font-size: 13px;
}
</style>