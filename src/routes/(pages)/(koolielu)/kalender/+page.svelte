<script>
    import CalendarWindow from "$lib/CalendarWindow.svelte";

    var month = new Date().toLocaleDateString("est-et", {month: "numeric"}) - 1;
    var year = new Date().getFullYear();

    var events = {
        "01.01.2024": "Koolivaheaeg",
        "02.01.2024": "Koolivaheaeg",
        "03.01.2024": "Koolivaheaeg",
        "04.01.2024": "Koolivaheaeg",
        "05.01.2024": "Koolivaheaeg",
        "06.01.2024": "Koolivaheaeg",
        "12.01.2024": "Kreutzwaldi nädal ja kooli sünnipäev",
        "02.02.2024": "5. klasside poole põhikooli läbimise tähistamine",
        "05.02.2024": "Avatud uste päev aulas",
        "12.02.2024": "1.-3. klasside sportlikud pärastlõunad",
        "13.02.2024": "1.-3. klasside sportlikud pärastlõunad",
        "15.02.2024": "Suusaõhtud Haanjas (6. ja 8. klassid)",
        "23.02.2024": "EV aastapäeva aktused ja Ruslan ning Rute Trochynsky kontsert \"Muusikaga vabaks Eesti ja Ukraina moodi\"",
    };

    function prevMonth() {month--; if(month == -1) {month = 11; year--;}}

    function nextMonth() {month++;}
</script>

<div id="titleContainer">
    <p>KALENDER</p>
</div>
<div id="calendar">
    <div id="calendarHeader">
        <p id="prevMonth" on:click={prevMonth}>4</p>
        <p class="calendarMonth">{new Date(year, month, 1).toLocaleString('est-et', { month: 'long', year: 'numeric'})}</p>
        <p id="nextMonth" on:click={nextMonth}>5</p>
    </div>
    <div id="calendarBody">
        <p class="day">E</p>
        <p class="day">T</p>
        <p class="day">K</p>
        <p class="day">N</p>
        <p class="day">R</p>
        <p class="day">L</p>
        <p class="day">P</p>
        {#each Array.from(Array(new Date(year, month, 0).getDate() - new Date(year, month, 0).getDay() + 36).keys()).slice(new Date(year, month, 0).getDate() - new Date(year, month, 0).getDay() + 1) as i } 
            <CalendarWindow 
                date={new Date(year, month - 1, i).getDate()} 
                event={events[new Date(year, month - 1, i).toLocaleDateString("est-et", {month: "2-digit", day: "2-digit", year: "numeric"})]} 
                description={events[new Date(year, month - 1, i).toLocaleDateString("est-et", {month: "2-digit", day: "2-digit", year: "numeric"})]} 
                year={year} 
                month={month % 12} 
                actualMonth={new Date(year, month - 1, i).getMonth()}
                id={i - new Date(year, month, 0).getDate() - 1}></CalendarWindow>
        {/each}
    </div>
</div>

<style>
    #calendarBody {
        display: grid;
        grid-template-columns: repeat(7, calc((100% - 60px) / 7));
        grid-template-rows: 30px repeat(5, 1fr);
        grid-gap: 10px;
    }

    #calendarHeader {
        display: flex;
        justify-content: center;
        align-items: center;
        margin-bottom: 30px;
    }

    #prevMonth {
        margin: 30px 0 10px 0;
        color: rgba(0, 0, 0, 0.6);
        font-family: 'eleganticons';
        font-size: 22px;
        text-align: center;
        font-weight: 600;
    }

    #nextMonth {
        margin: 30px 0 10px 0;
        color: rgba(0, 0, 0, 0.6);
        font-family: 'eleganticons';
        font-size: 22px;
        text-align: center;
        font-weight: 600;
    }

    #prevMonth:hover, #nextMonth:hover {
        cursor: pointer;
    }

    .calendarMonth {
        margin: 30px 50px 10px 50px;
        color: rgb(51, 51, 51);
        font-size: 22px;
        text-align: center;
        font-weight: 300;
        text-transform: uppercase;
    }

    .day {
        color: rgb(51, 51, 51);
        margin: 0;
        font-size: 16px;
        text-align: center;
        font-weight: 700;
    }

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

    @media only screen and (max-width: 1000px) {
    }
</style>