<script>
  import CreditCard from "./lib/CreditCard.svelte";

  const card_info = {
    card_number: "",
    holder_name: "",
    expiry_date: "",
    cvv: null,
  };

  const settings = {
    background_color: "#222222",
  };
</script>

<main>
  <h1 class="title">Credit Card Svelte Component</h1>
  <CreditCard {card_info} {settings} />
  <div class="card-form">
    <label for="">Card Number</label>
    <input type="text" bind:value={card_info.card_number} maxlength="16" />
    <label for="">Name</label>
    <input type="text" bind:value={card_info.holder_name} />
    <label for="">Date</label>
    <input type="month" bind:value={card_info.expiry_date} />
    <label for="">CVV</label>
    <input type="number" bind:value={card_info.cvv} min="100" max="9999" />
  </div>
  <a
    href="https://github.com/EladJosef/svelte-credit-card-component"
    class="hint">This is an open source project</a
  >
</main>

<style>
  @import url("https://fonts.googleapis.com/css2?family=Montserrat:wght@300;700&display=swap");

  main {
    text-align: center;
  }

  .title {
    font-size: 70px;
    font-family: "Montserrat", sans-serif;
    color: #222222;
  }

  .card-form {
    padding-top: 50px;
  }

  input[type="text"],
  input[type="number"],
  input[type="month"] {
    width: 500px;
    height: 40px;
    padding: 12px 20px;
    margin: 8px 0;
    display: inline-block;
    border: 1px solid rgba(0, 0, 0, 0);
    border-radius: 13px;
    box-sizing: border-box;
  }

  label {
    font-family: "Montserrat", sans-serif;
    font-size: 20px;
    color: #222222;
    display: block;
  }

  .hint {
    position: relative;
    top: 30px;
  }
</style>
