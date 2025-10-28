# Crypto Wallet UI

## Опис проєкту

Crypto Wallet UI - це простий та елегантний інтерфейс криптовалютного гаманця, розроблений за допомогою HTML та CSS. Проєкт демонструє базовий дизайн для мультивалютного гаманця з підтримкою Ethereum (ETH), ERC20 токенів та Bitcoin (BTC).

### Особливості:

- **Мультивалютна підтримка**: Вкладки для ETH, ERC20 та BTC
- **Відображення балансу**: Показує поточний баланс гаманця
- **Інформація про акаунт**: Відображає адресу гаманця
- **Форма відправки**: Інтерфейс для відправки криптовалюти
- **Адаптивний дизайн**: Темна тема з фоновим зображенням
- **Чистий UI**: Мінімалістичний та зрозумілий інтерфейс

### Технічний стек:

- **HTML5**: Структура сторінки
- **CSS3**: Стилізація та дизайн
- **Responsive Design**: Адаптивні елементи

## Розробник

**Сергій Щербаков**
- GitHub: [@sergiyscherbakov](https://github.com/sergiyscherbakov)
- Email: sergiyscherbakov@ukr.net
- Telegram: [@s_help_2010](https://t.me/s_help_2010)

## Структура проєкту

```
crypto-wallet-ui/
├── Index.html          # Головна HTML сторінка
├── styles.css          # Стилі для інтерфейсу
├── images/             # Папка з зображеннями
│   ├── img001.jpg      # Фонове зображення
│   └── 1.jpg           # Додаткове зображення
└── README.md           # Документація проєкту
```

## Швидкий старт

### Крок 1: Клонування репозиторію

```bash
git clone https://github.com/sergiyscherbakov/crypto-wallet-ui.git
cd crypto-wallet-ui
```

### Крок 2: Додавання зображень

Оскільки зображення не включені в репозиторій (через .gitignore), вам потрібно додати власне фонове зображення:

1. Створіть папку `images/`
2. Додайте фонове зображення `img001.jpg`

Або змініть шлях до зображення у файлі `styles.css`:

```css
background-image: url('path/to/your/image.jpg');
```

### Крок 3: Відкриття у браузері

Просто відкрийте файл `Index.html` у вашому браузері:

```bash
# Windows
start Index.html

# macOS
open Index.html

# Linux
xdg-open Index.html
```

Або використайте Live Server для розробки:

```bash
# Встановіть Live Server глобально (якщо ще не встановлено)
npm install -g live-server

# Запустіть сервер
live-server
```

## Опис інтерфейсу

### Верхня панель (Header)

Містить вкладки для переключення між різними типами гаманців:
- **ETH** - Ethereum гаманець (активна за замовчуванням)
- **ERC20** - Токени стандарту ERC20
- **BTC** - Bitcoin гаманець

### Основна секція гаманця

#### Інформація про гаманець:
- **Назва**: Ethereum
- **Баланс**: 4.250 ETH
- **Адреса акаунта**: `0xC8BfA7c694b8c21Cdc87242d1931FC58606d1d`

#### Форма відправки (Send):
- **Receiver**: Поле для введення адреси отримувача
- **Amount**: Поле для введення суми
- **Send Button**: Кнопка для відправки транзакції

## Стилізація

### Кольорова схема:

- **Фон**: `#1c1c1c` (темно-сірий)
- **Основний контейнер**: `#3d1c56` (фіолетовий)
- **Вкладки**: `#5c2e7e` (світло-фіолетовий)
- **Активна вкладка**: `#8a6eb7` (яскраво-фіолетовий)
- **Текст**: `#ffffff` (білий)

### CSS особливості:

```css
/* Фонове зображення на весь екран */
background-size: cover;
background-repeat: no-repeat;

/* Центрування контейнера */
display: flex;
flex-direction: column;
align-items: center;

/* Прозора кнопка */
background-color: rgba(255, 255, 255, 0.2);
```

## Розширення функціоналу

Цей UI можна розширити, додавши JavaScript функціонал:

### 1. Інтеграція з Web3.js

```javascript
// Підключення до MetaMask
if (typeof window.ethereum !== 'undefined') {
  const web3 = new Web3(window.ethereum);
  // Запит доступу до акаунтів
  await ethereum.request({ method: 'eth_requestAccounts' });
}
```

### 2. Відображення реального балансу

```javascript
// Отримання балансу
const balance = await web3.eth.getBalance(account);
const ethBalance = web3.utils.fromWei(balance, 'ether');
```

### 3. Відправка транзакцій

```javascript
// Відправка ETH
await web3.eth.sendTransaction({
  from: senderAddress,
  to: receiverAddress,
  value: web3.utils.toWei(amount, 'ether')
});
```

### 4. Переключення між гаманцями

```javascript
// Обробка кліків по вкладках
document.querySelectorAll('.wallet-name').forEach(tab => {
  tab.addEventListener('click', function() {
    // Видалити active з усіх
    document.querySelectorAll('.wallet-name').forEach(t =>
      t.classList.remove('active')
    );
    // Додати active до поточної
    this.classList.add('active');

    // Завантажити дані відповідного гаманця
    loadWalletData(this.textContent);
  });
});
```

## Рекомендовані покращення

### Функціональні:

1. **JavaScript інтеграція**:
   - Підключення до MetaMask або інших Web3 гаманців
   - Відображення реального балансу
   - Відправка транзакцій
   - Історія транзакцій

2. **Валідація форм**:
   - Перевірка адреси отримувача
   - Перевірка суми (достатність балансу)
   - Відображення помилок

3. **Додаткові функції**:
   - QR код для адреси
   - Копіювання адреси в буфер обміну
   - Конвертація валют (ETH → USD)
   - Графіки балансу

### Дизайн:

1. **Адаптивність**:
   - Підтримка мобільних пристроїв
   - Різні розміри екранів

2. **Анімації**:
   - Плавне переключення вкладок
   - Hover ефекти
   - Transitions для кнопок

3. **Покращення UX**:
   - Підказки (tooltips)
   - Індикатори завантаження
   - Повідомлення про успіх/помилку
   - Підтвердження транзакцій

## Приклади використання

### Сценарій 1: Перегляд балансу

1. Відкрити Index.html у браузері
2. Переглянути баланс ETH гаманця
3. Переключитися на вкладку ERC20/BTC для перегляду інших балансів

### Сценарій 2: Відправка коштів (UI демонстрація)

1. Ввести адресу отримувача у поле "Receiver"
2. Ввести суму у поле "Amount"
3. Натиснути кнопку "Send"
4. (Для повної функціональності потрібна інтеграція з Web3)

## Інтеграція з блокчейном

### Необхідні бібліотеки:

```html
<!-- Web3.js -->
<script src="https://cdn.jsdelivr.net/npm/web3@latest/dist/web3.min.js"></script>

<!-- Ethers.js (альтернатива) -->
<script src="https://cdn.ethers.io/lib/ethers-5.2.umd.min.js"></script>
```

### Приклад структури JavaScript файлу:

```javascript
// wallet.js
class CryptoWallet {
  constructor() {
    this.web3 = null;
    this.account = null;
    this.init();
  }

  async init() {
    // Ініціалізація Web3
    if (typeof window.ethereum !== 'undefined') {
      this.web3 = new Web3(window.ethereum);
      await this.connectWallet();
    } else {
      alert('Please install MetaMask!');
    }
  }

  async connectWallet() {
    const accounts = await ethereum.request({
      method: 'eth_requestAccounts'
    });
    this.account = accounts[0];
    await this.updateBalance();
  }

  async updateBalance() {
    const balance = await this.web3.eth.getBalance(this.account);
    const ethBalance = this.web3.utils.fromWei(balance, 'ether');
    document.querySelector('.wallet-info p').textContent =
      `Balance: ${parseFloat(ethBalance).toFixed(4)} ETH`;
  }

  async sendTransaction(to, amount) {
    try {
      await this.web3.eth.sendTransaction({
        from: this.account,
        to: to,
        value: this.web3.utils.toWei(amount, 'ether')
      });
      alert('Transaction successful!');
      await this.updateBalance();
    } catch (error) {
      alert('Transaction failed: ' + error.message);
    }
  }
}

// Ініціалізація при завантаженні сторінки
window.addEventListener('load', () => {
  const wallet = new CryptoWallet();

  // Обробка кнопки відправки
  document.querySelector('.send-button').addEventListener('click', async () => {
    const receiver = document.querySelector('input[placeholder="Receiver"]').value;
    const amount = document.querySelector('input[placeholder="Amount"]').value;

    if (receiver && amount) {
      await wallet.sendTransaction(receiver, amount);
    } else {
      alert('Please fill in all fields');
    }
  });
});
```

## Безпека

### Важливі зауваження:

1. **Ніколи не зберігайте приватні ключі у frontend коді**
2. **Використовуйте HTTPS** для production
3. **Валідуйте всі вхідні дані** на стороні клієнта та сервера
4. **Використовуйте перевірені бібліотеки** (Web3.js, Ethers.js)
5. **Попереджайте користувачів** перед відправкою транзакцій

### Рекомендації:

- Показувати підтвердження перед відправкою коштів
- Відображати gas fee перед транзакцією
- Перевіряти network (mainnet/testnet)
- Використовувати checksums для адрес

## Тестування

### Тестові мережі:

- **Sepolia**: Ethereum тестова мережа
- **Goerli**: Ethereum тестова мережа (застаріла)
- **Mumbai**: Polygon тестова мережа

### Отримання тестових токенів:

- Sepolia Faucet: https://sepoliafaucet.com/
- Goerli Faucet: https://goerlifaucet.com/

## Ліцензія

MIT License

## Контакти

Якщо у вас виникли питання або пропозиції:
- Email: sergiyscherbakov@ukr.net
- GitHub: https://github.com/sergiyscherbakov/crypto-wallet-ui
- Telegram: [@s_help_2010](https://t.me/s_help_2010)

## Додаткові ресурси

- [Web3.js Documentation](https://web3js.readthedocs.io/)
- [Ethers.js Documentation](https://docs.ethers.org/)
- [MetaMask Documentation](https://docs.metamask.io/)
- [Ethereum Developer Resources](https://ethereum.org/en/developers/)
- [HTML5 Documentation](https://developer.mozilla.org/en-US/docs/Web/HTML)
- [CSS3 Documentation](https://developer.mozilla.org/en-US/docs/Web/CSS)

---

**Дата створення**: 28 жовтня 2025
**Версія**: 1.0.0 (UI Only)
**Статус**: Демонстраційний прототип
