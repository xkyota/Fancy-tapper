# Tapper Game

Welcome to **Tapper**, a fun and interactive game where you can earn virtual currency by tapping and spend it on exciting upgrades for your GTR!  

## Features

- **Tap to Earn**: Click the tap button to earn virtual currency.
- **Timer and Cooldown**: Play within a time limit and wait for cooldowns to restart.
- **Shop Upgrades**: Spend your earnings on GTR performance upgrades.
- **Dynamic UI**: Interactive cards for purchasing items.

## Cards Database

The game includes the following upgrade options:

| Poster                     | Title                  | Price  | Button Text   |
|----------------------------|------------------------|--------|---------------|
| `/images/performance-exhaust.png` | GTR Performance       | $1200  | Upgrade Now   |
| `/images/turbocharger-kit.png`    | GTR Turbocharger Kit  | $3500  | Boost Now     |
| `/images/suspension-kit.png`      | GTR Suspension Kit    | $800   | Install Now   |
| `/images/ecu-tuning.png`          | GTR ECU Tuning        | $600   | Tune Now      |

## How It Works

1. **Start Tapping**:  
    - Click the tap button to earn $5 per click.  
    - The timer starts when you first tap.  

2. **Timer and Cooldown**:  
    - You have 100 seconds to tap and earn.  
    - After the timer ends, wait for a cooldown period before restarting.  

3. **Shop for Upgrades**:  
    - Use your balance to purchase upgrades from the shop.  
    - Insufficient balance? Keep tapping to earn more!  

4. **Interactive UI**:  
    - Cards dynamically update and disappear upon purchase.  

## Code Highlights

### Card Template Generator
```javascript
function cardTemplate(card) { 
     return `<div class="card">
                     <img src="${card.poster}" alt="${card.title}" class="card-poster">
                     <h2 class="card-title">${card.title}</h2>
                     <p class="card-price">${card.price}</p>
                     <button class="card-btn">${card.buttonText}</button>
                </div>`;
}
```

### Timer and Cooldown Logic
```javascript
function startTimer() {
     canClick = true;
     const interval = setInterval(() => {
          if (timerCnt > 0) {
                timer.textContent = `You have ${timerCnt} sec`; 
                timerCnt--; 
          } else {
                clearInterval(interval);
                canClick = false;
                timer.textContent = "Time's up! Wait for cooldown.";
                startCooldown();
          }
     }, 1000);
}
```

### Purchase Functionality
```javascript
container.addEventListener('click', function (event) {
     if (event.target.classList.contains('card-btn')) {
          const cardElement = event.target.closest('.card');
          const cardTitle = cardElement.querySelector('.card-title').textContent;
          const cardPrice = parseInt(cardElement.querySelector('.card-price').textContent.replace('$', ''), 10);

          if (userBalance >= cardPrice) {
                userBalance -= cardPrice;
                balance.textContent = `${userBalance}$`;
                alert(`You successfully purchased: ${cardTitle}`);
                cardElement.remove(); 
          } else {
                alert(`Insufficient balance to purchase: ${cardTitle}`);
          }
     }
});
```

## How to Run

1. Clone the repository to your local machine.
2. Open the `index.html` file in your browser.
3. Start tapping and enjoy the game!

## Future Enhancements

- Add more GTR upgrades.
- Implement a leaderboard for competitive tapping.
- Introduce animations and sound effects.

Enjoy the game and happy tapping!  