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
			<img  class="imgLogo" src="/favicon.png" alt="logo menu">
		</div>
		<div class="title">
			<p>Ne restez pas avec vos pensées négative, entourez-vous.</p>
			<h1>SUICIDE.COM</h1>
			<p>N’hésitez pas à parler à votre entourage si vous en ressentez le besoin</p>
		</div>
		<div class="end">
			<img class="phone"src="/phone.svg" alt="numero de téléphone">
			<h1>
				31 14
			</h1>
		</div>
	</div>
	<div class="links">
		<div class="">
			<a href="#"><h3>Mortalité en France</h3></a>
		</div>
		<div class="">
			<a href="#"><h3>Âge et Genre</h3></a>
		</div>
		<div class="">
			<a href="#"><h3>Passage à l'acte</h3></a>
		</div>
		<div class="last">
			<a href="#"><h3>VigilanS</h3></a>
		</div>
	</div>
</header>

<style>

	h3{
		font-size: 25px;
		text-align: center;
	}
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
		width: 20%;
		height: 100%;
		display: flex;
		justify-content: center;
		align-items: center;
	}

	.imgLogo {
		border: 3px solid black;
		/*max-width: 50%;*/
		height: 70%;
	}
@media screen and (max-width: 820px) {
	.imgLogo {
		max-width: 50%;
		height: fit-content;
	}
}

	.end {
		border-left: 3px solid black;
		height: 100%;
		width: 20%;
		display: flex;
		align-items: center;
		justify-content: center;
	}

	@media screen and (max-width: 620px) {
		.end {
		flex-direction: column;
	}
}
	.phone{
		width: 30px;
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
		background-image:url(/backgroundObject.png);
        background-size: contain;
        background-repeat: repeat;
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
	p{
		text-align: center;
	}


	@media screen and (max-width: 900px) {
	h3{
		font-size: 20px;
	}
}
</style>