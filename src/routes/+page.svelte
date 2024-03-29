<script>
    import Event from "$lib/Event.svelte";
</script>

<div id="content">
    <div class="columnItem">
        <div class="news">
            <ul id="news">
                <h2 id="uudised">UUDISED</h2>
                <li>
                    <a class="newsLink" href="https://vkrk.edu.ee/tundide-ajad/">OLULINE INFO!</a>
                    <p class="newsBrief">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Etiam consectetur eu urna ac imperdiet. Praesent nec turpis at ligula fringilla eleifend vel at mauris. Suspendisse egestas iaculis efficitur. Donec sagittis dolor sed rutrum accumsan. Sed scelerisque et eros nec ullamcorper. Praesent euismod arcu sed malesuada imperdiet. Aliquam elementum porta auctor. Donec id elit dolor. Fusce a orci euismod, accumsan lacus id, imperdiet magna. Sed gravida ex eu massa semper cursus.</p>
                    <p class="newsDate">12.10.2023</p>
                </li>
                <li>
                    <a class="newsLink" href="https://vkrk.edu.ee/tundide-ajad/">EUROOPA KEELTE PÄEVA VIKTORIIN</a>
                    <p class="newsBrief">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Duis nec ante dictum, faucibus orci ac, vulputate erat. Pellentesque maximus neque diam, a maximus dui convallis eget. Suspendisse potenti. Donec maximus ullamcorper neque, sit amet ornare massa. Mauris et tincidunt orci. Class aptent taciti sociosqu ad litora torquent per conubia nostra, per inceptos himenaeos. Aenean sollicitudin vulputate risus ac tempus. Donec euismod semper est, nec hendrerit ipsum tincidunt vitae. Phasellus eu erat sit amet est pellentesque lacinia. Nunc ac mollis mi. Sed fringilla velit et justo rutrum faucibus sed a tellus.</p>
                    <p class="newsDate">12.10.2023</p>
                </li>
                <li>
                    <a class="newsLink" href="https://vkrk.edu.ee/tundide-ajad/">UURIMISTÖÖ “KES ELAVAD TIIGIS?”</a>
                    <p class="newsBrief">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Vestibulum rutrum nunc egestas nulla aliquet ultrices eu non nunc. Duis facilisis feugiat elit, vel tincidunt purus fermentum eget. Pellentesque sollicitudin neque eu neque aliquet accumsan. Vestibulum eu velit sit amet lacus interdum placerat et at libero. Sed mattis diam eget risus sollicitudin fringilla. Morbi venenatis gravida placerat. Quisque nec nibh in felis condimentum ultricies. Donec velit nisi, mattis a malesuada pharetra, dapibus quis tellus. Etiam nisl quam, faucibus at justo vitae, lobortis vulputate eros. Sed id metus ut ante faucibus imperdiet in nec turpis.</p>
                    <p class="newsDate">9.10.2023</p>
                </li>
                <li>
                    <a class="newsLink" href="https://vkrk.edu.ee/tundide-ajad/">RAHVATANTSU INFO</a>
                    <p class="newsBrief">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Ut aliquam in lacus vitae condimentum. Praesent accumsan felis id tincidunt malesuada. Maecenas nec tellus in felis rutrum vulputate id eu mi. Suspendisse metus diam, ornare eget auctor ac, vestibulum at lacus. Proin eget odio feugiat, dignissim justo eu, vulputate quam. Curabitur ullamcorper nisi ut turpis pellentesque tristique. Proin suscipit, eros rutrum semper tincidunt, justo tellus sodales dolor, a interdum purus mauris et tortor. Duis finibus diam neque, ut ornare urna mattis a. Cras consequat libero eget mi elementum, ac egestas risus luctus. Integer eu velit massa. Nullam cursus augue nec vulputate euismod.</p>
                    <p class="newsDate">3.10.2023</p>
                </li>
                <li>
                    <a class="newsLink" href="https://vkrk.edu.ee/tundide-ajad/">STUUDIUMISSE SISENEMISE JUHEND</a>
                    <p class="newsBrief">Lorem ipsum dolor sit amet, consectetur adipiscing elit. Aenean ut metus non sem faucibus consectetur et sed arcu. Integer ullamcorper elit sed dui scelerisque hendrerit. Maecenas faucibus, leo vel bibendum aliquet, erat eros faucibus urna, sed tincidunt diam ipsum sit amet orci. Nulla pharetra felis eu mollis eleifend. Integer sit amet lectus interdum, consectetur quam ac, dignissim arcu. Mauris ac felis at ligula porta ullamcorper quis a erat. Pellentesque ac augue commodo, tincidunt velit vitae, consequat eros. Maecenas id magna nec est mattis dapibus quis non lectus.</p>
                    <p class="newsDate">30.08.2023</p>
                </li>
            </ul>
            <a class="more" href="/uudised">Kõik uudised</a>
        </div>
    </div>
    <div class="columnItem">
        
        <div class="events">
            <h2 id="sündmused">SÜNDMUSED</h2>
            <div class="eventsContainer">
                <Event date={"23. okt. 2023"} title={"Koolivaheaeg"} time={"Koolivaheaeg"}/>
                <Event date={"22. okt. 2023"} title={"Sündmus1"} time={"Sündmus1 kell 11.00 Aulas"}/>
                <Event date={"25. nov. 2023"} title={"Sündmus2"} time={"Sündmus2  kell 17.30 Koolimajas"}/>
                <Event date={"26. dets. 2023"} title={"Sündmus3"} time={"Sündmus3 kell 14.00."}/>
                <Event date={"27. dets. 2023"} title={"Sündmus4"} time={"Sündmus4 kell 13.00."}/>
            </div>
            <a class="more" href="/kalender">Kõik sündmused</a>
        </div>
    </div>
