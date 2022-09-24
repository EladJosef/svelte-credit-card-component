<script>
    import card from "../assets/card.svg";

    export let card_info;

    const data_headers = ["Card holder name", "Expiry date", "CVV"];

    const inn_data = {
        "american-express": [34, 37],
        discover: [
            6011,
            [622126, 622925],
            [624000, 626999],
            [628200, 628899],
            64,
            65,
        ],
        mastercard: [[2221, 2720], 51, 55],
        visa: [4],
    };

    function get_card_issuer(card_number) {
        let issuer_name = "unknown";
        Object.entries(inn_data).forEach(([issuer, value]) => {
            value.forEach((inn) => {
                if (typeof inn == "number") {
                    if (card_number.slice(0, `${inn}`.length) == inn) {
                        issuer_name = issuer;
                    }
                } else {
                    for (let i = inn[0]; i < inn[1] + 1; i++) {
                        if (card_number.slice(0, `${i}`.length) == i) {
                            issuer_name = issuer;
                        }
                    }
                }
            });
        });
        console.log(issuer_name);
        return issuer_name;
    }

    function format_card_number(card_number) {
        return (
            card_number.slice(0, 4) +
            " " +
            card_number.slice(4, 8) +
            " " +
            card_number.slice(8, 12) +
            " " +
            card_number.slice(12, 16)
        );
    }
</script>

<div class="card-container">
    <img src={card} class="card svelte" alt="credit card" />
    <div class="card-number">{format_card_number(card_info.card_number)}</div>
    <div class="card-title">Credit Card</div>
    <div class="card-holder-name">
        <div class="card-header">{data_headers[0]}</div>
        <div class="card-info">{card_info.holder_name}</div>
    </div>
    <div class="expiry-date">
        <div class="card-header">{data_headers[1]}</div>
        <div class="card-info">{card_info.expiry_date}</div>
    </div>
    <div class="cvv">
        <div class="card-header">{data_headers[2]}</div>
        <div class="card-info">{card_info.cvv}</div>
    </div>
    <img
        src="{get_card_issuer(card_info.card_number)}.svg"
        alt=""
        class="credit-card-logo {get_card_issuer(card_info.card_number)}"
    />
</div>

<style>
    @import url("https://fonts.googleapis.com/css2?family=Inconsolata&family=Montserrat:wght@300;700&display=swap");

    @font-face {
        font-family: CC;
        src: url("../assets/cc.woff2") format("woff2");
    }

    .card-container {
        position: relative;
        display: inline-block;
        color: rgb(255, 255, 255);
        user-select: none;
    }

    img {
        -webkit-user-drag: none;
    }

    .card {
        height: 20em;
    }

    .card-number {
        position: absolute;
        font-family: "CC";
        font-size: 31px;
        top: 180px;
        left: 40px;
    }

    .card-title {
        font-family: "Montserrat", sans-serif;
        position: absolute;
        font-weight: 700;
        top: 40px;
        left: 40px;
    }

    .card-holder-name {
        font-family: "Montserrat", sans-serif;
        position: absolute;
        top: 240px;
        left: 40px;
    }

    .expiry-date {
        font-family: "Montserrat", sans-serif;
        position: absolute;
        top: 240px;
        left: 320px;
    }

    .cvv {
        font-family: "Montserrat", sans-serif;
        position: absolute;
        top: 240px;
        left: 425px;
    }

    .card-header {
        font-size: 10px;
        text-align: left;
    }

    .card-info {
        font-size: 20px;
        text-align: left;
        text-transform: capitalize;
    }

    .credit-card-logo {
        position: absolute;
    }

    .american-express {
        top: 80px;
        width: 60px;
        left: 410px;
    }

    .discover {
        top: 35px;
        width: 150px;
        left: 320px;
    }

    .mastercard {
        top: 85px;
        width: 60px;
        left: 400px;
    }

    .visa {
        top: 95px;
        width: 90px;
        left: 380px;
    }
</style>
