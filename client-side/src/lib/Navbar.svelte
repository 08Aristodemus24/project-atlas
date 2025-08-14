<script>
    import { afterUpdate } from "svelte";

    let is_opened = false, is_at_top = true;
    let scroll_y = 0;
    $:rounded_scroll_y = Math.round(scroll_y);
    // const body = document.body;
    
    // if div is closed then its class is .closed if opened then .opened
    const toggle_menu = (event) => {
        if(is_opened === false){
        is_opened = !is_opened;
        // body.style.overflow = "hidden";

        }else{
        is_opened = !is_opened;
        // body.style.overflow = "auto";
        }
    };

    // I don't want links in desktop mode to have access to the modal
    // if navbar is opened then only then can it be closed
    // but what if user opens modal and sets the dims to desktop
    // then when a tag is clicked modal will be closed
    const close_and_go = (event) => {
        if(is_opened === true){
            is_opened = !is_opened;
            // body.style.overflow = "auto";
        }

        const section_id = event.target.classList[1];
        const section = document.querySelector(`#${section_id}`);
        section.scrollIntoView({
            block: 'start',
        });
    }

    const change_nav = () => {
        /*
        nav should only be hidden after 5 seconds under these conditions: 
        1. if above scrollY of 0
        
        nav should also not be hidden:
        1. if below or equal to scrollY of 0
        2. if modal is opened

        so if idle state is now set to false meaning navbar is to 
        be shown then class shown is added to the navbar container 
        */
        const rounded_scroll_y = Math.round(scroll_y);
        console.log(rounded_scroll_y);

        // if strictly modal is closed and scrollY is scrolled and not
        // at the top only count down to subsequently hide navbar
        if(rounded_scroll_y > 1 && is_opened === false){
            is_at_top = false
        }else if(rounded_scroll_y === 1 && is_opened === false){
            is_at_top = true
        }
    };

    afterUpdate(() => {
        console.log(`changed navbar state ${is_opened}`);
        console.log(`is at the top ${is_at_top}`);
    });
</script>

<svelte:window on:scroll={change_nav} bind:scrollY={scroll_y}/>
<header 
    class="navbar-container"
    class:opened={is_opened}
    class:not-at-top={!is_at_top}
>
    <nav class="navbar">
        <div class="nav-brand-container">
            <a 
                class="navbar-brand" 
                href="/"
            >
                <header>Atlas and Demeter</header>  
                <small>functional strength & artisanal meal prep</small>
            </a>
            <!-- <div 
                on:click|preventDefault={toggle_menu} 
                class="button-container" 
                class:opened={is_opened === true}
            > -->
            <div 
                on:click|preventDefault={toggle_menu} 
                class="button-container" 
                class:opened={is_opened}
            >
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="top-left-corner"></a>
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="top-edge"></a>
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="top-right-corner"></a>
                
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="left-edge"></a>
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="center"></a>
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="right-edge"></a>
                
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="bottom-left-corner"></a>
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="bottom-edge"></a>
                <a aria-label="https://svelte.dev/e/a11y_incorrect_aria_attribute_type" href="" class="bottom-right-corner"></a>
            </div>
        </div>
        
        <div class="nav-menu-container">
            <div class="nav-menu">
                <a href="/about-me" class="nav-item about-me-section">about me</a>
                <a href="/primer" class="nav-item primer-section">primer</a>
                <a href="/services" class="nav-item services-section">services</a>
                <!-- <a class="nav-item about-section" aria-current="page" on:click={close_and_go}>ABOUT</a>
                <a class="nav-item work-group-section" on:click={close_and_go}>WORK</a>
                <a class="nav-item contact-section" on:click={close_and_go}>CONTACT</a> -->
            </div>
        </div>
    </nav>
</header>