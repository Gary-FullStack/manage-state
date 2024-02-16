Managing state in a component refers to the process of storing and updating data within that component. State allows a component to keep track of information that can change over time, such as user input, API responses, or the current state of a UI element.


This react app is a small demo showing usage of state.



1. **State Initialization**: The `useState` hook is used to initialize the state of the gift card. The state is an object that contains the following properties: `firstName`, `lastName`, `text`, `valid`, and `instructions`.

```javascript
const [giftCard, setGiftCard] = useState(
  {
    firstName: "Bob",
    lastName: "Smiff",
    text: "Free oil and filter change.",
    valid: true,
    instructions: "To use your coupon, click the button below.",
  }
);
```

2. **State Update Function**: The `spendGiftCard` function is defined to update the state of the gift card. It uses the `setGiftCard` function (returned by `useState`) to update the state. The new state is based on the previous state (`prevState`), but with the `text`, `valid`, and `instructions` properties updated.

```javascript
function spendGiftCard() {
  setGiftCard(prevState => {
    return {
      ...prevState,
      text: "Your coupon has been used.",
      valid: false,
      instructions: "Please visit our car clinic to renew your gift card.",
    }
  });
}
```

3. **Rendering**: The component renders a `div` that displays the gift card information. It uses the properties of the `giftCard` state to display the customer's name, the text of the gift card, and the instructions. If the gift card is valid (`giftCard.valid` is `true`), it also displays a "Spend Gift Card" button. When this button is clicked, it calls the `spendGiftCard` function, which updates the state of the gift card.

```javascript
return (
  <div style={{padding: '40px'}}>
    <h1>
      Free Gift Page
    </h1>
    <h2>
      Customer: {giftCard.firstName} {giftCard.lastName}
    </h2>
    <h3>
      {giftCard.text}
    </h3>
    <p>
      {giftCard.instructions}
    </p>
    {
      giftCard.valid && (
        <button onClick={spendGiftCard}>
          Spend Gift Card
        </button>
      )
    }
  </div>
);
```

In summary, this component manages the state of a gift card, allowing the user to "spend" the gift card by clicking a button, which updates the state and re-renders the component with the updated state.