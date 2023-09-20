<script setup>
import TweetHeader from '../components/TweetHeader.vue'
import TweetFooter from '../components/TweetFooter.vue' 
</script>

<template>
    <div :class="$style.wrapper">
        <div :class="$style.left">
            <div :class="$style.avatar">

            </div>
        </div>
        <div :class="$style.content">

            <TweetHeader name="Eddy" badge="" name-id="eddyDsn" date="12m" />

            <div :class="$style.tweetContent" contenteditable="true">
                Write your tweet content here...
            </div>

            <TweetFooter />

        </div>
    </div>
</template>

<style module>
.wrapper {
    padding: 12px 16px;
    width: 598px;
    border: solid 1px #2F3336;
    display: flex;
    gap: 12px;
    text-align: left;
}

.content {
    flex: 1;
}

.avatar {
    width: 40px;
    aspect-ratio: 1;
    border-radius: 50%;
    background: red;
}

.tweetContent:active,
.tweetContent:focus {
    outline: none;
}
</style>