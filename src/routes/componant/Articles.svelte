<script>
    export let imgSrc;
    export let imgAlt;

</script>


<section>
    <div class="images">
        <h3>suicide post-covid</h3>
        <img src="{imgSrc}" alt="{imgAlt}">
    </div>

    <div class="">
        <p><slot></slot></p>
    </div>

</section>


<style>
    section{
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .images{
        border: 2px black dashed;
        width: 30%;
        padding: 1rem;
    }
    img{
        width: -webkit-fill-available;
        height:-webkit-fill-available;
    }

</style>