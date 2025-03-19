
# 🍎 Fruit Match Game 🍓

Welcome to the **Fruit Match Game**! 🍍 In this interactive game, you flip cards to match pairs of fruits. 🍌

## 🎮 How the Game Works:

- The game starts with a grid of face-down cards, each showing a fruit on the back (🍎, 🍓, 🍍, etc.).
- You can click on the cards to flip them over and reveal the fruit.
- If two cards match (showing the same fruit), they remain face-up. 🍇🍍
- If the cards don't match, they will flip back after a short delay, and you can try again! 🍊
- The game continues until all pairs of fruits have been matched and the cards are all face-up. 🍏

## 🍓 Code Breakdown:

### 1. **HTML Structure**:
The HTML contains a container `div` with an ID of `app`, where all the cards are dynamically added. Each card has two sides: a front side (`.front`) and a back side (`.back`) displaying the fruit.

### 2. **Variables**:
```javascript
let templateHTML = '';
let ArrayCard = [];
let ArrayFruit = [];
const btn = document.getElementById('btn');
let listFruit = ['🍓', '🍌', '🍎', '🍇', '🍎', '🍍', '🍓', '🍉', '🍉', '🍇', '🍌', '🍍'];
```
- `templateHTML`: Stores the HTML for all the cards.
- `ArrayCard`: An array to track the flipped cards.
- `ArrayFruit`: An array to track the fruits displayed on the flipped cards.
- `btn`: The button element that shuffles the cards.
- `listFruit`: The list of fruits shown on the cards.

### 3. **Generating Cards**:
```javascript
listFruit.forEach(fruit => {
    templateHTML += \`
    <div class="card">
        <div class="sides front"></div>
        <div class="sides back">${fruit}</div>
    </div>
    \`;
});
app.innerHTML = templateHTML;
```
- This code creates the cards by looping through the `listFruit` array. For each fruit, a card is created with a front and back side.

### 4. **Card Flipping Mechanism**:
```javascript
app.addEventListener('click', (e) => {
    let value = e.target.matches('.front');
    if (value && ArrayCard.length <= 2) {
        let ElementCard = e.target.parentElement;
        let fruit = ElementCard.children[1].textContent;
        ElementCard.classList.add('rotate');
        ArrayCard = [...ArrayCard, ElementCard];
        ArrayFruit = [...ArrayFruit, fruit];
        VerificationsCards();
    }
});
```
- When a card is clicked, it flips over if it’s not already face-up. The fruit is recorded in the `ArrayFruit`, and the card is added to `ArrayCard`.
- After flipping two cards, the function `VerificationsCards()` is called to check if they match.

### 5. **Card Match Verification**:
```javascript
const VerificationsCards = () => {
    if (ArrayCard.length > 1) {
        if (ArrayFruit[0] === ArrayFruit[1]) {
            ArrayCard = "";
            ArrayFruit = "";
        } else {
            setTimeout(() => {
                ArrayCard[0].classList.remove('rotate');
                ArrayCard[1].classList.remove('rotate');
                ArrayCard = "";
                ArrayFruit = "";
            }, 800);
        }
    }
};
```
- If two cards show the same fruit, they remain flipped.
- If they don’t match, they will flip back after 800 milliseconds.

### 6. **Shuffle Button**:
```javascript
const ramdon = () => {
    for (let index = app.children.length; index >= 0; index--) {
        app.appendChild(app.children[(Math.random() * index) | 0]);
    }
};
btn.addEventListener('click', () => {
    ramdon();
    for (let index of cards) {
        index.classList.remove('rotate');
    }
});
```
- The shuffle button randomizes the positions of the cards on the screen.
- After shuffling, all the cards are reset to face down.

## 🍊 Conclusion:

The game continues until all fruit pairs are matched! 🍏 The goal is to memorize the fruit locations and match them as fast as possible. 🍎 Have fun playing and challenge your memory skills! 🧠

# Have you questions? Please write me at:

## koding@duck.com ☻