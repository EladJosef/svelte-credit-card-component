# Credit Card Svelte Component

## Component explain
A simple credit card component based on svelte freamwork
component support multi issuers (american express, discover, mastercard, visa)

## How to use
```html
<script>
  import CreditCard from "./lib/CreditCard.svelte";

  const card_info = {
    card_number: "4546857415124368",
    holder_name: "Steve Carell",
    expiry_date: "26/01",
    cvv: 412,
  };
</script>

<CreditCard {card_info} />
```

## Result
<img src="https://user-images.githubusercontent.com/25385540/192116257-7672979b-bbd4-4b02-83ec-3b69fc434ab5.gif" width="350" />


