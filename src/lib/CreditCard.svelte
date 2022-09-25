<script>
    import CardBackground from "./CardBackground.svelte";
    import issuer_data from "../assets/issuer_data.json";

    export let card_info;
    export let settings;

    const color = settings.background_color;

    // credit card titles
    const data_headers = ["Card holder name", "Expiry date", "CVV"];

    function get_issuer_name(card_number) {
        /**
         * fucntion return issuer name by card number
         * @param  {[string]} card_number card number
         */
        let issuer_name = "unknown";
        Object.entries(issuer_data.inn).forEach(([issuer, value]) => {
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
        return issuer_name;
    }

    function format_card_number(card_number) {
        /**
         * fucntion get card number and return formated string of card number
         * by issuer different formating types
         * @param  {[string]} card_number card number
         */
        let card_format = issuer_data.card_format[get_issuer_name(card_number)];
        let card_number_format = "";
        let index = 0;

        card_number = card_number.replace(/[^0-9]/g, "");

        if (!card_format) {
            card_format = issuer_data.card_format.default;
        }

        card_format.forEach((card_index) => {
            card_number_format +=
                card_number.slice(index, index + card_index) + " ";
            index += card_index;
        });

        return card_number_format;
    }
</script>

<div class="card-container">
    <!-- card background -->
    <CardBackground {settings} />
    <div class="card-title">Credit Card</div>

    <div class="card-number">{format_card_number(card_info.card_number)}</div>

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

    <!-- card issusr logo -->
    <img
        src="{get_issuer_name(card_info.card_number)}.svg"
        alt=""
        class="credit-card-logo {get_issuer_name(card_info.card_number)}"
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

    .diners-club {
        top: 95px;
        width: 130px;
        left: 340px;
    }

    .jcb {
        top: 80px;
        width: 70px;
        left: 400px;
    }
</style>
