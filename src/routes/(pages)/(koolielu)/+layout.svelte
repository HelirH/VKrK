<div id="content">
    <div id="sidebar">
        <a href="/toitlustamine">Toitlustamine</a>
        <a href="/pikapaevaruhm">Pikapäevarühm</a>
        <a href="/koolitervishoid">Koolitervishoid</a>
        <a href="/tervisenoukogu">Tervisenõukogu</a>
        <a href="/projektid">Projektid</a>
        <a href="/ainetepaev">Ainetepäev</a>
        <a href="/almanahh">Almanahh "Lennuk"</a>
        <a href="/kalender">Sündmuste kalender</a>
        <a href="/galerii">Galerii</a>
    </div>
    <div id="wrapper">
        <slot/>
    </div>
</div>

<style>
    #content {
        display: grid;
        grid-template-columns: 4fr 1fr;
        margin-bottom: 60px;
    }

    #sidebar {
        grid-column: 2 / span 1;
        grid-row: 1 / span 1;
        flex: 1;
        position: relative;
        margin: 109px 0 0 0;
    }

    #sidebar a {
        display: block;
        margin-bottom: 2px;
        padding: 10px;
        font-size: 16px;
        font-weight: 500;
        text-align: right;
    }

    #wrapper {
        grid-column: 1 / span 1;
        grid-row: 1 / span 1;
    }

    @media only screen and (max-width: 1000px) {
        #content {
            grid-template-columns: 1fr;
        }
        
        #sidebar {
            display: none;
        }

        #wrapper {
            grid-column: 1 / span 1;
            grid-row: 1 / span 1;
        }
    }
</style>