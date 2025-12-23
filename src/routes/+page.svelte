<script>
   import 'plyr/dist/plyr.css';

   import { page } from '$app/stores';
    import { onMount } from 'svelte';
    import {fade} from 'svelte/transition';
    import {cubicOut} from 'svelte/easing';
    import { inview } from 'svelte-inview'
    import { browser } from '$app/environment';
	import { goto } from '$app/navigation';







let isInView = false;
let duration = 500;
let learnmore;
let player;
  let videoElement;
   let videoEl;  // Native video element reference
  let isMuted = true;  // Track mute state for button



 
onMount(async () => {
    if (!browser) return;

    learnmore = document.getElementById('learnmore');

    // Dynamic import hls.js only when needed
    const Hls = (await import('hls.js')).default;

    // Wait a tick if needed (rare), but bind:this usually works immediately
    if (Hls.isSupported() && videoEl) {
      const hls = new Hls();
      const sourceEl = videoEl.querySelector('source');
      if (sourceEl) {
        hls.loadSource(sourceEl.src);
        hls.attachMedia(videoEl);
      }
    }
    // Safari handles HLS natively → nothing needed

    // Setup autoplay, loop, mute
    if (videoEl) {
      videoEl.loop = true;
      videoEl.muted = true;
      videoEl.volume = 0;
      videoEl.play().catch(err => console.warn('Autoplay prevented:', err));

      // Update button when volume changes
      videoEl.addEventListener('volumechange', () => {
        isMuted = videoEl.muted || videoEl.volume === 0;
      });
    }
  });


 function toggleMute() {
    if (!videoEl) return;
    if (isMuted) {
      videoEl.muted = false;
      videoEl.volume = 0.7;  // Nice default level (adjust as needed)
    } else {
      videoEl.muted = true;
      videoEl.volume = 0;
    }
    isMuted = videoEl.muted || videoEl.volume === 0;
  }

   const clickLearnMore = () =>{
        learnmore.scrollIntoView({behavior: 'smooth'});
    }


  // Great subtle options:
  // Desert: https://images.unsplash.com/photo-1506905925346-21bda4d32df4
  // Misty mountains: https://images.unsplash.com/photo-1506318137071-a8e063b4c8ed
  // Night sky: https://images.unsplash.com/photo-1419242902214-272b3f66ee7a


  
  const baseUrl = import.meta.env.VITE_BASE_PUBLIC_URL; // e.g., "https://skye.top"
  const pageUrl = `${baseUrl}${$page.url.pathname}`;
  const title = "Prophetic Insight that Brings Clarity | Bishop Shammah Womack-El";
  const description = "Bishop Shammah Womack-El provides prophetic insight that brings clarity and wisdom-driven guidance for clear direction and discernment in decisions.";
  const image = `${baseUrl}/Prophetic-Insight.png`; // always absolute URL for social sharing
  const bgImage = "/a_woman_standing_on_a_mountain_top_with_raised_hands-1920x1152.jpg";
  const bishopPhoto = "/bishopphoto.png";
  const pageKeywords = "prophetic insight, wisdom-driven guidance, clear direction, discernment, Bishop Shammah Womack-El POW Prophet of Wellness, wellness, spiritual guidance, decision-making, clarity, wisdom, prophetic ministry, divine insight, real-world results";
</script>







<div class="prophetic-bg h-screen w-full relative overflow-hidden flex items-center">

  <!-- 1. Background image -->
  <div 
    class="absolute inset-0 bg-cover bg-center bg-no-repeat"
    style="background-image: url({bgImage});">
</div>

  <!-- 2. Dark amber/fuchsia overlay (keeps text readable + prophetic mood) -->
  <div class="absolute inset-0 bg-linear-to-b from-black/40 via-purple-950/60 to-fuchsia-900/60"></div>
  
  <!-- 3. Soft horizon glow on top of the overlay -->
  <div class="absolute bottom-0 left-0 right-0 h-96 bg-linear-to-t from-amber-600/30 via-fuchsia-600/20 to-transparent blur-3xl"></div>
  <!-- 4. Rising embers (same as before) -->






