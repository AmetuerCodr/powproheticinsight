<script>
	import './layout.css';
	import favicon from '$lib/assets/Prophetic-Insight.ico';
	import { page } from '$app/stores';



  const baseUrl = import.meta.env.VITE_BASE_PUBLIC_URL; // e.g., "https://skye.top"
  const pageUrl = `${baseUrl}${$page.url.pathname}`;
  const title = "Prophetic Insight that Brings Clarity | Bishop Shammah Womack-El";
  const description = "Bishop Shammah Womack-El provides prophetic insight that brings clarity and wisdom-driven guidance for clear direction and discernment in decisions.";
  const image = `${baseUrl}/Prophetic-Insight.jpg`; // always absolute URL for social sharing
  const bgImage = "/a_woman_standing_on_a_mountain_top_with_raised_hands-1920x1152.jpg";
  const bishopPhoto = "/bishopphoto.png";
  const pageKeywords = "prophetic insight, wisdom-driven guidance, clear direction, discernment, Bishop Shammah Womack-El POW Prophet of Wellness, wellness, spiritual guidance, decision-making, clarity, wisdom, prophetic ministry, divine insight, real-world results";
	let { children } = $props();
</script>


<svelte:head>
  <!-- Open Graph / Facebook / LinkedIn / Discord / Slack -->
  <title>{title}</title>
  <meta name="keywords" content={pageKeywords} />
  <meta name="author" content="Bishop Shammah Womack-El" />
  <meta name="description" content={description} />
  <meta property="og:title" content={title} />
  <meta property="og:description" content={description} />
  <meta property="og:image" content={image} />
  <meta property="og:url" content={pageUrl} />
  <meta property="og:type" content="website" />
  <meta property="og:locale" content="en_US" />
  <!-- Twitter -->
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:title" content={title} />
  <meta name="twitter:description" content={description} />
  <meta name="twitter:image" content={image} />
  <meta name="twitter:url" content={pageUrl} />
  <!-- Optional: Twitter creator -->
  <meta name="twitter:creator" content="@YourTwitterHandle" />
  <!-- Optional / Generic -->
  <meta name="description" content={description} />
  <link rel="icon" href={favicon} />
</svelte:head>
{@render children()}