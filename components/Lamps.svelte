<script>
	import { onMount } from 'svelte';
	import Multiselect from '../components/Multiselect.svelte'
	function handleMessage(e) {console.log(e.detail);}
	let finres = [];

	const QUERY_PRODS = () => `{ 
			lamps { data{id attributes{
				createdAt lampholder color brand type Wattage Voltage Lifetime luminous name price shortdesc longdesc listimage instock sold rating ratecount article EAN13 countryorigin warranty flaskshape function
			} }}
		}`

	const options = {  method: "post",headers: {"Content-Type": "application/json"},body: JSON.stringify({query: QUERY_PRODS()})};

	async function getLamps() {
		const res= await fetch(`https://teststrapikost.herokuapp.com/graphql`, options)//
      	const fin= await res.json(), v=[]
	  	fin.data.lamps.data.forEach(i => {v.push({'value': i.id, 'name':i.attributes.name})});
		return v
	}
	let promise = getLamps();	

	onMount(async () => {//https://res.cloudinary.com/dxzefnveb/image/upload/v1653578851/jorql5rgzxlrilrlx0sy.svg
		const res= await fetch(`https://teststrapikost.herokuapp.com/graphql`, options)//https://teststrapikost.herokuapp.com/graphql http://localhost:1337/graphql
      //const fin= await res.json()
	  const photos = await res.json();
       finres=photos.data.lamps.data		
	});
</script>

<h1>Фотоальбом</h1>
{#await promise}
	<p>...подождите</p>
{:then number}
<Multiselect id='lang' list ={number}  on:message={handleMessage}></Multiselect>
<!-- <Multiselect id='lang' list ={number} bind:value={values}></Multiselect> -->
{:catch error}
	<p style="color: red">{error.message}</p>
{/await}

<!-- <button on:click={getLamps}>Get Lamps</button> -->

<div class="photos">
	{#each finres as photo}
	{#if photo.attributes.listimage&&photo.attributes.listimage.a}
	<p>{photo.attributes.name}</p>
		<figure>
			<img src={!photo.attributes.listimage||!photo.attributes.listimage.a?
					'https://res.cloudinary.com/dxzefnveb/image/upload/v1653578851/jorql5rgzxlrilrlx0sy.svg':
					photo.attributes.listimage.a
					} alt={photo.title}>
			<!-- <figcaption>{photo.title}</figcaption> -->
		</figure>
{:else}		
		 <p>загрузка...</p>
		 {/if}
	{/each}
</div>

<style>
	.photos {
		width: 100%;
		display: grid;
		grid-template-columns: repeat(5, 1fr);
		grid-gap: 8px;
	}

	figure, img {
		width: 100%;
		margin: 0;
	}
</style>