<div class="max-w-6xl relative z-10 mb-auto mt-10 sm:mt-14 mx-5 sm:ml-10 lg:ml-14 text-center sm:text-left">

  <!-- Headline -->
  <h1 class="text-white tracking-tight leading-[1.05]">

    <!-- Line 1 -->
    <span class="block renade-bold text-5xl sm:text-6xl md:text-7xl lg:text-7xl xl:text-8xl">
      Prophetic <span class="text-amber-400">Insight</span>
    </span>

    <!-- Line 2 -->
    <span class="block text-white mt-3 sm:mt-3 renade-regular text-5xl sm:text-5xl md:text-6xl lg:text-6xl xl:text-7xl">
      That Brings
      <span class="dancing-script inline text-6xl sm:text-6xl md:text-7xl lg:text-7xl xl:text-8xl
             bg-linear-to-br from-white via-gray-100 to-white/70
             bg-clip-text text-transparent
             drop-shadow-[0_4px_15px_rgba(255,255,255,0.5)]">
        Clarity
      </span>
    </span>

  </h1>

  <!-- Supporting text -->
  <p class="mt-4 sm:mt-10 renade-regular text-lg md:text-xl lg:text-2xl sm:max-w-xl max-w-lg mx-auto sm:mx-0
            bg-linear-to-br from-white via-gray-100 to-white/70
            bg-clip-text text-transparent
            drop-shadow-[0_4px_15px_rgba(255,255,255,0.5)]">
    Wisdom-driven prophetic guidance that provides clear direction, sharpens discernment in decisions, and positions you to move forward boldly and with confidence.
  </p>

  <!-- CTAs -->
  <div class="mt-9 sm:mt-10 flex flex-col sm:flex-row items-center sm:items-start gap-6">
    <button on:click={() =>{
      window.location.href = "https://2fa56510-20ca-4664-af0f-9e6d04f2c447.paylinks.godaddy.com/POWPropheticInsight"
    }} class="bg-gray-200 renade-bold rounded-md w-full sm:w-auto py-2 sm:px-8 text-sm sm:text-sm md:text-lg font-medium">
      Get started
    </button>

    <button on:click={clickLearnMore} class="bg-linear-to-br renade-bold from-amber-400 to-amber-500 rounded-md text-white w-full sm:w-auto py-2 sm:px-8 underline text-sm sm:text-sm md:text-lg font-medium">
      Learn more
    </button>
  </div>


  <button on:click={clickLearnMore} aria-labelledby="down arrow">

  <div class="ico animated sm:hidden ">
  
  <div class="circle circle-top"></div>  
  <div class="circle circle-main"></div>
  <div class="circle circle-bottom"></div>  
  
  <svg class="svg" version="1.1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px" viewBox="0 0 612 612" style="enable-background:new 0 0 612 612;" xml:space="preserve" >
  <defs>
    <clipPath id="cut-off-arrow">
      <circle cx="306" cy="306" r="287"/>
    </clipPath>
    
    <filter id="goo">
      <feGaussianBlur in="SourceGraphic" stdDeviation="10" result="blur" />
      <feColorMatrix in="blur" mode="matrix" values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -7" result="goo" />
      <feBlend in="SourceGraphic" in2="goo" />
    </filter>
   
  </defs>
    <path  class="st-arrow" d="M317.5,487.6c0.3-0.3,0.4-0.7,0.7-1.1l112.6-112.6c6.3-6.3,6.3-16.5,0-22.7c-6.3-6.3-16.5-6.3-22.7,0
					l-86,86V136.1c0-8.9-7.3-16.2-16.2-16.2c-8.9,0-16.2,7.3-16.2,16.2v301.1l-86-86c-6.3-6.3-16.5-6.3-22.7,0
					c-6.3,6.3-6.3,16.5,0,22.7l112.7,112.7c0.3,0.3,0.4,0.7,0.7,1c0.5,0.5,1.2,0.5,1.7,0.9c1.7,1.4,3.6,2.3,5.6,2.9
					c0.8,0.2,1.5,0.4,2.3,0.4C308.8,492.6,313.8,491.3,317.5,487.6z"/>
</svg>
</div>
  </button>

</div>




<!-- RIGHT: Bishop image -->
<div class="absolute right-0 bottom-0 h-full hidden sm:flex items-end pointer-events-none">
  <img
    src={bishopPhoto}
    loading="lazy"
    alt="Bishop Dr. Shammah Womack-El"
    class="
      h-[65vh]
      sm:h-[75vh]
      lg:h-[90vh]
      xl:h-[95vh]
      object-contain
    "
  />
</div>

</div>




<!-- second section -->
<div class="bg-slate-950  relative ">

    <div class="bg-[url('/abstract3.jpg')] object-cover bg-no-repeat  absolute inset-0"></div>

    <!-- overlay div -->
      <div class="absolute inset-0 z-10 bg-black/25"></div>
  <!-- Content -->
