<script>
    import { onMount } from "svelte";

    import Image from "$lib/Image.svelte";

    let albumName;

    onMount(() => {
        albumName = decodeURI(window.location.href.split("/")[window.location.href.split("/").length - 1]);
    })

    let openImg = -1;
</script>

<div id="titleContainer">
    <p>GALERII / {albumName}</p>
</div>

<div id="album">
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/1700/1500"} description={"Lorem ipsum dolor sit amet"} id={0} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={1} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={2} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={3} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={4} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={5} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={6} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={7} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={8} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/1700/1500"} description={"Lorem ipsum dolor sit amet"} id={9} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={10} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={11} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={12} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={13} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={14} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={15} bind:openImg={openImg}></Image>
    <Image coverSrc={"https://picsum.photos/id/" + Math.floor(Math.random() * 700) + "/700/500"} description={""} id={16} bind:openImg={openImg}></Image>
</div>

<style>
    #titleContainer {
        width: 100%;
        margin-bottom: 20px;
        border-bottom: 1px solid rgb(209, 219, 151);
    }

    #titleContainer p {
        margin-bottom: 10px;
        color: rgb(70, 88, 85);
        font-size: 40px;
        font-weight: 300;
        line-height: 1.2em;
    }

    #album {
        display: grid;
        grid-template-columns: repeat(4, minmax(0, 1fr));
        @media only screen and (max-width: 1000px) {
            grid-template-columns: repeat(3, minmax(0, 1fr));
        }
        @media only screen and (max-width: 700px) {
            grid-template-columns: repeat(2, minmax(0, 1fr));
        }
        @media only screen and (max-width: 500px) {
            grid-template-columns: minmax(0, 1fr);
        }
        grid-gap: 20px;
    }

    img {
        width: 100%;
        margin: 0 0 20px;
    }

    .button {
        display: block;
        height: fit-content;
        width: fit-content;
        padding: 7px 15px;
        margin: 30px 0;
        background-color: rgb(61, 149, 125);
        color: white;
        font-size: 16px;
        font-weight: 500;
        text-decoration: none;
    }
</style>