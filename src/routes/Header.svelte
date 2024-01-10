<script>
 let isClient = false;

// Vérifier si le code s'exécute côté client
import { onMount } from 'svelte';
onMount(() => {
  isClient = true;

  window.addEventListener('scroll', handleScroll);

  return () => {
	window.removeEventListener('scroll', handleScroll);
  };
});

function handleScroll() {
  // Votre logique de défilement ici
  const contenaire = document.querySelector('.contenaire');
  const links = document.querySelector('.links');
  const contenaireHeight = contenaire.offsetHeight;

  if (window.scrollY > contenaireHeight) {
	console.log('is sticky');
	links.style.position = 'fixed';
    links.style.top = '0';
	links.style.backgroundColor = 'white';
	links.style.left = '50%';
    links.style.transform = 'translateX(-50%)';
	links.style.width = '95%';

  } else {
	links.style.position = 'relative';
      links.style.top = 'auto';
	  links.style.left = 'auto';
      links.style.transform = 'none';
	  links.style.width = '100%';

  }
}

</script>

<header>
	<div class="contenaire">
		<div class="logo">
			<img src="/favicon.png" alt="logo menu">
		</div>
		<div class="title">
			<p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Animi obcaecati veniam quo similique !</p>
			<h1>SUICIDE.COM</h1>
			<p>Lorem, ipsum dolor sit amet consectetur adipisicing elit. Animi obcaecati veniam quo similique !</p>
		</div>
		<div class="end"></div>
	</div>
	<div class="links">
		<div class="">
			<a href="#">Articles</a>
		</div>
		<div class="">
			<a href="#">Articles</a>
		</div>
		<div class="">
			<a href="#">Articles</a>
		</div>
		<div class="last">
			<a href="#">Articles</a>
		</div>
	</div>
</header>

<style>
	header {
		position: relative;
		width: 100vw;
		padding-top: 1rem;
		padding-bottom: 1rem;
		padding-left: 2rem;
		padding-right: 2rem;
	}

	.contenaire {
		border: 3px solid black;
		height: 170px;
		display: flex;
		justify-content: space-between;
		align-items: center;
		flex-direction: row;
	}

	.logo {
		border-right: 3px solid black;
		width: 10%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	img {
		border: 3px solid black;
		width: 70%;
		height: fit-content;
	}

	.end {
		border-left: 3px solid black;
		height: 100%;
		width: 10%;
	}

	.links {
		width: 100%;
		height: 64px;
		border: 3px solid black;
		border-top: 0;
		display: flex;
		justify-content: space-between;
		align-items: center;
		z-index: 1000;
		position: relative;
		top: 0;
		transition: width ease-in-out 50ms;
	}

	.links div {
		border-right: 3px solid black;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
		width: 40%;
	}

	div a {
		color: black;
	}

	.links .last {
		border: 0;
	}
</style>