<div id="content">
    <div id="sidebar">
        <a href="/tunniplaan">Tunniplaan</a>
        <a href="/tundideajad">Tundide ajad</a>
        <a href="/trimestridkoolivaheajad">Trimestrite ja koolivaheaegade ajad</a>
        <a href="/eksamidjareltood">Eksamid ja tasemetööd</a>
        <a href="/konsultatsioonjarelvastamine">Konsultatsioon ja järelvastamine</a>
        <a href="/olumpiaadidvoistlused">Olümpiaadid ja võistlused</a>
        <a href="/raamatukogu">Raamatukogu</a>
        <a href="/https://kreutzwaldi.ope.ee/">Stuudium</a>
    </div>
    <div id="wrapper">
        <slot/>
    </div>
</div>

<style>
    #content {
        display: grid;
        grid-template-columns: 4fr 1fr;
        grid-template-rows: 1fr;
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