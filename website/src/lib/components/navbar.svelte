<script>
    let isHovered = -1;

    const navButtons = [
        { text: 'Projects', link: '#' },
        { text: 'Contact', link: '#' },
        { text: 'Blog', link: '#' },
    ];
</script>

<style>
    .navbar {
        display: flex;
        justify-content: space-between;
        align-items: center;
        padding: 0.5rem; /* Adjusted padding */
        background: linear-gradient(to right, #0e153a, #515c9b);
        border-image-slice: 1;
        border-radius: 0.5rem; /* Adjusted border radius */
        overflow: hidden;
    }

    .navbar-button {
        padding: 0.8rem; /* Adjusted padding */
        font-size: 1.2rem; /* Increased font size */
        color: silver;
        text-decoration: none;
        transition: background-color 0.3s, border-radius 0.3s;
        border-radius: 1.5rem; /* Adjusted border radius */
    }

    .navbar-button:hover {
        background-color: rgba(255, 255, 255, 0.2);
        border-radius: 1.5rem; /* Adjusted border radius on hover */
    }

    .navbar-button:hover img {
        transform: scale(1.1);
    }

    .navbar-button img {
        width: 28px; /* Adjusted image size */
        height: 28px;
        vertical-align: middle;
        transition: transform 0.3s;
    }

    .left-button {
        display: flex;
        align-items: center;
    }

    .right-buttons {
        display: flex;
        gap: 1rem; /* Adjusted gap */
    }
</style>

<div class="navbar">
    <a class="navbar-button left-button">
        <img src="/images/profile/home.png" alt="Logo" />
    </a>
    <div class="right-buttons">
        {#each navButtons as button, index (button.text)}
            <a
                    class="navbar-button"
                    href={button.link}
                    on:mouseenter={() => isHovered = index}
                    on:mouseleave={() => isHovered = -1}
            >
                {button.text}
            </a>
        {/each}
    </div>
</div>
