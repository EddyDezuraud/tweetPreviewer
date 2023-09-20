<script setup>

import IconComment from '../components/Icons/Comment.vue'
import IconRetweet from '../components/Icons/Retweet.vue'
import IconLike from '../components/Icons/Like.vue'
import IconStats from '../components/Icons/Stats.vue'
import IconDownload from '../components/Icons/Download.vue'

</script>

<template>
    <footer :class="$style.wrapper" class="grey">
        <div :class="$style.el">
            <IconComment />
            <span>2</span>
        </div>

        <div :class="$style.el">
            <IconRetweet />
            <span>2</span>
        </div>

        <div :class="$style.el">
            <IconLike />
            <span>2</span>
        </div>

        <div :class="$style.el">
            <IconStats />
            <span>2</span>
        </div>

        <div :class="$style.el">
            <IconDownload />
        </div>

    </footer>
</template>

<style module>
.wrapper {
    display: flex;
    align-items: center;
    justify-content: space-between;
    width: 100%;
    margin-top: 12px;
}

.el {
    display: flex;
    gap: 12px;
    font-size: 13px;
}

.el svg {
    width: 18.75px;
    fill: currentColor;
}
</style>