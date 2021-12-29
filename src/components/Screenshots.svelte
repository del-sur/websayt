<script lang="ts">
  interface Image {
    key: string
    alt: string
    orientation?: 'landscape' | 'portrait'
  }
  type Images = Array<Image>

  const URL = 'https://res.cloudinary.com/di60w2ni6/image/upload'

  export let images: Images


  function landscapeImage(key: string): string {
    return `${URL}/w_736,c_fill/work/${key}`
  }
  
  function portraitImage(key: string): string {
    return `${URL}/w_320,ar_9:20,c_fill/work/${key}`
  }

  function transform(images: Images): Array<{ src: string, alt: string }> {
    return images.map(({ key, orientation, alt }) => ({
      src: orientation === 'portrait' ? portraitImage(key) : landscapeImage(key),
      alt,
    }))
  }
</script>

<div class="flex flex-wrap justify-between">
  {#each transform(images) as { src, alt }}
    <a class="p-3" href={src} target="_blank">
      <img {src} {alt} />
    </a>
  {/each}
</div>
