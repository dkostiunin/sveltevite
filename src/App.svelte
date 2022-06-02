<script>
  import logo from './assets/svelte.png'
  import Lamps from '../components/Lamps.svelte';
  import { Router, Route, Link } from "svelte-navigator";
  import Catalog from "../pages/Catalog.svelte";
  import Navbarsimple from '../components/Navbarsimple.svelte';
 
</script>
<Navbarsimple></Navbarsimple>

<!-- <Router>
 
    <h1>History</h1>

    <nav>
      <Link to="/">Base</Link>
      <Link to="home">Homee</Link>
      <Link to="about">About</Link>
      <Link to="blog">Blog</Link>
    </nav>

  <div>
    <Route path="blog/*blogRoute" component={Catalog} />

    <Route path="home">
      <h3>Home</h3>
      <p>Home sweet home...</p>
    </Route>

    <Route path="about">
      <h3>About</h3>
      <p>That's what it's all about!</p>
    </Route>

    <Route>
      <h3>Default</h3>
      <p>No Route could be matched.</p>
    </Route>
  </div>
</Router> -->


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

<!-- <main>
  <Lamps></Lamps>
  <img src={logo} alt="Svelte Logo" />
  <h1>Hello world!</h1>


</main>
 -->
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
  
  
</style>
