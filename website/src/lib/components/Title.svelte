<script>
    import { onMount } from "svelte";

    export let initialText = 'David "Glitchez" Safro'; // Customizable initial text
    let visibleText = "";
    let animationDelay = 100; // Adjust this for animation speed
    let isBackspacing = false;
    let currentIndex = 0;
    export let textList = ["I am David Safro", "I enjoy programming and applied math", "subscribe to my only fans"];

    onMount(() => {
        animateText();
    });

    async function animateText() {
        while (true) {
            for (let i = 0; i < initialText.length; i++) {
                visibleText = initialText.slice(0, i + 1);
                await sleep(animationDelay);
            }
            await sleep(1000); // Pause before backspacing

            isBackspacing = true;
            for (let i = initialText.length - 1; i >= 0; i--) {
                visibleText = initialText.slice(0, i);
                await sleep(animationDelay);
            }
            isBackspacing = false;

            currentIndex = (currentIndex + 1) % textList.length;
            initialText = textList[currentIndex];
        }
    }

    async function sleep(ms) {
        return new Promise(resolve => setTimeout(resolve, ms));
    }
</script>

<style>
    .glow-text {
        font-size: 3rem;
        font-weight: bold;
        background: linear-gradient(135deg, #7efff5, #00b3ff);
        -webkit-background-clip: text;
        -webkit-text-fill-color: transparent;
        animation: glow 2s ease-in-out infinite;
    }

    .blinking-cursor {
        animation: blink 1s step-start infinite;
    }

    @keyframes glow {
        0%, 100% {
            text-shadow: 0 0 10px #7efff5, 0 0 20px #7efff5, 0 0 30px #7efff5;
        }
        50% {
            text-shadow: 0 0 20px #7efff5, 0 0 30px #7efff5, 0 0 40px #7efff5;
        }
    }

    @keyframes blink {
        0%, 100% {
            opacity: 1;
        }
        50% {
            opacity: 0;
        }
    }
</style>

<div class="glow-text">{visibleText}<span class="blinking-cursor">|</span></div>
