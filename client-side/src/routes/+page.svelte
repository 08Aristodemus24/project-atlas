<script>
    import Hero from "$lib/Hero.svelte";

    const images = [
        '0983.jpg',
        'IMG_2530.jpg', 
         
        'IMG_0470.png', 
        'IMG_0513.jpg', 
        'IMG_1451.png', 
        'IMG_0469.png', 
        'IMG_2872.jpg', 
        'IMG_3751.jpg', 
        'IMG_4993.jpg', 
        'IMG_5393.png', 
        'IMG_7288.jpg', 
        'IMG_9774.jpg', 
        'IMG_9897.jpg', 
        'Waiting.jpg'
    ]
</script>
<Hero>
    <div class="featured-image-container">
    </div>
</Hero>
<Hero section_name="featured">
    <h1 class="featured-header">Featured</h1>
    <div class="grid-container">
        {#each images as image, index}
            <div class={`featured-grid-${index + 1}`} data-grid-index={`${index + 1}`}>
                <img class="featured-grid-image" src={`https://raw.githubusercontent.com/08Aristodemus24/lalais-portfolio/master/client-side/src/assets/mediafiles/compressed/${image}`} alt=""/>
            </div>
        {/each}
    </div>
</Hero>
