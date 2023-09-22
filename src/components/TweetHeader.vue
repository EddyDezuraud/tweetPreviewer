<template>
    <header :class="$style.wrapper">
        <span>
            <strong class="editableElt" contenteditable="true" spellcheck="false" ref="editedNameRef" @input="handleInput('editedName')"
                @paste="handlePaste($event, 'editedName')">{{ editedName }}</strong>
        </span>
        <span v-if="badge">
            {{ badge }}
        </span>
        <span class="grey">
            @<span class="editableElt" contenteditable="true" spellcheck="false" @input="handleInput('editedNameId')"
                @paste="handlePaste($event, 'editedNameId')" ref="editedNameIdRef">
                {{ editedNameId }}
            </span>
        </span>
        <span v-if="date" class="grey">·</span>
        <span v-if="date" class="grey">
            {{ date }}
        </span>
    </header>
</template>

<script setup>
import { ref } from 'vue';

const editedName = ref('Your Name');
const editedNameId = ref('yourNameId');
const badge = null;
const date = '12m';

const editedNameRef = ref(null);
const editedNameIdRef = ref(null);

const handleInput = (field) => {
    const range = window.getSelection().getRangeAt(0);
    const startOffset = range.startOffset > 25 ? 25 : range.startOffset;
    const endOffset = range.endOffset > 25 ? 25 : range.endOffset;

    if (field === 'editedName') {
        if (editedNameRef.value.textContent.length > 25) {
            // Annuler la saisie de la dernière lettre
            editedNameRef.value.textContent = editedNameRef.value.textContent.substring(0, 25);
        }
        editedName.value = editedNameRef.value.textContent;

        range.setStart(editedNameRef.value.firstChild, startOffset);
        range.setEnd(editedNameRef.value.firstChild, endOffset);
    } else if (field === 'editedNameId') {
        if (editedNameIdRef.value.textContent.length > 25) {
            // Annuler la saisie de la dernière lettre
            editedNameIdRef.value.textContent = editedNameIdRef.value.textContent.substring(0, 25);
        }
        const newValue = editedNameIdRef.value.textContent.replace(/\s+/g, '_');
        editedNameId.value = newValue;
        editedNameIdRef.value.textContent = newValue;

        // Annuler la saisie de la dernière lettre
        editedNameIdRef.value.textContent = editedNameIdRef.value.textContent.substring(0, 25);
        range.setStart(editedNameIdRef.value.firstChild, startOffset);
        range.setEnd(editedNameIdRef.value.firstChild, endOffset);
    }

    // Rétablir la position du curseur


    window.getSelection().removeAllRanges();
    window.getSelection().addRange(range);
};

const handlePaste = (event, field) => {
    event.preventDefault();
    const text = event.clipboardData.getData('text/plain');
    document.execCommand('insertText', false, text);
    handleInput(field);
};
</script>

<style module>
.wrapper {
    display: flex;
    gap: 4px;
    font-size: 15px;
}

.wrapper * {
    outline: none;
}
</style>