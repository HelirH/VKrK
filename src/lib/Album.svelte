<div id="album" on:mouseenter={cover.style.backgroundSize = `${w + 40}px`} on:mouseleave={cover.style.backgroundSize = `${w}px`} on:click={() => window.location.href = "galerii/Kreutzwaldi päev"}>
    <img id="measure" style="display: none;" src="{coverSrc}" alt="" bind:naturalWidth={nw} bind:naturalHeight={nh}>

    <div class="cover" style="background-image: url({coverSrc});" bind:clientWidth={cw} bind:clientHeight={ch} bind:this={cover}></div>
    <p id="title">{title}</p>
    <p id="images">{images} pilti</p>
</div>

<script>
    import { onMount } from "svelte";

    export let coverSrc;
    export let title;
    export let images;

    let loaded = false;
    let cover;

    onMount(() => {
        loaded = true;

        if(nw > nh) {
            h = ch;
            w = h * (nw / nh);
        }
        else {
            w = cw;
            h = w * (nh / nw);
        }
        cover.style.backgroundSize = w + "px";
    })

    let cw;
    let ch;
    let nw;
    let nh;

    let w;
    let h;

    $: if (loaded) {
        if(nw > nh) {
            h = ch;
            w = h * (nw / nh);
        }
        else {
            w = cw;
            h = w * (nh / nw);
        }
        cover.style.backgroundSize = w + "px";
    }
</script>

<style>
    #album:hover {
        cursor: pointer;
    }

    .cover {
        padding-top: 100%;
        background-position-x: center;
        background-position-y: center;
        border-radius: 10px;
        transition: 0.3s;
    }

    #album:hover .cover {
        filter: brightness(120%) saturate(90%);
    }

    #title {
        width: 100%;
        margin: 5px 0 0 0;
        font-size: 22.4px;
    }

    #images {
        width: 100%;
        margin: 0;
        font-size: 16px;
    }
</style>