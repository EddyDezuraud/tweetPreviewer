<script setup>
</script>

<template>
    <div :class="$style.wrapper">
        <label :class="$style.label" for="usernameInput">What is you X username ?</label>
        <div :class="$style.inputWrapper">
            <div :class="$style.inputPrefix">
                <span>@</span>
            </div>
            <input :class="$style.input" id="usernameInput" type="text" placeholder="username">
        </div>
    </div>
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
</style>