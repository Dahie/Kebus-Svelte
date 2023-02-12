<script>
  import { FontAwesomeIcon } from '@fortawesome/svelte-fontawesome'
  import { faGlobe } from '@fortawesome/free-solid-svg-icons'
  import { faGooglePlay, faApple } from '@fortawesome/free-brands-svg-icons'
  import { config } from '@fortawesome/fontawesome-svg-core'
  
  export let app;
</script>

<div class="col col-md-6">
  <div class="package">
    <p class="package-name">
      <a href="{app.website_url}" target="_blank" rel="noreferrer">{app.title}</a>
    </p>
    <hr>
    <div class="store-link">
      <a href="{app.app_store_url}" class="button button-primary button-round">
        <FontAwesomeIcon icon={faApple} />
        Apple App Store
      </a>
    </div>
    <div class="store-link">
      <a href="{app.play_store_url}" class="button button-primary button-round">
        <FontAwesomeIcon icon={faGooglePlay} />
        Google Play Store
      </a>
    </div>
    
    {#if app.web_store_url}
      <div class="store-link">
        <a href="{app.web_store_url}" class="button button-primary button-round">
          <FontAwesomeIcon icon={faGlobe} />
          Web Shop
        </a>
      </div>
    {:else}
      <div class="store-link">
        <div class="button button-primary button-round button-disabled">
          <FontAwesomeIcon icon={faGlobe} />
          Web Shop
        </div>
      </div>
    {/if}
  </div>
</div>

<style>
  .store-link {
    margin: 15px 0;
  }

  .store-link:last-of-type {
    margin-bottom: 0;
  }

  .package {
    display: block;
    border: 0;
    border-radius: 1rem;
  }  

  .package-name a {
    text-transform: none;
    font-size: 1.2rem;
    font-weight: bold;
  }

  .button-disabled {
    opacity: 0.3;
  }

</style>