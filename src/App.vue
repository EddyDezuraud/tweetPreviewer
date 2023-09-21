<script setup>
import Tweet from './components/Tweet.vue'
import { inject } from '@vercel/analytics';
inject();
</script>

<template>
  <Tweet/>
</template>