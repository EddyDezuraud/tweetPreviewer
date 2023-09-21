<template>
    <header :class="$style.wrapper">
        <span>
            <strong contenteditable="true">{{ name }}</strong>
        </span>
        <span v-if="badge">
            {{ badge }}
        </span>
        <span class="grey">
            @<span contenteditable="true">
                {{ nameId }}
            </span>
        </span>
        <span v-if="date" class="grey">·</span>
        <span v-if="date" class="grey">
            {{ date }}
        </span>
    </header>
</template>

<script setup>
defineProps(['name', 'badge', 'nameId', 'date'])
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