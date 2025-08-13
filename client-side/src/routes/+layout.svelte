<script>    
    import Navbar from "$lib/Navbar.svelte";
    import Footer from "$lib/Footer.svelte";
    import '$lib/stylesheets/content.css';
    import '$lib/stylesheets/navbar-862-and-up.css';
    import '$lib/stylesheets/navbar-862-down.css';
</script>

<Navbar />
<slot />
<Footer />