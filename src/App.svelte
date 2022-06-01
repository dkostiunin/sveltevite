<script>
  import logo from './assets/svelte.png'
  import Lamps from '../components/Lamps.svelte';
  import Navbar from '../components/navbar/Navbar.svelte';
 
</script>
<header>
  <Navbar></Navbar>
</header>



<!-- <p>
	Let's read the <code>values</code> of the MultiSelect:
</p>
{#if values && values.length}
	<ul>
		{#each values as val}
			<li>
				{val}
			</li>
		{/each}
	</ul>
{:else}
	<div>
		Nothing selected
	</div>
{/if} -->

<main>
  <Lamps></Lamps>
  <img src={logo} alt="Svelte Logo" />
  <h1>Hello world!</h1>


</main>

<style>
  :root {
    font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
      Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;
  }

  main {
    text-align: center;
    padding: 1em;
    margin: 0 auto;
  }

  img {
    height: 16rem;
    width: 16rem;
  }

  h1 {
    color: #ff3e00;
    text-transform: uppercase;
    font-size: 4rem;
    font-weight: 100;
    line-height: 1.1;
    margin: 2rem auto;
    max-width: 14rem;
  }

/*   p {
    max-width: 14rem;
    margin: 1rem auto;
    line-height: 1.35;
  }
 */
  @media (min-width: 480px) {
    h1 {
      max-width: none;
    }
/* 
    p {
      max-width: none;
    } */
  }
  header {
    background-color: lightblue;
    height: 50px;
    padding: 0 15px;
  }

  
</style>
