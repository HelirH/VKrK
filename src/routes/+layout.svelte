<script>
    import { page } from '$app/stores';
    import { onMount } from 'svelte';
    
    import Menu from "$lib/Menu.svelte";
    import Dropdown from "$lib/Dropdown.svelte";

    let href;
    let loaded;

    onMount(async () => {
        loaded = true;
	});

    $: if (loaded) {
        href = $page.url.pathname;
        if (href == "/") {
            navbar.style.maxWidth = "100%";
        } else {
            navbar.style.maxWidth = "1300px";
        }
    }

    let innerWidth;

    $: if (loaded) {
        for (let i = 0; i < document.getElementsByClassName("dropdown").length; i++) {
            document.getElementsByClassName("dropdown")[i].addEventListener('click', function(event) {
                if (innerWidth <= 1000) {
                    event.preventDefault();
                }
            });
        }
    }

    let navbar;
</script>

<svelte:window bind:innerWidth/>

<main>
    <div id="navbar" bind:this={navbar}>
        <img src="\voru-kreutzwaldi-kooli-logo.svg" id="logo" onclick="window.location.href='/'">
        <Menu>
            <Dropdown>
                <span slot="link">
                    <a href="/oppetoo" class="dropdown">Õppetöö</a>
                </span>
                <span slot="dropdown">
                    {#if innerWidth <= 1000}
                        <a href="/oppetoo" class="link">Õppetöö</a>
                    {/if}
                    <a href="/tunniplaan" class="link">Tunniplaan</a>
                    <a href="/tundideajad" class="link">Tundide ajad</a>
                    <a href="/trimestridvaheajad" class="link">Trimestrite ja koolivaheaegade ajad</a>
                    <a href="/eksamidtasemetood" class="link">Eksamid ja tasemetööd</a>
                    <a href="/konsultatsioonjarelvastamine" class="link">Konsultatsioon ja järelvastamine</a>
                    <a href="/olumpiaadidvoistlused" class="dropdown">Olümpiaadid ja võistlused</a>
                    <a href="/raamatukogu" class="link">Raamatukogu</a>
                    <a href="https://kreutzwaldi.ope.ee/" class="link">Stuudium</a>
                </span>
            </Dropdown>
            <Dropdown>
                <span slot="link">
                    <a href="/koolielu" class="dropdown">Koolielu</a>
                </span>
                <span slot="dropdown">
                    {#if innerWidth <= 1000}
                        <a href="/koolielu" class="link">Koolielu</a>
                    {/if}
                    <a href="/toitlustamine" class="link">Toitlustamine</a>
                    <a href="/pikapaevaruhm" class="link">Pikapäevarühm</a>
                    <a href="/koolitervishoid" class="link">Koolitervishoid</a>
                    <a href="/tervisenoukogu" class="link">Tervisenõukogu</a>
                    <a href="/projektid" class="link">Projektid</a>
                    <a href="/ainetepaev" class="link">Ainetepäev</a>
                    <a href="/almanahh" class="link">Almanahh "Lennuk"</a>
                    <a href="/kalender" class="link">Sündmuste kalender</a>
                    <a href="/galerii" class="link">Galerii</a>
                </span>
            </Dropdown>
            <Dropdown>
                <span slot="link">
                    <a href="/koolist" class="dropdown">Koolist</a>
                </span>
                <span slot="dropdown">
                    {#if innerWidth <= 1000}
                        <a href="/koolist" class="link">Koolist</a>
                    {/if}
                    <a href="/pohimotted" class="link">Põhimõtted</a>
                    <a href="/ajalugu" class="link">Ajalugu</a>
                    <a href="/fond" class="link">Võru Kreutzwaldi Kooli Fond</a>
                    <a href="/toetajad" class="link">Toetajad</a>
                </span>
            </Dropdown>
            <a href="/dokumendid" class="link">Dokumenid</a>
            <a href="/kontakt" class="link">Kontakt</a>
            <div id="searchBar">
                <input type="text" name="searchBar">
                <a>&#x55;</a>
            </div>
        </Menu>
    </div>

    {#if href == "/"}
        <div id="heroSection">
            <div id="bgImage">
                <div id="quoteContainer">
                    <p id="quote">Ülemaks kui hõbevara, kallimaks kui kullakoormad tuleb tarkus tunnistada.</p>
                    <p id="quoteSignature">Fr. R. Kreutzwald “Kalevipoeg”</p>
                </div>
                <p id="allkiri">Illustratsioon pilteeposest <big>„Kalevipoeg”</big></p>
            </div>
        </div>
    {/if}

    <div id="content">

    
        <slot />
    </div>
    
    <div id="footer">
        <div id="footerGrid">
            <div class="footerColumn">
                <p><strong>Võru Kreutzwaldi Kool</strong></p>
                <p>Kooli 7, 65606 Võru</p>
            </div>
            <div class="footerColumn">
                <p>Rg-kood: 75039014</p>
                <p>E-post: kool@vkrk.edu.ee</p>
                <p>Telefon: +372 782 8100</p>
                <p>Konto: EE031010220239533228 SEB</p>
            </div>
        </div>
    </div>
</main>

<style>
    main {
        display: flex;
        min-height: 100vh;
        width: 100%;
        align-items: center;
        flex-direction: column;
    }

    .dropdown::after {
        content: "3";
        margin-left: 5px;
        font-family: 'eleganticons';
        font-weight: 500;
        text-decoration: none;
    }

    #content {
        position: relative;
        width: 90%;
        max-width: 1200px;
    }

    #logo {
        position: relative;
        margin-left: 50px;
        cursor: pointer;
    }

    #navbar {
        display: flex;
        align-items: center;
        justify-content: space-between;
        width: 100%;
        height: 70px;
        background-color: rgb(255, 255, 255);
    }

    #searchBar {
        position: relative;
        display: flex;
        width: 25px;
        margin-left: 10px;
        align-items: center;
        justify-content: right;
        transition: 0.3s;
    }

    #searchBar:hover, #searchBar:has(input:focus) {
        width: 210px;
    }

    #searchBar a {
        display: inline-block;
        font-family: 'eleganticons'; 
        transform: scaleX(-1);
    }

    #searchBar input{
        position: absolute;
        height: 25px;
        width: 25px;
        right: 3px;
        border: 1px rgb(61, 149, 125) solid;
        border-radius: 50px;
        opacity: 0;
        color: rgb(51, 51, 51);
        font-weight: 300;
        padding: 0 5px;
        transition: width 0.3s;
    }

    #searchBar:hover input, #searchBar input:focus {
        width: 205px;
        opacity: 1;
    }

    #searchBar input:focus {
        border: 2px rgb(39, 118, 75) solid;
        outline: none;
    }

    #heroSection {
        position: relative;
        height: calc(75vh - 74px);
        min-height: 200px;
        width: 100%;
        margin-bottom: 60px;
    }

    #bgImage {
        position: relative;
        width: 100%;
        height: 100%;
        background-image: url("/avalehe_bg_2-1280x408-transformed-HEHi2Kwkf-transformed.jpeg");
        background-repeat: no-repeat;
        background-size: cover;
        background-position: center;
        border-bottom: 4px solid rgb(209, 219, 151);
    }

    #quoteContainer {
        position: absolute;
        top: 50%;
        left: 50%;
        -ms-transform: translate(-50%, -50%);
        transform: translate(-50%, -50%);
        padding: 30px;
        background-color: rgba(255, 255, 255, 0.01);
        border-radius: 10px;
        backdrop-filter: blur(5px) brightness(110%) contrast(90%);
        box-shadow: 0 1px 16px 0 rgba(51, 51, 51, 0.37);
    }

    #quote {
        margin: 10px 0 20px;
        width: 700px;
        color: rgb(0, 0, 0);
        font-size: 40px;
        font-weight: 500;
        line-height: 1.4em;
        letter-spacing: -2px;
    }

    #quote::before {
        content: "\e06a";
        position: relative;
        top: 15px;
        float: left;
        margin-right: 10px;
        color: rgb(61, 149, 125);
        font-family: 'eleganticons';
        font-size: 80px;
        font-weight: 500;
        line-height: 80px;
        background-color: rgba(255, 255, 255, 0.3);
        border-radius: 100%;
    }

    #quoteSignature {
        color: rgb(51, 51, 51);
        font-size: 20px;
        font-weight: 500;
        line-height: 1.4em;
        text-decoration: none;
    }

    #allkiri {
        position: absolute;
        bottom: 10px;
        right: 0;
        width: 482px;
        padding-left: 20px;
        background-color: rgba(255, 255, 255, 0.6);
        color: rgb(70, 88, 85);
        font-size: 18px;
        text-align: left;
        line-height: 2.2em;
    }

    #allkiri big {
        font-size: 30px;
    }

    #footer {
        z-index: -1;
        position: relative;
        flex-grow: 1;
        bottom: 0;
        width: 100%;
        height: fit-content;
        box-sizing: border-box;
        padding: 25px 10%;
        background-color: rgb(61, 149, 125);
        border-top: 5px solid rgb(209, 219, 151);
    }

    #footerGrid {
        position: relative;
        display: grid;
        grid-template-columns: 1fr 2fr;
        grid-column-gap: 40px;
        left: 50%;
        -webkit-transform: translateX(-50%);
        -ms-transform: translateX(-50%);
        transform: translateX(-50%);
        max-width: 1100px;
    }

    .footerColumn p {
        margin: 0;
        font-size: 14px;
        font-weight: 500;
        line-height: 22.4px;
        color: white;
    }

    @media only screen and (max-width: 1000px) {
        #logo {
            height: 35px;
            margin-left: 15px;
        }
        
        #navbar {
            height: 45px;
        }

        #searchBar {
            order: -1;
            display: block;
            margin: 0 0 13px 30px;
            width: calc(100% - 60px);
        }

        #searchBar input {
            position: relative;
            width: 100%;
            left: 0;
            opacity: 1;
            background-color: rgb(230, 230, 230);
            border: none;
            transition: none;
        }

        #searchBar input:focus {
            width: 100%;
        }

        #searchBar:hover, #searchBar:has(input:focus) {
            width: calc(100% - 60px);
        }

        #searchBar a {
            display: block;
            position: absolute;
            right: 0;
            top: 0;
            margin: 5px 0 5px 5px;
        }

        #heroSection {
            height: calc(40vh - 74px);
            margin-bottom: 30px;
        }

        #quoteContainer {
            padding: 15px;
        }

        #quote {
            margin: 5px 0 10px;
            width: calc(100vw - 100px);
            max-width: 300px;
            font-size: 20px;
        }

        #quote::before {
            top: 5px;
            font-size: 40px;
            line-height: 40px;
        }

        #quoteSignature {
            font-size: 10px;
        }

        #allkiri {
            display: none;
        }

        #footerGrid {
            grid-template-columns: 1fr;
        }

        .footerColumn {
            margin-bottom: 30px;
        }
    }
</style>