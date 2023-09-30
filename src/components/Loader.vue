<script setup>
import { onMounted } from "vue";

const emits = defineEmits("end");

onMounted(() => {
    setTimeout(() => {
        emits('end');
    }, 4000);
});
</script>

<template>
    <div :class="$style.wrapper">
        <div :class="$style.svg">
            <div :class="$style.innerSvg">
                <svg :class="$style.left" width="54" height="90" viewBox="0 0 54 90" fill="none"
                    xmlns="http://www.w3.org/2000/svg">
                    <path d="M17.5 90H2L38 49.5L0 0H31.5L53.5 28.5L47 34.5L27.5 9H18L51 52C39.6667 64.6667 17.1 90 17.5 90Z"
                        fill="white" />
                </svg>
                <svg :class="$style.right" width="56" height="90" viewBox="0 0 56 90" fill="none"
                    xmlns="http://www.w3.org/2000/svg">
                    <path d="M33.5 0H53.5L17.5 40.5L55.5 90H24L0 58.5L6 52L28 81H37.5L2 34.5C13.3333 21.8333 33.5 0 33.5 0Z"
                        fill="white" />
                </svg>
            </div>
        </div>
        <div :class="$style.title">
            <span>
                X
            </span>
            <span>
                Post
            </span>
            <span>
                Preview
            </span>
        </div>
    </div>
</template>

<style module>
.wrapper {
    animation: hideLoader 1.3s ease;
    animation-delay: 2.7s;
    animation-fill-mode: forwards;
    height: 100vh;
    width: 100vw;
    position: absolute;
    left: 0;
    top: 0;
}


.title,
.svg {
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    left: 0;
    width: 100%;
    display: flex;
    justify-content: center;
}

.innerSvg {
    display: flex;
    justify-content: center;
    animation: svgAnim 1s ease;
    animation-fill-mode: both;
}

.svg {
    gap: -10px;
}

.left {
    transform: translateX(5px);
    animation: leftAnim 1.5s ease;
    animation-delay: 1s;
    animation-fill-mode: both;
}

.right {
    transform: translateX(-5px);
    animation: rightAnim 1.5s ease;
    animation-delay: 1s;
    animation-fill-mode: both;
}

@keyframes svgAnim {
    0% {
        opacity: 0;
        transform: scale(0.8);
    }

    50% {
        transform: scale(1.1);
    }

    100% {
        opacity: 1;
        transform: scale(1);
    }

}

@keyframes leftAnim {
    0% {
        transform: translateX(5px);
    }

    100% {
        transform: translateX(-130px) scale(0.6);
    }
}

@keyframes rightAnim {
    0% {
        transform: translateX(-5px);
    }

    100% {
        transform: translateX(130px) scale(0.6);
    }
}

.title {
    font-size: 32px;
    font-weight: 700;
    color: white;
    text-align: center;
    gap: 10px;
    font-weight: 900;
}

.title>* {
    animation: textAnim 0.8s ease;
    animation-delay: 1.5s;
    animation-fill-mode: both;
}

.title>*:nth-child(1) {
    animation-delay: 1.5s;
}

.title>*:nth-child(2) {
    animation-delay: 1.55s;
}

.title>*:nth-child(3) {
    animation-delay: 1.6s;
}

@keyframes textAnim {
    0% {
        opacity: 0;
        text-shadow: 0px -15px 0px #08ff31, 0px -10px 0px #08a4ff, 0px -5px 0px #7125ff;
        transform: translateY(30px);
    }

    100% {
        opacity: 1;
        text-shadow: 0px 0px 0px #08ff3100, 0px -px 0px #7125ff00, 0px 0px 0px #08a4ff00;
        transform: translateY(0);
    }
}

@keyframes hideLoader {
    0% {
        opacity: 1;
        transform: translateY(0);
    }

    100% {
        opacity: 0;
        transform: translateY(-30px);
    }
}
</style>