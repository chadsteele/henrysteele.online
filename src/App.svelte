<script>
  import adventures from './data/adventures.js';
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
     <p>I speak: 🇺🇸 English and 🇨🇳 Chinese fluently, 🇫🇷 French (3 years), and a little 🇪🇸 Spanish, 🇯🇵 Japanese, and 🎸 Rock'n Roll</p>
       <p>
    Let's talk!  
        ✉️  <a href="mailto:henrysogod@gmail.com">Email</a> &nbsp;
        ☎️  <a href="https://wa.me/+23057464071">WhatsApp</a>
    </p>
    <div class="intro-copy">
      <p>I'm looking for my next gig and volunteer opportunity. I'm spending this year traveling around the world, making a difference with animals, nature, and communities, and learning new skills as I go.</p>
      <p>I graduated high school last spring with a 3.8 GPA.  I love mountains and play soccer, basketball, MMA and ultimate frisbee.  I love to travel, learn, and explore new things. I have a passion for animals, music, nature, and the environment. I also love to cook and play my guitar. I'm looking for opportunities to learn and grow as a person and make a positive impact on the world.</p>
      <p>Please share this site with anyone you think might be interested in hiring me or offering me a volunteer opportunity. I'm open to anything and everything. I want to learn and grow as a person and make a positive impact on the world. Thank you for your time and consideration.</p>
     
    </div>
  
    
  </header>
  <section class="gallery-grid" aria-label="Adventures">
    {#each adventures as adventure, index}
      <GalleryCard {adventure} {index} />
    {/each}
  </section>
  <footer class="site-footer">
  Let's talk! &nbsp;
   
     ✉️  <a href="mailto:henrysogod@gmail.com">Email</a> &nbsp; 
     ☎️  <a href="https://wa.me/+23057464071">WhatsApp</a>
   
  </footer>
</main>
