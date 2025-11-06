<script>
	import apps from '../../apps.json';

  let sortByAppTitle = function (a, b) {
    if (a.title.toLowerCase() < b.title.toLowerCase()) {
      return -1;
    }
    if (a.title.toLowerCase() > b.title.toLowerCase()) {
      return 1;
    }
    return 0;
  };
</script>


{#if apps}
  <section>
    <table>
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
        {#each apps.sort(sortByAppTitle) as app}
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
          </tr>
        {/each}
      </tbody>
    </table>
  </section>
  
{:else}
	<p class="loading">loading...</p>
{/if}

<style>
  td.app-title a {
    font-weight: bold;
  }

  td img {
    min-height: 40px;
    max-height: 60px;
    max-width: inherit;
  }

  table { 
    width: 100%; 
    border-collapse: collapse; 
  }
  /* Zebra striping */
  tbody tr:nth-of-type(odd) { 
    background-color: var(--lightest-grey-bg-color);
    border-radius: 1em;
  }
  th { 
    font-weight: bold; 
  }
  td, th { 
    padding: 6px; 
    
    text-align: left; 
  }

  @media 
  only screen and (max-width: 760px),
  (min-device-width: 768px) and (max-device-width: 1024px)  {

    /* Force table to not be like tables anymore */
    table, thead, tbody, th, td, tr { 
      display: block; 
    }
    
    /* Hide table headers (but not display: none;, for accessibility) */
    thead tr { 
      position: absolute;
      top: -9999px;
      left: -9999px;
    }
    
    tr { 
      margin-bottom: var(--spacer);
    }
    
    td { 
      /* Behave  like a "row" */
      border: none;
      position: relative;
      padding-left: 50%; 
    }
    
    td:before { 
      /* Now like a table header */
      position: absolute;
      /* Top/left values mimic padding */
      top: 6px;
      left: 6px;
      width: 45%; 
      padding-right: 10px; 
      white-space: nowrap;
    }
    
    /*
    Label the data
    */
    td:nth-of-type(1):before { content: "Ticket App"; }
    td:nth-of-type(2):before { content: "Region"; }
    td:nth-of-type(3):before { content: "iOS"; }
    td:nth-of-type(4):before { content: "Android"; }
  }
</style>
