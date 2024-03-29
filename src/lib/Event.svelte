<div class="event">
    <div class="eventDate">{date}</div>
    <p class="eventTitle">{title}</p>
    <p class="eventTime">{time}</p>
    <a class="eventLink" href="/kalender">Ava kalendris</a>
</div>

<script>
    export let date;
    export let title;
    export let time;
</script>

<style>
    .event {
        position: relative;
    }

    .eventDate {
        position: relative;
        width: fit-content;
        padding: 7px 10px;
        background-color: rgb(209, 219, 151);
        font-size: 14.4px;
        font-weight: 700;
        letter-spacing: 0.5px;
    }

    .eventDate::before {
        content: "";
        display: block;
        position: absolute;
        bottom: 0;
        left: 0;
        width: 300px;
        border-bottom: 1px solid rgb(209, 219, 151);
    }

    .eventTitle {
        margin-top: 25px;
        font-size: 16px;
        font-weight: 700;
        letter-spacing: 0.5px;
        line-height: 0;
    }

    .eventTime {
        margin: 15px 0 10px 0;
        font-size: 13.44px;
        font-weight: 500;
        letter-spacing: 0.5px;
        text-wrap: wrap;
    }

    .eventLink {
        display: block;
        margin-bottom: 0;
        font-size: 13.44px;
        font-weight: 500;
        letter-spacing: 0.5px;
        line-height: 1.5em;
    }

    @media only screen and (max-width: 1000px) {
        .eventDate::before {
            width: 90vw;
        }
    }
</style>