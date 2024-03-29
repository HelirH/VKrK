<div id="link" on:click={() => expanded = !expanded} on:mouseenter={() => {if(!mobile) {expanded = true}}} on:mouseleave={() => {if(!mobile) {expanded = false}}} class:expanded="{expanded}">
    <slot name="link"/>
    <div id="dropdown" on:mouseleave={() => expanded = false} class:expanded="{expanded}">
        <slot name="dropdown"/>
    </div>
</div>

<svelte:window bind:innerWidth/>

<script>
    let expanded = false;
    let innerWidth;
    let mobile;

    $: if (innerWidth <= 1000)
        mobile = true;
    else
        mobile = false
</script>

<style>
    #link {
        padding: 30px 0;
    }

    #link :global(.link) {
        text-wrap: nowrap;
    }

    #link.expanded {
        position: relative;
        align-self: start;
        top: -6px;
    }

    #dropdown {
        z-index: 10;
        position: absolute;
        margin-top: 30px;
        padding: 20px;
        flex-grow: 500;
        background-color: white;
        border-top: 3px rgb(209, 219, 151) solid;
        display: none;
        line-height: 2em;
    }

    #dropdown.expanded {
        display: block;
        animation: fade 0.3s;
    }

    @keyframes fade {
        from {opacity: 0; display: block;}
        to {opacity: 1;}
    }

    #dropdown :global(a) {
        display: none;
    }

    #dropdown.expanded :global(a) {
        display: block;
    }

    @media only screen and (max-width: 1000px) {
        #link {
            padding: 0;
        }

        #dropdown {
            position: relative;
            padding: 0 0 0 20px;
            border-top: none;
        }
    }
</style>