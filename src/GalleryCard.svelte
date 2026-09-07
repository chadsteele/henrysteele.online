<script>
  export let adventure;
  export let index = 0;
</script>

<article class="gallery-item" style={`--delay: ${index * 90}ms`}>
  <div class="gallery-image">
    <img src={adventure.image} alt={adventure.title} loading={index === 0 ? 'eager' : 'lazy'} />
    <div class="image-wash"></div>
  </div>
  <div class="gallery-description">
    <h2>{adventure.title}</h2>
    <p>{adventure.description}</p>
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

  .gallery-image img {
    display: block;
    width: 100%;
    height: auto;
    transition: transform 700ms cubic-bezier(0.2, 0.75, 0.25, 1);
  }

  .gallery-item:hover .gallery-image img { transform: scale(1.06); }

  .image-wash {
    position: absolute;
    inset: 0;
    background: linear-gradient(180deg, rgba(36, 33, 51, 0) 25%, rgba(36, 33, 51, 0.8) 100%);
    opacity: 0.88;
  }

  .gallery-description {
    position: absolute;
    right: 0;
    bottom: 0;
    left: 0;
    z-index: 1;
    padding: 30px;
    background: linear-gradient(0deg, rgba(36, 33, 51, 0.96), rgba(36, 33, 51, 0.72), transparent);
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
    .gallery-image img {
      animation-duration: 1ms !important;
      transition-duration: 1ms !important;
    }
  }
</style>
