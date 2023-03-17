<script>
  	let showMenu = false;
</script>

<nav>
  <div class="nav-container">
      <div class="nav-logo">
        <a href="/">
        <img src="/images/kebus-logo-inverse.svg" height="40" alt="Kebus Home page"></a>
      </div>
      <ul class="nav-links">
        <li><a href="/apps">Apps</a></li>
        <li><a href="/about-us">About</a></li>
      </ul>
      <a class="mobile-menu-toggle" on:click={() => showMenu = true}></a>
      {#if showMenu}
        <ul class="mobile-menu menu">
          <li><a href="/apps">Apps</a></li>
          <li><a href="/about-us">About</a></li>
        </ul>
        <div class="modal-background" on:click={() => showMenu = false}></div>
      {/if}
  </div>
  
</nav>

<style>
  nav {
    background-color: var(--dark-grey-bg-color);
  }

  nav .nav-links a {
    color: white
  }

  .menu.mobile-menu {
    display: block;
  }

  .mobile-menu-toggle::before {
    background-color: white;
    box-shadow: 0 8px 0 0 white,0 16px 0 0 white;
  }

  .modal-background {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
	}
  
</style>