<div class="flex flex-col items-center justify-start relative">
  <!-- Your animated SVG stays 100% unchanged -->
  <svg class="absolute inset-0 w-full h-full z-0 opacity-50" viewBox="0 0 1920 1080" xmlns="http://www.w3.org/2000/svg">
    <!-- all your beautiful SVG code -->
  </svg>

  <!-- HERO TEXT – now perfectly centered + better breathing room -->
  <div id="learnmore" class="relative z-10 mt-20 lg:mt-32 text-center px-6 max-w-7xl">
    <h1 class="block lg:text-7xl md:text-6xl text-5xl leading-tight renade-regular text-white tracking-tight">
  This is    <span class="renade-bold">  Not</span>  <span class="text-amber-400 underline"> Guesswork.</span>
    </h1>
    <h1 class="block lg:text-7xl md:text-6xl text-5xl leading-tight renade-medium text-white tracking-tight">
    <span class="renade-regular">  This is </span>    <span class="dancing-script inline text-6xl sm:text-6xl md:text-7xl lg:text-7xl xl:text-8xl
       bg-linear-to-br from-white via-gray-100 to-white/70
       bg-clip-text text-transparent
       drop-shadow-[0_4px_15px_rgba(255,255,255,0.5)]">
        Wisdom.
</span>
    </h1>

    <div class="mt-8 lg:mt-12 max-w-6xl mx-auto ">
      <h2 class="text-2xl sm:text-2xl lg:text-3xl renade-medium text-white leading-snug">
        This <span class="text-amber-400">prophetic ministry</span> doesn’t just reveal, it <span class=" bg-linear-to-br from-white via-gray-100 to-white/70
            bg-clip-text text-transparent
            drop-shadow-[0_4px_15px_rgba(255,255,255,0.5)]">resolves</span>.
      </h2>
      <h2 class="text-2xl sm:text-2xl mb-8 sm:mb-0 lg:text-3xl renade-medium text-white leading-relaxed text-opacity-90 mt-4">
        Each session delivers <span class="text-amber-400">divine insight</span> that produces <span class=" bg-linear-to-br from-white via-gray-100 to-white/70
            bg-clip-text text-transparent
            drop-shadow-[0_4px_15px_rgba(255,255,255,0.5)]">real-world results</span>.
      </h2>
    </div>
  </div>

  <!-- VIDEO – perfectly centered with elegant max-width -->
  <div class="w-full max-w-7xl mx-auto mb-24 lg:mt-16 px-6 sm:px-10 lg:px-20">
    <div class="w-full aspect-256/135 bg-amber-300 rounded-2xl shadow-2xl overflow-hidden">

