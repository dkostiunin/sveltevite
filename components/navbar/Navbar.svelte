<script>
    import Fluid from "./src/index.svelte";
    const links = ['Главная','Каталог']
   
  </script>
    <Fluid breakpoint="md">
      <div slot="left">Darom.tk</div>
      <nav class="h-menu" slot="right">
        {#each links as link}
          <a href="/">{link}</a>
        {/each}
      </nav>
      <nav class="v-menu" slot="drawer">
        {#each links as link}
          <a href="/">{link}</a>
        {/each}
      </nav>
      <div slot="basket">Корзина</div>
    </Fluid>

  <style>
 .v-menu {
    background-color: lightblue;
    padding: 15px;
  }
  .v-menu a {
    display: block;
    padding-bottom: 15px;
  }
  .h-menu a {
    padding-right: 15px;
  }

  :global(.svelte-fluid-header--button) {
    color: grey;
  }
  :global(.svelte-fluid-header--button:hover) {
    color: black;
  }
  </style>