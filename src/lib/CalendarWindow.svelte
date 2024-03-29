<div class="window" on:click={() => expanded = !expanded} class:notCurrent={month != actualMonth} class:today={new Date(year, month, date).setHours(0, 0, 0, 0) == new Date().setHours(0, 0, 0, 0)} class:events={event != ""}>
    <p id="date">{date}</p>
    <p id="event">{event}</p>
</div>

<div id="modalContainer" class:expanded={expanded} on:click={() => {if (!modal.classList.contains("hovered")) expanded = false}}>
    <div id="modal" on:mouseenter={modal.classList.add("hovered")} on:mouseleave={modal.classList.remove("hovered")} bind:this={modal}>
        <div id="close" on:click={() => expanded = false}><img src="/Close.svg" alt=""></div>
        <p id="modalDate">{new Date(year, month, date).toLocaleString("et-EE", { weekday: "long", day: "numeric", month: "long", year: "numeric"}).charAt(0).toUpperCase() + new Date(year, month, date).toLocaleString("et-EE", { weekday: "long", day: "numeric", month: "long", year: "numeric"}).slice(1)}</p>
        <p id="modalTitle">{eventText}</p>
        <p id="modalDescription">{description}</p>
    </div>
</div>

<script>
    export let date;
    export let event;
    export let description;
    export let year;
    export let month;
    export let actualMonth;
    export let id;

    let modal;
    let eventText = event;

    $: if (event == undefined)
        event = "";
    $: if (description == undefined)
        description = "";
    $: if (event == "")
        eventText = "Sündmusi pole";
    else
        eventText = event;
    
    let expanded = false;
</script>

<style>
    .window {
        aspect-ratio: 1 / 1;
        border-radius: 10px;
        border: 1px solid rgba(0,0,0, 0.1);
        background-color: rgb(241, 241, 241);
    }

    .window:hover {
        background-color: rgb(229, 229, 229);
        cursor: pointer;
    }

    .notCurrent {
        visibility: hidden;
    }

    .today {
        border: 1px solid rgb(61, 149, 125);
    }

    #date {
        margin: 0;
        background-color: rgba(0,0,0, 0.05);
        text-align: center;
        color: rgb(51, 51, 51);
        font-size: 16px;
        font-weight: 500;
        border-radius: 7px 7px 0 0;
    }
    
    .events #date {
        background-color: rgb(51, 51, 51);
        color: white;
    }

    .today #date{
        background-color: rgb(61, 149, 125);
        color: white;
    }

    #event {
        margin: 5px;
        color: rgb(51, 51, 51);
        font-size: 11px;
        font-weight: 500;
    }

    #modalContainer {
        z-index: 100;
        position: fixed;
        top: 0;
        left: 0;
        display: none;
        width: 100vw;
        height: 100vh;
    }

    #modalContainer.expanded {
        display: block;
    }

    #modalContainer.expanded #modal {
        animation: pop 0.1s forwards;
    }

    #modal {
        position: relative;
        width: calc(90% - 40px);
        height: 300px;
        max-width: 500px;
        padding: 20px;
        background-color: rgb(241, 241, 241);
        top: 45%;
        left: 50%;
        transform: translate(-50%, -50%);
        border: 1px solid rgba(0,0,0, 0.1);
        border-radius: 10px;
        box-shadow: 0 5px 16px 0 rgba(51, 51, 51, 0.37);
    }

    @keyframes pop {
        0% {
            width: calc(80% - 40px);
            height: 250px;
            opacity: 0;
        }

        100% {
            width: calc(90% - 40px);
            height: 300px;
            opacity: 1;
        }
    }

    #modalDate {
        font-size: 15px;
        margin: 0;
    }

    #modalTitle {
        font-size: 20px;
        font-weight: 500;
        letter-spacing: -0.5px;
        margin: 5px 0;
    }

    #modalDescription {
        font-size: 17px;
        margin: 30px 0;
    }

    #close:hover {
        cursor: pointer;
    }

    #close img {
        position: absolute;
        right: 0;
        width: 20px;
        margin-right: 20px;
        filter: brightness(0);
    }

    @media only screen and (max-width: 1000px) {
        .window:hover {
            background-color: rgb(241, 241, 241);
        }

        .window.today:hover {
            background-color: rgb(61, 149, 125);
        }
        
        #date {
            position: relative;
            height: 100%;
            background-color: transparent;
            border-radius: 7px;
            top: 60%;
            transform: translateY(-50%);
        }

        .events #date {
            background-color: transparent;
            color: black;
        }

        .events.today #date {
            color: white;
        }

        .today #date{
            background-color: transparent;
        }

        .today {
            background-color: rgb(61, 149, 125);
        }

        .events #date::after {
            content: "";
            display: block;
            position: relative;
            width: 5px;
            height: 5px;
            background-color: rgb(61, 149, 125);
            border-radius: 10px;
            left: 50%;
            transform: translateX(-50%);
        }

        .events.today #date::after {
            background-color: rgb(241, 241, 241);
        }

        #event {
            display: none;
        }

        #modal {
            width: 80%;
        }
    }
</style>