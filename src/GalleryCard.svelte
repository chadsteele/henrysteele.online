<script>
  export let adventure;
  export let index = 0;

  let muted = true;

  $: descriptionLink = adventure.description.match(/<a\b[^>]*href=['"]([^'"]+)['"][^>]*>(.*?)<\/a>/i);
  $: descriptionMarkup = adventure.description.replace(/<a\b[^>]*href=['"][^'"]+['"][^>]*>(.*?)<\/a>/i, '');
</script>

<article class:has-video={adventure.video} class="gallery-item" style={`--delay: ${index * 90}ms`}>
  <div class="gallery-image">
    {#if adventure.video}
      <video
        src={adventure.video}
        autoplay
        muted={muted}
        loop
        playsinline
        aria-label={adventure.title}
      ></video>
      <button
        class="mute-toggle"
        type="button"
        aria-label={muted ? 'Unmute video' : 'Mute video'}
        title={muted ? 'Unmute video' : 'Mute video'}
        onclick={() => (muted = !muted)}
      >
        {muted ? '🔇' : '🔊'}
      </button>
    {:else}
      <img src={adventure.image} alt={adventure.title} loading={index === 0 ? 'eager' : 'lazy'} />
    {/if}
    <div class="image-wash"></div>
  </div>
  <div class="gallery-description">
    <h2>{@html adventure.title}</h2>
    <p>{@html descriptionMarkup}</p>
    {#if descriptionLink}
      <a
        class="description-link"
        href={descriptionLink[1]}
        target="_blank"
        rel="noreferrer"
      >{descriptionLink[2]}</a>
    {/if}
  </div>
</article>

<style>
  .gallery-item {
    position: relative;
    width: 100%;
    overflow: hidden;
    border: 3px solid #242133;
    border-radius: 22px;
    background: #fffdf8;
    box-shadow: 7px 8px 0 #242133;
    isolation: isolate;
    animation: reveal 800ms var(--delay) cubic-bezier(0.2, 0.75, 0.25, 1) both;
  }

  .gallery-item {
    break-inside: avoid;
    margin-bottom: 32px;
  }

  .gallery-image {
    position: relative;
    width: 100%;
    overflow: hidden;
  }

  .gallery-item.has-video .gallery-image {
    aspect-ratio: 3 / 5;
  }

  .gallery-image img,
  .gallery-image video {
    display: block;
    width: 100%;
    height: auto;
    transition: transform 700ms cubic-bezier(0.2, 0.75, 0.25, 1);
  }

  .gallery-item.has-video .gallery-image video {
    height: 100%;
    object-fit: cover;
  }

  .gallery-item:hover .gallery-image img,
  .gallery-item:hover .gallery-image video { transform: scale(1.06); }

  .image-wash {
    position: absolute;
    inset: 0;
    background: linear-gradient(180deg, rgba(36, 33, 51, 0) 25%, rgba(36, 33, 51, 0.8) 100%);
    opacity: 0.88;
  }

  .mute-toggle {
    position: absolute;
    top: 16px;
    right: 16px;
    z-index: 2;
    display: grid;
    width: 42px;
    height: 42px;
    place-items: center;
    padding: 0;
    border: 2px solid #fffdf8;
    border-radius: 50%;
    background: rgba(36, 33, 51, 0.78);
    color: #fffdf8;
    cursor: pointer;
    font-size: 1.1rem;
    line-height: 1;
    transition: transform 180ms ease, background 180ms ease;
  }

  .mute-toggle:hover {
    background: rgba(36, 33, 51, 0.96);
    transform: scale(1.08);
  }

  .mute-toggle:focus-visible {
    outline: 3px solid #ffd166;
    outline-offset: 3px;
  }

  .gallery-description {
    position: absolute;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1;
    padding: 30px;
    background: linear-gradient(0deg, rgba(36, 33, 51, 0.96), rgba(36, 33, 51, 0.5), transparent);
  }

  .description-link {
    display: inline-flex;
    margin-top: 18px;
    padding: 10px 16px;
    border: 2px solid #ffd166;
    border-radius: 999px;
    background: #ffd166;
    color: #242133;
    font-weight: 700;
    line-height: 1.2;
    text-decoration: none;
    transition: background 180ms ease, color 180ms ease, transform 180ms ease;
  }

  .description-link:hover,
  .description-link:focus-visible {
    background: transparent;
    color: #fffdf8;
    transform: translateY(-2px);
  }

  .gallery-description h2 {
    margin: 0 0 12px;
    color: #fffdf8;
    font-family: 'Space Grotesk', sans-serif;
    font-size: clamp(1.8rem, 3vw, 2.8rem);
    line-height: 1.05;
  }

  .gallery-description p {
    max-width: 480px;
    margin: 0;
    color: #f4edf0;
    line-height: 1.7;
  }

  @keyframes reveal {
    from { opacity: 0; transform: translateY(28px); }
    to { opacity: 1; transform: translateY(0); }
  }

  @media (max-width: 759px) {
    .gallery-item { margin-bottom: 24px; }
    .gallery-description { padding: 26px; }
  }

  @media (prefers-reduced-motion: reduce) {
    .gallery-item,
    .gallery-image img,
    .gallery-image video {
      animation-duration: 1ms !important;
      transition-duration: 1ms !important;
    }
  }
</style>
