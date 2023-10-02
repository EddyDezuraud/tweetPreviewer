<script setup>

import { ref, defineEmits } from 'vue';

const username = ref('');
const error = ref(false);

const emits = defineEmits('valid')

const validateUsername = () => {
    // Vérifier la longueur du username
    if (username.value.length > 25) {
        return false;
    }

    // Vérifier s'il y a des espaces
    if (username.value.includes(' ')) {
        return false;
    }

    return true;
};


const onSubmit = () => {

    if (!validateUsername()) {
        error.value = true;
        return;
    }

    emits('valid', { username: username.value })

    console.log('submited');
}
</script>

<template>
    <form :class="$style.wrapper" @submit.prevent="onSubmit">
        <label :class="$style.label" for="usernameInput">What is your X username ?</label>
        <div :class="$style.inputWrapper">
            <div :class="$style.inputPrefix">
                <span>@</span>
            </div>
            <input :class="$style.input" id="usernameInput" type="text" placeholder="username" maxlength="25">
            <span :class="$style.error" v-if="error">Please enter valid username</span>
        </div>
        <button :class="$style.btn" type="submit">
            Validate
        </button>
    </form>
</template>


<style module>
.wrapper {
    display: flex;
    flex-direction: column;
    height: calc(100vh - 40px);
    justify-content: center;
    align-content: flex-start;
    width: 100%;
    width: 800px;
    margin: 0 auto;
}

.label {
    text-align: left;
    font-size: 2.4rem;
    display: block;
    margin-bottom: 20px;
}

.inputWrapper {
    position: relative;
    margin-bottom: 80px;
}

.inputPrefix {
    position: absolute;
    left: 24px;
    height: 100%;
    display: flex;
    align-items: center;
    justify-content: center;
    font-size: 24px;
}

.input {
    width: 100%;
    padding: 16px 24px 16px 50px;
    border-radius: 8px;
    background: linear-gradient(180deg, rgba(255, 255, 255, .1), rgba(255, 255, 255, .08));
    border: solid 0px rgba(255, 255, 255, .1);
    font-size: 24px;
    outline: none;
}

.btn {
    align-self: flex-end;
    background: white;
    color: black;
    margin: 0;
    font-weight: 600;
    padding: 12px 36px;
    border-radius: 8px;
}


/* ANIMATIONS */
.btn,
.label,
.inputWrapper {
    animation: itemOpening 0.7s ease;
    animation-fill-mode: both;
}

.inputWrapper {
    animation-delay: 0.3s;
}

.btn {
    animation-delay: 0.6s;
}

.error {
    color: red;
}


@keyframes itemOpening {
    0% {
        opacity: 0;
        transform: translateY(30px);
    }

    100% {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>