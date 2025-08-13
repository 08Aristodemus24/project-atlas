<script>
    export let section_name = "landing"
</script>

<section id={`${section_name}-section`} class="hero">
    <div class={`${section_name}-content`}>
        <slot/>
    </div>
</section>
