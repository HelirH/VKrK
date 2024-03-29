<div id="image" on:mouseenter={cover.style.backgroundSize = `${w + 40}px`} on:mouseleave={cover.style.backgroundSize = `${w}px`} on:click={() => open()}>
    <img id="measure" style="display: none;" src="{coverSrc}" alt="" bind:naturalWidth={nw} bind:naturalHeight={nh}>

    <div class="cover" style="background-image: url({coverSrc});" bind:clientWidth={cw} bind:clientHeight={ch} bind:this={cover}></div>
</div>

<div id="large" class:large={large} bind:this={modal}>
    <div id="close" on:click={() => large = false}><img src="/Close.svg" alt=""></div>
    <div id="prev" bind:this={prevArrow} on:click={() => prev()}><img src="/Previous.svg" alt=""></div>
    <div id="next" bind:this={nextArrow} on:click={() => next()}><img src="/Next.svg" alt=""></div>
    <img id="largeImage" src="{coverSrc}" alt="" bind:naturalWidth={nw} bind:naturalHeight={nh}>
    <div id="description">
        <p>{description}</p>
    </div>
</div>

<script>
    import { onMount } from "svelte";

    export let coverSrc;
    export let title;
    export let description;
    export let id;
    export let openImg;

    let loaded = false;
    let cover;
    let large = false;
    let modal;

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

        if (id == 0) {
            prevArrow.style.display = "none";
        }

        if (id == 8) {
            nextArrow.style.display = "none";
        }
        if (openImg == id) {
            large = true;
        }
    }

    function open() {
        large = true;
        openImg = id;
    }

    function prev() {
        openImg--;
        large = false;
    }

    function next() {
        openImg++;
        large = false;
    }

    let prevArrow;
    let nextArrow;
</script>

<style>
    #image:hover {
        cursor: pointer;
    }

    .cover {
        padding-top: 100%;
        background-position-x: center;
        background-position-y: center;
        border-radius: 10px;
        transition: 0.3s;
    }

    #image:hover .cover {
        filter: brightness(120%) saturate(90%);
    }

    #title {
        width: 100%;
        margin: 5px 0 0 0;
        font-size: 22.4px;
    }

    #large {
        display: none;
    }

    #large.large {
        z-index: 100;
        display: block;
        position: fixed;
        width: 100vw;
        height: 100vh;
        top: 0;
        left: 50%;
        transform: translateX(-50%);
        background-color: rgba(51, 51, 51, 0.8);
    }

    #largeImage {
        position: relative;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        max-width: 80vw;
        max-height: 80vh;
    }

    #close {
        position: fixed;
        top: 20px;
        right: 20px;
        color: white;
        transition: 0.3s;
    }

    #close:hover {
        cursor: pointer;
    }

    #close img {
        width: 50px;
        transform: rotateZ(0deg);
        transition: 0.3s;
    }

    #close:hover img {
        transform: rotateZ(90deg);
    }

    #prev {
        position: fixed;
        top: 50%;
        left: 0;
        transform: translateY(-50%);
        color: white;
    }

    #prev:hover {
        cursor: pointer;
    }

    #prev img {
        position: relative;
        left: 30px;
        width: 40px;
        transition: 0.3s;
    }

    #prev:hover img {
        left: 20px;
    }

    #next {
        position: fixed;
        top: 50%;
        right: 0;
        transform: translateY(-50%);
        color: white;
    }

    #next:hover {
        cursor: pointer;
    }

    #next img {
        position: relative;
        right: 30px;
        width: 40px;
        transition: 0.3s;
    }

    #next:hover img {
        right: 20px;
    }

    #description {
        position: fixed;
        bottom: 0;
        width: 80%;
        height: 150px;
        padding: 0 10%;
        margin: 0;
        background: linear-gradient(0deg, rgba(0, 0, 0, 0.8) 40%, rgba(0, 0, 0, 0.5) 70%, transparent);
    }

    #description p {
        position: relative;
        top: 50%;
        right: 0;
        transform: translateY(-50%);
        color: white;
        font-size: 22.4px;
        text-align: center;
    }

    @media only screen and (max-width: 1000px) {
        #prev {
            top: 75%;
            left: calc(50% - 90px);
            transform: translate(-50%, -50%);
        }

        #next {
            top: 75%;
            right: calc(50% - 110px);
            transform: translate(-50%, -50%);
        }

        #close img {
            width: 40px;
        }

        #prev img {
            width: 30px;
        }

        #next img {
            width: 30px;
        }
    }
</style>