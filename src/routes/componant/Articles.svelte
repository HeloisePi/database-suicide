<script>
    import { onMount } from 'svelte';

    export let imgSrc;
    export let imgAlt;
    export let title;

    let showPopup = false;

    function openPopup() {
        showPopup = true;
    }

    function closePopup() {
        showPopup = false;
    }

    // Ferme la popup si l'utilisateur clique en dehors de l'image
    onMount(() => {
        window.addEventListener('click', (event) => {
            if (showPopup && !event.target.closest('.popup-content')) {
                closePopup();
            }
        });
    });
</script>

<section>
    <div class="images" on:click|stopPropagation={openPopup}>
        <h3>{title}</h3>
        <img src="{imgSrc}" alt="{imgAlt}">
    </div>


    {#if showPopup}
        <div class="popup-overlay">
            <div class="popup-content" on:click|stopPropagation={e => e.stopPropagation()}>
                <span class="close-btn" on:click={closePopup}>&times;</span>
                <img src="{imgSrc}" alt="{imgAlt}">
            </div>
        </div>
    {/if}

    <div class="description">
        <p><slot></slot></p>
    </div>
</section>

<style>
    section {
        display: flex;
        justify-content: center;
        align-items: start;
    }

    .description{
        border: 3px solid black;
        padding: 2rem;
        padding-left: 4rem;
        padding-right: 4rem;
        max-width: 70%;
        transform: translateX(9rem);
    }

    .images {
        cursor: pointer; /* Ajout du curseur pointer pour indiquer que l'image est cliquable */
        border: 2px black dashed;
        width: min-content;
        padding: 1rem;
        position: absolute;
        background-image:url(/backgroundObject.png);
        background-size: contain;
        background-repeat: repeat;
        transform: translate(-21rem, -4rem);
        z-index: 3;
    }

    img {

        height: fit-content;
        max-width: 350px;
    }

    .popup-overlay {
        position: fixed;
        top: 0;
        left: 0;
        width: 100%;
        height: 100%;
        background: rgba(255, 255, 255, 0.7);
        display: flex;
        justify-content: center;
        align-items: center;
        z-index: 1000;
    }

    .popup-content {
        position: relative;
        text-align: center;
    }

    .close-btn {
        position: absolute;
        top: 10px;
        right: 10px;
        font-size: 20px;
        color: rgb(0, 0, 0);
        cursor: pointer;
    }

    .popup-content {
    position: relative;
    text-align: center;
    max-width: 80%;  /* Ajout de la largeur maximale pour la popup content */
    max-height: 80%; /* Ajout de la hauteur maximale pour la popup content */
}
h3{
    max-width: 70%;
}

.popup-content img {
    max-width: 100vw;  /* Ajout de la largeur maximale pour l'image dans la popup */
    height: fit-content; /* Ajout de la hauteur maximale pour l'image dans la popup */
}


@media screen and (max-width: 1100px) {
		section{
            flex-direction: column-reverse;
            align-items: center;
            gap: 1rem;
        }

        .images{
            position: relative;
            transform: translate(0rem, 0rem);
        }
        .description{
            transform: translateX(0rem);
    }
}

@media screen and (max-width: 600px) {

        .description{
            padding-left: 1rem;
        padding-right: 1rem;
        }
}


</style>
