<script setup>
import TweetHeader from '../components/TweetHeader.vue'
import TweetFooter from '../components/TweetFooter.vue'


const handlePaste = (event) => {
    event.preventDefault(); // Empêcher le comportement par défaut de la coller
    const clipboardData = event.clipboardData || window.clipboardData;
    const text = clipboardData.getData('text/plain'); // Obtenir le texte brut du clipboard
    document.execCommand('inserttext', false, text); // Insérer le texte brut sans le HTML
};
</script>

<template>
    <div :class="$style.wrapper">
        <div :class="$style.left">
            <div :class="$style.avatar">

            </div>
        </div>
        <div :class="$style.content">

            <TweetHeader name="Name" badge="" name-id="username" date="12m" />

            <div class="editableElt" contenteditable="true" @paste="handlePaste">
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
</style>