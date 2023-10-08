<script setup>
import { defineProps, onMounted, watch, ref } from 'vue';

import TweetHeader from '../components/TweetHeader.vue'
import TweetFooter from '../components/TweetFooter.vue'

const props = defineProps({
    username: {
        type: String,
        default: ''
    }
})

const loadingApiData = ref(false);

const handlePaste = (event) => {
    event.preventDefault(); // Empêcher le comportement par défaut de la coller
    const clipboardData = event.clipboardData || window.clipboardData;
    const text = clipboardData.getData('text/plain'); // Obtenir le texte brut du clipboard
    document.execCommand('inserttext', false, text); // Insérer le texte brut sans le HTML
};

const getRandomHexColor = () => {
    // Generate random values for red, green, and blue components
    const red = Math.floor(Math.random() * 256);
    const green = Math.floor(Math.random() * 256);
    const blue = Math.floor(Math.random() * 256);

    // Convert the values to hex and format as a color code
    const hexColor = `#${red.toString(16)}${green.toString(16)}${blue.toString(16)}`;

    return hexColor;
};

const fetchData = async () => {
    loadingApiData.value = true;

    try {

        const res = await fetch('https://twitter-crawler.onrender.com/checkTwitterId/' + props.username);
        console.log(res);

    } catch (e) {

        console.error(e);

    } finally {
        loadingApiData.value = false;
    }
}

watch(() => props.username, (newValue) => {
    fetchData();
});

onMounted(() => {
    fetchData();
})
</script>

<template>
    <div :class="$style.wrapper">

        <div :class="$style.left">
            <div :class="$style.avatar" :style="{ background: getRandomHexColor() }"></div>
        </div>
        <div :class="$style.content">

            <TweetHeader name="" badge="" :name-id="username" date="12m" />

            <div class="editableElt" contenteditable="true" spellcheck="false" @paste="handlePaste">
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
    position: relative;
}

.avatar::before {
    position: absolute;
    content: '';
    width: 100%;
    height: 100%;
    border-radius: 50%;
    background: linear-gradient(45deg, rgba(255, 255, 255, 0.04), rgba(255, 255, 255, 0.1))
}
</style>