<script>
	import './layout.css';
	import favicon from '$lib/assets/Prophetic-Insight.ico';
	import { page } from '$app/stores';



  const baseUrl = import.meta.env.VITE_BASE_PUBLIC_URL; // e.g., "https://skye.top"
  const pageUrl = `${baseUrl}${$page.url.pathname}`;
  const title = "Prophetic Insight that Brings Clarity | Bishop Shammah Womack-El";
  const description = "Bishop Shammah Womack-El provides prophetic insight that brings clarity and wisdom-driven guidance for clear direction and discernment in decisions.";
  const image = `/Prophetic-Insight.jpg`; // always absolute URL for social sharing
  const bgImage = "/a_woman_standing_on_a_mountain_top_with_raised_hands-1920x1152.jpg";
  const bishopPhoto = "/bishopphoto.png";
  const pageKeywords = "prophetic insight, wisdom-driven guidance, clear direction, discernment, Bishop Shammah Womack-El POW Prophet of Wellness, wellness, spiritual guidance, decision-making, clarity, wisdom, prophetic ministry, divine insight, real-world results";
	let { children } = $props();
</script>



{@render children()}