<script>
    import Album from "$lib/Album.svelte";
</script>

<div id="titleContainer">
    <p>GALERII</p>
</div>

<div id="gallery">
    <Album coverSrc={"/avalehe_bg_2-1280x408.jpg"} title={"Kreutzwaldi päev"} images={17}></Album>
    <Album coverSrc={"/voru-kreutzwaldi-kooli-toitlustamine-230518-480x720.jpg"} title={"Tervisliku toitumise loeng"} images={23}></Album>
    <Album coverSrc={"/voru-kreutzwaldi-kooli-raamatukogu-230518-980x419.jpg"} title={"1. - 3. klasside huvipäev"} images={7}></Album>
    <Album coverSrc={"/projektid-230525-980x476.jpg"} title={"Koolidevaheline koostöökohtumine"} images={15}></Album>
    <Album coverSrc={"/oppetoo-230516-980x419.jpg"} title={"Ainetepäev"} images={31}></Album>
    <Album coverSrc={"/kreutzwaldi-kool-230524-980x419.jpg"} title={"1. september"} images={83}></Album>
    <Album coverSrc={"/fotod-videod-230523-980x419.jpg"} title={"Kooli sünnipäev"} images={42}></Album>
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

    #gallery {
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