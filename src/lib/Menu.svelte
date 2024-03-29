<div id="hamburger" on:click={() => expanded = !expanded} class:expanded="{expanded}">
    <div id="bar1"></div>
    <div id="bar2"></div>
    <div id="bar3"></div>
</div>
<div id="menu" class:expanded="{expanded}">
    <slot />
</div>

<script>
    import { onMount } from "svelte";
    let expanded = false;
    onMount(() => 
        window.navigation.addEventListener('navigate', (event) => {
            expanded = false;
    }));
</script>

<style>
    #menu {
        z-index: 10;
        display: flex;
        flex-direction: row;
        align-items: center;
        height: 70px;
        margin-right: 50px;
    }

    #menu :global(a) {
        margin: 10px;
        color: rgb(61, 149, 125);
        font-size: 16px;
        font-weight: 700;
        letter-spacing: 0.5px;
        text-decoration: none;
        transition-duration: 0.6s;
    }

    #menu :global(a:hover) {
        opacity: 0.7;
    }

    #hamburger {
        display: none;
        margin-right: 15px;
    }

    #bar1, #bar2, #bar3 {
        height: 2px;
        width: 20px;
        margin-bottom: 4px;
        background-color: rgb(61, 149, 125);
    }

    #bar3 {
        margin-bottom: 0;
    }

    @media only screen and (max-width: 1000px) {
        #hamburger {
            display: block;
        }

        #menu {
            position: fixed;
            top: 45px;
            width: 100%;
            height: 0;
            margin: 0;
            padding: 0;
            align-items: start;
            flex-direction: column;
            background-color: white;
            border-top: none;
            box-shadow: 0 5px 16px 0 rgba(51, 51, 51, 0.37);
            overflow-y: hidden;
            transition: height 0.6s ease-in-out;
        }
        
        #menu.expanded {
            height: calc(100vh - 105px);
            padding: 30px 0;
            border-top: 3px solid rgb(61, 149, 125);
            overflow-y: scroll;
        }

        :global(body):has(#menu.expanded) {
            overflow-y: hidden;
        }
        
        #menu :global(a) {
            z-index: 999;
            display: none;
            margin: 13px 30px;
            color: rgb(61, 149, 125);
            font-size: 16px;
            font-weight: 700;
            letter-spacing: 0.5px;
            text-decoration: none;
            transition-duration: 0.6s;
        }
        
        #menu :global(a:hover) {
            opacity: 1;
        }

        #menu.expanded :global(a) {
            display: block;
        }
    }
</style>