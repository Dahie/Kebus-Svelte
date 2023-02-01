<script>
	import apps from '../../apps.json';
	import Region from '../../Region.svelte';
	import TransportApp from '../../TransportApp.svelte';
</script>


{#if apps}
  <table class="table is-fullwidth">
    <thead>
      <tr>
        <th>Ticket App</th>
        <th>Regions</th>
        <th>iOS</th>
        <th>Android</th>
        <th>Web</th>
      </tr>
    </thead>
    <tbody>
      {#each apps as app}
        <tr>
          <td class="app-title">
            <a href="{app.website_url}">{app.title}</a>
          </td>
          <td>
            {app.regions.map(region => region.title).join(', ')}
          </td>
          <td>
            <a href="{app.app_store_url}">
              <img src="/images/app-store-badge-en.svg" alt="Download from App Store">
            </a>
          </td>
          <td>
            {#if app.play_store_url}
              <a href="{app.play_store_url}">
                <img src="/images/play-store-badge-en.svg" alt="Download from Google Play Store">
              </a>
            {/if}
          </td>
          <td>
            {#if app.web_store_url}
              <a href="{app.web_store_url}">
                <img src="/images/web-store-badge-en.svg" alt="Download from Web Store">
              </a>
            {/if}
          </td>
          <td></td>
        </tr>
      {/each}
    </tbody>
  </table>
{:else}
	<p class="loading">loading...</p>
{/if}

<style>
  td.app-title {
    font-weight: bold;
  }

  td img {
    min-height: 40px;
    max-width: inherit;
  }
</style>
