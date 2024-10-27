# llm_bots
bots for messagers with LLM (by ollama)


```markdown
# LLM Bots

This repository contains a Telegram bot that leverages the Ollama AI model to intelligently respond to user queries and extract content from web pages. The bot is designed to facilitate knowledge sharing by summarizing articles and providing informative responses.

## Features

- **URL Content Extraction:** Extracts and summarizes the main text content from web pages.
- **Intelligent Responses:** Utilizes the Ollama AI model to generate human-like responses to user inquiries.
- **Multi-Language Support:** Responds to queries in the language they are asked.

## Prerequisites

Before you begin, ensure you have the following installed:

- **Python 3.7 or higher**
- **Telegram Bot Token:** Obtain your token from [BotFather](https://core.telegram.org/bots#botfather).
- **Ollama API access**

## Installation

Follow these steps to set up the project:

1. **Clone the repository:**
   ```bash
   git clone git@github.com:vsobolev/llm_bots.git
   cd llm_bots
   ```

2. **Install the required packages:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configuration:**
   - Open the script and replace `'your_token_by_botfather'` with your actual Telegram bot token.
   - Set the desired Ollama (recommended model) here: https://ollama.com/.

## Usage

To run the bot, execute the following command:

```bash
python telegrambot_llm.py
```

### Interaction

- **Extract Content:** Send a message containing a URL to the bot, and it will extract and summarize the content from that page.
- **Ask Questions:** Type any question or statement, and the bot will respond with relevant information.

### Example Interactions

1. **Extracting Content from a URL:**
   - **User:** `https://example.com/article`
   - **Bot:** *Extracts and summarizes the content from the provided URL.*

2. **General Knowledge Inquiry:**
   - **User:** `Что такое искусственный интеллект?`
   - **Bot:** *Provides an informative response based on the question asked.*

## Logging

The bot utilizes Python's logging module to log messages for debugging purposes. You can adjust the logging level in the code as needed.

## License

This project is licensed under the GNU License.

## Contributing

Contributions are welcome! If you have suggestions for improvements or want to add features, feel free to submit issues or pull requests.

## Contact

For questions or feedback, please reach out to me on [GitHub](https://github.com/vsobolev).
```
