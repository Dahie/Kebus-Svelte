<script>
  export let app;
</script>

<div class="col col-md-6">
  <div class="package">
    <p class="package-name">
      <a href="{app.website_url}" target="_blank" rel="noreferrer">{app.title}</a>
    </p>
    <hr>
  
    <a href="{app.app_store_url}">
      <img src="/images/app-store-badge-en.svg" alt="Download from App Store">
    </a>
    <a href="{app.play_store_url}">
      <img src="/images/play-store-badge-en.svg"  alt="Download from Google Play Store">
    </a>
    {#if app.web_store_url}
      <a href="{app.web_store_url}">
        <img src="/images/web-store-badge-en.svg"  alt="Download from online Web Store">
      </a>
    {:else}
      <img src="/images/web-store-badge-en.svg"  class="disabled" alt="Download from online Web Store">
    {/if}
  </div>
</div>

<style>
  .package img.disabled {
    opacity: 30%;
  }
</style>