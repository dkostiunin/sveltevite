<script>
  import { onMount } from "svelte";
  import { Router, Route, Link } from "svelte-navigator";
  import Catalog from "../pages/Catalog.svelte";
  let showMobileMenu = false;

  const handleMobileIconClick = () => (showMobileMenu = !showMobileMenu);

  const mediaQueryHandler = e => { if (!e.matches) {showMobileMenu = false}}
  onMount(() => {
    const mediaListener = window.matchMedia("(max-width: 767px)");
    mediaListener.addListener(mediaQueryHandler);
  });
  
</script>
<Router>
<nav>
  <div class="inner">
    <div on:click={handleMobileIconClick} class={`mobile-icon${showMobileMenu ? ' active' : ''}`}>
      <div class="middle-line"></div>
    </div>
    <div class="logo">
      <Link to="/" class="childClass"><h2>Darom.tk</h2></Link>
    </div>
    <div class={`navbar-list${showMobileMenu ? ' mobile' : ''}`}>     
      
      <div class="parent">
        <Link to="home" class="childClass">ГЛАВНАЯ</Link>
        <Link to="about" class="childClass">КАТАЛОГ</Link>
      </div>   
    </div>
    <div class="basket">
      <Link to="basket" class="childClass">Корзина</Link>
    </div>
  </div>
</nav>

  <Route path="basket/*blogRoute" component={Catalog} />
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
</Router>

<style>
  nav {
    background-color: #556cd6;
    font-family: "Roboto","Helvetica","Arial",sans-serif;
    height: 68px;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
  }
  .basket :global(.childClass) {
    color: white; text-decoration: none;
  }
  .logo :global(.childClass) {
    color: white; text-decoration: none;
  }
  .parent :global(.childClass) {
    color: white; text-decoration: none;font-size: 15px; padding-right: 15px;
  }
  
  .inner {
    padding-left: 20px;
    padding-right: 20px;
    margin: auto;
    box-sizing: border-box;
    display: flex;
    align-items: center;
    height: 100%;
  }

  .mobile-icon {
    width: 25px;
    height: 14px;
    position: relative;
    cursor: pointer;
  }

  .mobile-icon:after,
  .mobile-icon:before,
  .middle-line {
    content: "";
    position: absolute;
    width: 100%;
    height: 2px;
    background-color: #fff;
    transition: all 0.4s;
    transform-origin: center;
  }

  .mobile-icon:before,
  .middle-line {
    top: 0;
  }

  .mobile-icon:after,
  .middle-line {
    bottom: 0;
  }

  .mobile-icon:before {
    width: 66%;
  }

  .mobile-icon:after {
    width: 33%;
  }

  .middle-line {
    margin: auto;
  }

  .mobile-icon:hover:before,
  .mobile-icon:hover:after,
  .mobile-icon.active:before,
  .mobile-icon.active:after,
  .mobile-icon.active .middle-line {
    width: 100%;
  }

  .mobile-icon.active:before,
  .mobile-icon.active:after {
    top: 50%;
    transform: rotate(-45deg);
  }

  .mobile-icon.active .middle-line {
    transform: rotate(45deg);
  }

  .navbar-list {
    display: none;
    width: 100%;
    justify-content: space-between;
    margin: 0;
    padding: 0 40px;
  }

  .navbar-list.mobile {
    background-color: #556cd6;
    position: fixed;
    display: block;
    /* height: calc(100% - 45px);
    bottom: 0; */
    top:68px;left: 0;width: 100%;
    padding-bottom: 20px;
  }

  .navbar-list li {
    list-style-type: none;
    position: relative;
  }

  .navbar-list li:before {
    content: "";
    position: absolute;
    bottom: 0;
    left: 0;
    width: 100%;
    height: 1px;
  }

  .navbar-list a {
    color: #fff;
    text-decoration: none;
    display: flex;
    height: 68px;
    align-items: center;
    padding: 0 10px;
    font-size: 13px;
  }

  @media only screen and (min-width: 767px) {
    .mobile-icon {
      display: none;
    }

    .navbar-list {
      display: flex;
      padding: 0;
      justify-content: space-around;
    }

    .navbar-list a {
      display: inline-flex;
    }
  }

  @media (max-width: 767px) {
    .basket{position: fixed;right: 19px;}
    .logo{position: fixed;left: calc(50% - 52px);}
  }
</style>