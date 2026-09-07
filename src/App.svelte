<script>
  import adventures from './data/adventures.json';
  import GalleryCard from './GalleryCard.svelte';
</script>

<svelte:head>
  <title>Henry Steele</title>
  <meta name="description" content="About Henry Steele" />
</svelte:head>

<main class="container">
  <header class="intro">
    <p class="eyebrow">My gap year and bucket list adventures</p>
    <h1>Hi!  I'm Henry</h1>
    <p class="intro-copy">I'm looking for my next gig and volunteer opportunity.  I'm spending this year traveling around the world and making a difference with animals, nature, and communities and learning new skills as I go.</p>
    <p>
    Let's talk!  
        ✉️  <a href="mailto:henrysogod@gmail.com">Email</a> &nbsp;
        ☎️  <a href="https://wa.me/+23057464071">WhatsApp</a>
    </p>
    
  </header>
  <section class="gallery-grid" aria-label="Adventures">
    {#each adventures as adventure, index}
      <GalleryCard {adventure} {index} />
    {/each}
  </section>
</main>