</div>

<style>
    #content {
        display: grid;
        grid-template-columns: 1fr 300px;
        grid-column-gap: 40px;
        height: fit-content;
        margin-bottom: 60px;
    }

    .columnItem ul {
        list-style: none;
        margin-bottom: 40px;
        padding: 0;
    }

    .columnItem li {
        text-indent: -10px;
        margin: 30px 0;
    }

    #sündmused {
        text-align: left;
    }

    #news {
        margin: 0 0 20px 0;
    }

    #news li {
        margin-top: 40px;
    }

    #news li:first-of-type {
        margin-top: 0;
    }

    .newsLink {
        margin: 10px;
        font-size: 24px;
        font-weight: 600;
        letter-spacing: -0.5px;
    }

    .newsBrief {
        margin: 30px 0 0 0;
        max-width: 800px;
        color: rgb(51, 51, 51);
        font-size: 100%;
        font-weight: 500;
        line-height: 1.4em;
        letter-spacing: 0.5px;
        text-decoration: none;
        text-indent: 0px;
    }

    .newsDate {
        margin: 10px;
        color: rgb(102, 102, 102);
        font-size: 100%;
        font-weight: 500;
        line-height: 1.4em;
        letter-spacing: 0.5px;
        text-decoration: none;
    }

    .button {
        padding: 10px 15px;
        background-color: rgb(61, 149, 125);
        color: white;
        font-size: 16px;
        font-weight: 500;
        text-decoration: none;
    }

    .more {
        display: block;
        width: 100%;
        color: rgb(61, 149, 125);
        font-size: 16px;
        font-weight: 500;
        text-decoration: none;
        text-align: center;
    }

    .more::after {
        content: "3";
        font-family: 'eleganticons';
    }

    .events {
        position: sticky;
        top: 30px;
        margin: 0 0 40px 0;
    }

    .eventsContainer {
        display: grid;
        grid-template-rows: auto;
        row-gap: 30px;
        margin-bottom: 30px;
    }

    img {
        margin: 30px 0;
    }

    @media only screen and (max-width: 1000px) {
        #content {
            grid-template-columns: 1fr;
        }

        #sündmused {
            text-align: center;
        }

        .more {
            margin-bottom: 30px;
        }
    }
</style>