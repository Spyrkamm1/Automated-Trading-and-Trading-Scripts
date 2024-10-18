
# Automated Trading Bot with Webhook and Screen Monitoring

![License](https://img.shields.io/github/license/your-username/trading-bot) ![Version](https://img.shields.io/badge/version-1.0-blue) ![Sponsors](https://img.shields.io/badge/sponsors-welcome-orange)

Welcome to the **Automated Trading Bot** repository! This project integrates trading automation with webhooks, screen monitoring via OCR, and efficient trade execution using Python. The bot is designed to facilitate seamless market entry and exit actions for traders, providing real-time decision making with high accuracy. All actions, including order placement, confirmation, and error handling, are automated.

## 🧑‍💻 Project Overview

The trading bot is triggered by webhooks that contain buy or sell instructions, executes trades through a simulated or real trading interface, and verifies that orders are filled by watching the screen for visual confirmation (using [Tesseract OCR](https://github.com/tesseract-ocr/tesseract)).

This repository includes:
- **Automated click handling** to perform trades based on webhook instructions.
- **Position management** to handle opening and closing trades with minimal user interaction.
- **Screen monitoring** using OCR to confirm order fills.
- **Error handling and restart mechanisms** to ensure the bot runs continuously.
- **Flask-based webhook service** to handle incoming trade signals.

By sharing this project, I aim to improve the automation of trading workflows and create a space for future contributions and sponsorships.

## 🛠️ Key Features

- **Webhook-Based Trade Execution**: Handles incoming trade signals through HTTP POST requests to a Flask API.
- **Position Management**: Automatically manages opening and closing positions, ensuring that no duplicate trades are made when already in a position.
- **OCR Order Confirmation**: Uses Tesseract OCR to read screen output and confirm successful order fills.
- **Efficient Error Handling**: Restarts the bot upon critical errors and logs detailed information for troubleshooting.
- **Prevents Double Orders**: Built-in logic to avoid double-clicks or placing the same order multiple times.

## 💡 How It Works

1. **Webhook Service**: The bot listens for HTTP POST requests containing trade instructions (`buy` or `sell`) via the `/webhook` endpoint.
   
2. **Position Closing**: If a position is already open (e.g., a buy order), the bot will close it before placing the opposite side order (sell order).

3. **Order Placement**: Once the position is closed, the bot simulates a mouse click at predefined screen coordinates to place a new buy or sell order.
   
4. **Order Fill Verification**: The bot takes screenshots of the order status area and uses Tesseract OCR to detect order status messages such as "filled" or "executed." This ensures that the trade was processed successfully.

5. **Resting Position**: After placing an order, the bot moves the mouse to a predefined "resting" position to avoid accidental clicks or interference with other screen elements.

## 🖥️ System Requirements

- **Operating System**: Windows 10 (or higher) / Linux / macOS
- **Python Version**: 3.8 or higher
- **Dependencies**:
  - `Flask`: For handling incoming webhook requests
  - `pyautogui`: For simulating mouse clicks
  - `pytesseract`: For OCR-based screen monitoring
  - `Pillow`: For capturing screen images
  - `Tesseract-OCR`: Installed locally on your machine for screen reading

## 🔧 Setup Instructions

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/trading-bot.git
cd trading-bot
```

### 2. Install Dependencies

Make sure to install the required Python libraries:

```bash
pip install -r requirements.txt
```

### 3. Configure Tesseract Path (Windows Only)

If you are using Windows, ensure that the correct path to `Tesseract-OCR` is set in the script (`pytesseract.pytesseract.tesseract_cmd`). You can download it [here](https://github.com/tesseract-ocr/tesseract).

### 4. Set Up Flask Webhook Service

To run the webhook service:

```bash
python app.py
```

The server will be running at `http://localhost:3000/`.

### 5. Test the Webhook

To test a buy or sell action, you can use `curl` or Postman to send a POST request to the `/webhook` endpoint:

```bash
curl -X POST http://localhost:3000/webhook -H "Content-Type: application/json" -d '{"action": "buy"}'
```

The bot will attempt to place a buy order after receiving the request.

### 6. Monitor Logs

The bot outputs detailed logs to help you understand what actions it is taking. These logs include information about orders being placed, positions being closed, and order fills being confirmed.

```bash
tail -f app.log
```

## 🚀 Future Enhancements

I am constantly looking for ways to improve this project, and there are several enhancements that could be made, such as:
- **Integration with Real Trading Platforms**: Adding support for brokers or APIs such as Alpaca or Binance.
- **More Advanced Order Fill Confirmation**: Expanding the order fill detection to work with a wider range of platforms.
- **GUI Control Panel**: Building a graphical interface to manually control and monitor the bot.

## 🏅 Sponsors & Support

If you find this project useful, please consider sponsoring its continued development. Your support helps in adding more features, improving stability, and providing updates for various platforms.

[Sponsor this project](https://github.com/sponsors/spyrkamm1)

## 📜 License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.

## 🤝 Contributing

Contributions are welcome! If you want to contribute, please open an issue or submit a pull request. Be sure to follow the guidelines provided in [CONTRIBUTING.md](CONTRIBUTING.md).

## 📧 Contact

If you have any questions or suggestions, feel free to reach out:

- GitHub Issues: [Report Issues](https://github.com/your-username/trading-bot/issues)
- Email: matthewspyrka@gmail.com

---

Thank you for checking out the **Automated Trading Bot** project! If you like this project, give it a ⭐ on GitHub and share it with others.

---

### 📋 Changelog
- **v1.0**: Initial release with basic buy/sell functionality and OCR-based order fill verification.

---

_This project is maintained and developed by [Your Name]._

---

### Contributions

The bot is designed to automate trading workflows, and its modular architecture makes it suitable for integration with more complex trading strategies. We are actively seeking collaborators and sponsors to help improve and expand the system.

---

Feel free to copy and paste this README into your GitHub repository. It provides a detailed overview, clear instructions, and conveys a professional tone to attract interest and support from the developer and trading communities.
