<script>
  import adventures from './data/adventures.json';
</script>

<svelte:head>
  <title>Adventures Along the Way</title>
  <meta name="description" content="A gallery of memorable adventures along the way." />
</svelte:head>

<main class="container">
  <header class="intro">
    <p class="eyebrow">A collection of moments</p>
    <h1>Adventures Along the Way</h1>
    <p class="intro-copy">Five memories, gathered from shorelines, kitchens, mountain roads, and quiet encounters.</p>
  </header>

  {#each adventures as adventure, index}
    <article class={`gallery-item ${adventure.layout}`} style={`--delay: ${index * 90}ms`}>
      <div class="gallery-image">
        <img src={adventure.image} alt={adventure.alt} loading={index === 0 ? 'eager' : 'lazy'} />
        <div class="image-wash"></div>
      </div>
      <div class="gallery-description">
        <span class="card-number">0{index + 1}</span>
        <h2>{adventure.title}</h2>
        <p>{adventure.description}</p>
      </div>
    </article>
  {/each}
</main>
