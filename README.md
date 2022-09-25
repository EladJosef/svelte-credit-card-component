# Credit Card Svelte Component

<img src="https://raw.githubusercontent.com/EladJosef/svelte-credit-card-component/96cd899a2a21725c8eb48fb158eb541f693353d8/public/banner.svg" width="550" />

## Component explain
A simple credit card component based on svelte freamwork
component support multi issuers (american express, discover, mastercard, visa, jcb, diners-club)
check the web demo at https://svelte-credit-card-component.web.app/

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

  const settings = {
    background_color: "#222222",
  };
</script>

<CreditCard {card_info} {settings} />
```

## Result
<img src="https://user-images.githubusercontent.com/25385540/192116257-7672979b-bbd4-4b02-83ec-3b69fc434ab5.gif" width="350" />

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details
