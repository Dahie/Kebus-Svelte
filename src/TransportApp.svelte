<script>
  import 'bulma/css/bulma.css';
  import appStoreBadge from '$lib/images/app-store-badge-en.svg';
  import playStoreBadge from '$lib/images/play-store-badge-en.svg';
  import webStoreBadge from '$lib/images/web-store-badge-en.svg';

	export let app;
</script>

<div class="card mt-2 mb-2">
  <div class="card-content">
    <p class="title">
      {app.title}
    </p>
    <p class="subtitle">
			<a href="{app.website_url}" target="_blank" rel="noreferrer">Website</a>
    </p>
  </div>
  <footer class="card-footer">
    <p class="card-footer-item">
      <a href="{app.app_store_url}">
        <img src={appStoreBadge} alt="Download from App Store">
      </a>
    </p>
		<p class="card-footer-item">
      <span>
        <a href="{app.play_store_url}">
          <img src={playStoreBadge} alt="Download from Google Play Store">
        </a>
      </span>
    </p>
		{#if app.web_store_url}
			<p class="card-footer-item">
				<span>
					<a href="{app.web_store_url}">
            <img src={webStoreBadge} alt="Download from online Web Store">
          </a>
				</span>
			</p>
		{/if}
  </footer>
</div>
	