<button
      class=" absolute z-20 bg-black/70 hover:bg-black/90 text-white px-4 py-2.5 rounded-xl text-sm font-medium transition-all duration-200 flex items-center gap-2 shadow-2xl backdrop-blur-sm border border-white/20 hover:scale-105 active:scale-95"
      on:click={toggleMute}
      title={isMuted ? 'Unmute' : 'Mute'}>
      
      <!-- Icon changes based on state -->
      {#if isMuted}
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 4.75v14.5c0 .641-.077 1.087-.707.95L5.586 15z"/>
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 14l2-2m0 0l2-2m-2 2l-2-2m2 2l2 2"/>
        </svg>
        <span>Unmute</span>
      {:else}
        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5.586 15H4a1 1 0 01-1-1v-4a1 1 0 011-1h1.586l4.707-4.707C10.923 3.663 12 4.109 12 4.75v14.5c0 .641-.077 1.087-.707.95L5.586 15z"/>
        </svg>
        <span>Mute</span>
      {/if}
    </button>

<video 
bind:this={videoEl}
  playsinline 
  autoplay 
  muted 
  preload="auto"
  loading="lazy">
  <source src="https://nyc.cloud.appwrite.io/v1/storage/buckets/694ae94e001383811353/files/694af23300020555b2c8/view?project=694ae93a003d9d879a41" type="application/x-mpegURL" />
</video>
    </div>
  </div>


<!-- ================== Separate Wisdom Section ================== -->
<section class="relative min-h-screen w-full  bg-slate-950">

      <!-- Centered text -->

<div  class="relative w-full z-10 px-6 flex flex-col items-center mt-20 text-center max-w-6xl mx-auto">

  <!-- Eyebrow / qualifier -->

<svg class="absolute inset-0 w-full h-full pointer-events-none z-10" xmlns="http://www.w3.org/2000/svg">
  <defs>
    <circle id="star" r="1" fill="white"/>
  </defs>

  <g id="stars">
    <!-- 100 stars -->
    {#each Array(100) as _, i}
      <use href="#star" 
           x="{Math.random() * 100}%" 
           y="{Math.random() * 100}%" 
           class="star" 
           style="--i: {i};"/>
    {/each}
  </g>
</svg>

  <!-- Primary message -->
  <h2 class="renade-medium text-white tracking-tight leading-[1.1]
             text-4xl sm:text-5xl md:text-6xl lg:text-7xl lg:max-w-3xl max-w-sm sm:max-w-lg">
    If you're <span class="renade-bold text-white">tired</span> of going in circles
  </h2>

  <!-- Secondary line (supporting thought) -->
  <p class="mt-6 text-xl sm:text-xl md:text-2xl text-white/80 max-w-sm sm:max-w-3xl leading-relaxed">
    facing major <span class="renade-bold text-white">decisions</span> and needing
    <span class="renade-bold text-amber-400">wisdom</span>
    instead of <span class="renade-bold text-white" >confusion</span>:
    <span class=" block text-4xl mt-3.5 uppercase text-amber-400/80">this is for you.</span>
  </p>

</div>


<div  use:inview
  on:change={({ detail }) => {
    isInView = detail.inView;
  }}>
{#if isInView}
<section
  class="relative w-full min-h-screen overflow-hidden"
  in:fade={{ duration }}
>
  <!-- IMAGE BACKGROUND -->
  <div class="absolute inset-0 z-0 p-4">
    <div class="columns-2 sm:columns-3 md:columns-4 gap-3">
      <img src="/bishop12.jpg" class="w-full mb-3 block" alt="image1" />
      <img src="/bishop2.jpg" class="w-full mb-3 block" alt="image2" />
      <img src="/bishop3.jpg" class="w-full mb-3 block" alt="image3" />
      <img src="/bishop4.jpg" class="w-full mb-3 block" alt="image4" />
      <img src="/bishop5.jpg" class="w-full mb-3 block" alt="image5" />
      <img src="/bishop6.jpg" class="w-full mb-3 block" alt="image6" />
      <img src="/bishop7.jpg" class="w-full mb-3 block" alt="image7" />
      <img src="/bishop8.jpg" class="w-full mb-3 block" alt="image8" />
      <img src="/bishop9.png" class="w-full mb-3 block" alt="image9" />
      <img src="/bishop10.jpg" class="w-full mb-3 block" alt="image10" />
      <img src="/bishop11.jpg" class="w-full mb-3 block" alt="image11" />
      <img src="/bishop1.png" class="w-full mb-3 block" alt="image1" />
      <img src="/bishop13.jpg" class="w-full mb-3 block" alt="image13" />
      <img src="/bishop14.jpg" class="w-full mb-3 block" alt="image14" />
      <img src="/bishop15.jpg" class="w-full mb-3 block" alt="image15" />
      <img src="/bishop16.jpg" class="w-full mb-3 block" alt="image16" />
    </div>
  </div>

  <!-- DARK OVERLAY (readability) -->
  <div class="absolute inset-0 z-10 bg-black/20"></div>

  <!-- TEXT CONTENT -->
  <div class="relative z-20 min-h-screen flex flex-col items-center justify-center text-center px-6">
    <h1 class="renade-medium text-5xl md:text-6xl text-white max-w-4xl">
      <span class=" bg-linear-to-br from-white via-gray-100 to-white/70
       bg-clip-text text-transparent
       drop-shadow-[0_4px_15px_rgba(255,255,255,0.5)]">A Trusted</span> <span class="text-amber-400 dancing-script text-6xl md:text-7xl">Voice</span>
    </h1>

<p class="renade-regular text-lg md:text-xl lg:text-2xl text-white/90 max-w-3xl mt-6 leading-relaxed">
  For over <span class="font-semibold text-amber-400">35 years</span>, 
  Bishop <span class="font-semibold text-amber-300">Shammah Womack-El</span> has provided 
  <span class="font-medium text-white">accurate prophetic insight</span> to individuals, leaders, 
  and ministries nationwide.
</p>


    <p class="renade-regular text-lg md:text-xl lg:text-2xl text-white/90 max-w-3xl mt-6 leading-relaxed">
      Donate & Get your <span class="font-medium text-amber-400">prophetic insight</span> today!
    </p>
    <button on:click={() =>{window.location.href = "https://2fa56510-20ca-4664-af0f-9e6d04f2c447.paylinks.godaddy.com/POWPropheticInsight"}} class="mt-4 px-12 py-3 bg-fuchsia-800 text-white renade-bold text-xl rounded-full hover:bg-fuchsia-700 transition">Donate Now</button>
  </div>






</section>




{/if}
</div>


  <!-- Background image -->


  <!-- Dark overlay for readability -->
  <div class="absolute inset-0 bg-black/20"></div>



</section>


  <!-- Add more centered sections below if you want -->
</div>
</div>




<style lang="scss">
  

.star {
    opacity: 0.3;
    animation: twinkle 30s infinite alternate;
    animation-delay: calc(var(--i) * 0.1s);
  }

  @keyframes twinkle {
    0% { opacity: 0.2; transform: scale(1); }
    50% { opacity: 0.8; transform: scale(1.3); }
    100% { opacity: 0.2; transform: scale(1); }
  }  









:root {
  --circle-w: 100px;
  --circle-bg: #fff;
  --arrow-bg: #FFCA28;
  --body-bg: transparent;
  --bezier: cubic-bezier(0.77, 0, 0.175, 1);
  --bezier-bounce: cubic-bezier(.87, -.41, .19, 1.44);
  --anim-timing: 3s;
}


.ico {
  margin: 0 auto;
  margin-top: 6em;
  text-align: center;
  width: var(--circle-w);
  height: var(--circle-w);
  position: relative;
  top: 50%;
  transform: translateY(-50%);
  filter: url("#goo");
  .circle {
    background: var(--circle-bg);
    border-radius: 50%;
    display: inline-block;
    height: var(--circle-w);
    width: var(--circle-w);

    position: absolute;
    top: 50%;
    left:50%;
    transform: translateX(-50%) translateY(-50%);
    transform-origin: 0%;
    
    &.circle-top {
      height: var(--circle-w) / 3;
      width: var(--circle-w) / 2.4;
      animation: blob-1-anim var(--anim-timing) var(--bezier) infinite;
      z-index: 0;
      top:0;
    }
    &.circle-bottom {
      height: var(--circle-w) / 3;
      width: var(--circle-w) / 2.4;
      animation: blob-2-anim var(--anim-timing) var(--bezier)  infinite;
      z-index: 9;
      bottom:0px;
    }
    
  }
  
  
  .st-arrow{
    fill:var(--arrow-bg);
    animation: scrolly var(--anim-timing) var(--bezier) forwards infinite;
    perspective: 9000px;
    transform: translateZ(0);
    transform-origin: bottom;
  }
}

.svg {z-index:9;position:relative;}
  
@keyframes blob-1-anim {
  0%{
    transform:translateX(-50%) translateY(0);
  }
  14%{
    transform:translateX(-50%) translateY(-8px);
  }
  24% {
    transform:translateX(-50%) translateY(0);
  }
  100% {
    transform:translateX(-50%) translateY(0);
  }
}

@keyframes blob-2-anim {
  0% {
    //transform: scale(1) translate(-50%,-150%);
    transform: scale(1) translate(-50%,10px);
  }
  30% {
    //transform: scale(1) translate(-50%,-50%);
    transform: scale(1) translate(-50%,10px);
  }
  70% {
    //transform: scale(1) translate(-50%,-50%);
    transform: scale(1) translate(-50%,10px);
    
  }
  95% {
    //transform: scale(1) translate(-50%,-50%);
    transform: scale(1) translate(-50%,26px);
    
    
  }
  100% {
    //transform: scaleX(1.5) translate(-50%,140%);
    transform: scale(1) translate(-50%,10px);
  }
}

@keyframes scrolly {
  0% {
    transform: translate3d(0,-150%,0) rotateX(90deg) scale(0.5) skewX(3deg);
  }
  30% {
    transform: translate3d(0,0,0) rotateX(0deg) scale(1) skewX(0deg);
  }
  70% {
    transform: translate3d(0,0,0) rotateX(0deg) scale(1) skewX(0deg);
  }
  95% {
    transform: translate3d(0,50%,0) rotateX(-90deg) scale(0.5) skewX(-3deg);
  }
  100% {
    transform: translate3d(0,50%,0) rotateX(-90deg) scale(0.5) skewX(-3deg);
  }
}
</style>





