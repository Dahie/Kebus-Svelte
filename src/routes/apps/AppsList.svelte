<script>
	import 'bulma/css/bulma.css';
	import Button from 'svelma/src/components/Button.svelte';
	import apps from '../../apps.json';
	import Region from '../../Region.svelte';
	import TransportApp from '../../TransportApp.svelte';
  import appStoreBadge from '$lib/images/app-store-badge-en.svg';
  import playStoreBadge from '$lib/images/play-store-badge-en.svg';
  import webStoreBadge from '$lib/images/web-store-badge-en.svg';
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
              <img src={appStoreBadge} alt="Download from App Store">
            </a>
          </td>
          <td>
            {#if app.play_store_url}
              <a href="{app.play_store_url}">
                <img src={playStoreBadge} alt="Download from Google Play Store">
              </a>
            {/if}
          </td>
          <td>
            {#if app.web_store_url}
              <a href="{app.web_store_url}">
                <img src={webStoreBadge} alt="Download from Web Store">
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
