<script>
    let isHovered = false; // Tracks if the component is hovered
</script>

<style>
    .bio-paragraph {
        padding: 1rem;
        border-radius: 1rem;
        background: linear-gradient(to right, #00b4db, #0083b0);
        color: white;
        transition: transform 0.3s, background 0.3s;
        cursor: pointer;
    }

    .bio-paragraph:hover {
        transform: scale(1.05);
        background: linear-gradient(to right, #a8e063, #56ab2f);
    }

    .animated-line {
        position: relative;
        display: block;
        width: 100%;
        height: 1px;
        background: linear-gradient(to right, #00b4db, #0083b0);
        opacity: 0;
        transition: opacity 0.3s;
    }

    .bio-paragraph:hover .animated-line {
        opacity: 1;
    }
</style>

<div
        class="bio-paragraph"
        on:mouseenter={() => isHovered = true}
        on:mouseleave={() => isHovered = false}
>
    <p>
        This is a futuristic bio paragraph component. Hover over me to see the animation!
    </p>
    {#if isHovered}
        <span class="animated-line"></span>
    {/if}
</div>
