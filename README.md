# Telegram Grocery Assistant

An intelligent Telegram bot powered by n8n workflows and Google Gemini AI that helps you track and query your grocery purchases through receipt analysis.

## 🌟 Features

- **📸 Receipt Processing**: Upload photos, PDFs, or screenshots of grocery receipts
- **🤖 AI-Powered Analysis**: Uses Google Gemini AI for OCR and data extraction
- **💬 Natural Language Queries**: Ask questions like "How much did I spend at Kaufland last month?" or "What were my most expensive purchases?"
- **📊 Smart Categorization**: Automatically categorizes items and handles complex receipt layouts
- **🔍 Advanced Search**: Filter by store, category, price range, date, and more
- **📱 Telegram Integration**: Seamless chat interface with HTML-formatted responses
- **🗄️ Database Storage**: Persistent storage of purchase records and receipt data
- **🔄 Workflow Automation**: Fully automated n8n workflows for processing and analysis

## 🏗️ Architecture

### Core Workflows

- **`telegram-grocery-main-flow.json`**: Main orchestration workflow handling Telegram messages, OCR processing, and AI responses
- **`telegram-grocery-database-query.json`**: Database operations for storing and retrieving purchase data
- **`telegram-grocery-receipt-lookup.json`**: Receipt-specific queries and image retrieval
- **`telegram-grocery-vector-search.json`**: Similarity search for finding related purchases
- **`telegram-grocery-nearby-offers.json`**: Location-based offer suggestions
- **`telegram-grocery-show-receipt.json`**: Receipt image display functionality

### AI Components

- **OCR Engine**: `models/gemini-3.1-flash-lite-preview` for high-precision receipt transcription
- **Data Extraction**: `models/gemini-3.1-pro-preview` for structured data parsing from receipts
- **AI Agent**: Conversational interface with tool integration for natural language queries

### Tool Ecosystem

The AI agent uses specialized tools for different query types:

- **Database Query Tool**: Filter and search purchase records by store, category, price, date
- **Receipt Lookup Tool**: Find specific receipts and purchase events
- **Similarity Search Tool**: Find related or similar purchases
- **Nearby Offers Tool**: Location-based shopping suggestions
- **Receipt Image Tool**: Retrieve and display receipt images

## �️ Workflow Previews

Explore the visual workflows on n8n's sharing platform:

- **[Main Flow](https://share-n8n.com/shared/X2t4oiJmW6hz)** - Complete orchestration workflow handling Telegram messages, OCR processing, and AI responses
- **[Nearby Offers](https://share-n8n.com/shared/WlRh5D6ilvyk)** - Location-based shopping suggestions workflow
- **[Database Query](https://share-n8n.com/shared/Dk4KthiObBtH)** - Database operations for storing and retrieving purchase data
- **[Receipt Lookup](https://share-n8n.com/shared/AtXmM0OBZGob)** - Receipt-specific queries and image retrieval
- **[Vector Search](https://share-n8n.com/shared/TEQRE4I4V6Af)** - Similarity search for finding related purchases
- **[Show Receipt](https://share-n8n.com/shared/CZHX9eQ5VHFM)** - Receipt image display functionality

*Note: All workflows can be previewed and shared via [share-n8n.com](https://share-n8n.com/). Individual workflow links may vary - check the latest shared versions.*

## �🚀 Quick Start

### Prerequisites

- [n8n](https://n8n.io/) instance (self-hosted or cloud)
- Google Gemini API key
- Telegram Bot Token
- Database connection (PostgreSQL/MySQL recommended)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/telegram-grocery-assistant.git
   cd telegram-grocery-assistant
   ```

2. **Import workflows into n8n**
   - Open your n8n instance
   - Import each JSON file from the `workflows/` directory
   - Import prompts from the `prompts/` directory

3. **Configure credentials**
   - Set up Google Gemini API credentials in n8n
   - Configure Telegram bot token
   - Set up database connection credentials
   - Configure any external service URLs (PDF conversion, etc.)

4. **Activate workflows**
   - Enable all imported workflows
   - Set up webhooks for Telegram integration

## 📖 Usage

### For Users

1. **Start a chat** with your Telegram bot
2. **Upload receipts** by sending photos, PDFs, or screenshots
3. **Ask questions** like:
   - "How much did I spend at Lidl last month?"
   - "Show me all my bakery purchases"
   - "What were my most expensive items?"
   - "Find receipts from Kaufland"

### Supported Categories

- Fruits & Vegetables
- Bakery
- Dairy & Eggs
- Meat
- Cold Cuts & Fish
- Beverages
- Pantry & Dry Goods
- Frozen & Chilled
- Sweets & Snacks
- Breakfast & Spreads
- Household & Personal Care
- Pet Food
- Organic & Health
- International
- Pfand & Deposits
- Discounts

## 📁 Project Structure

```
telegram-grocery-assistant/
├── workflows/                    # n8n workflow definitions
│   ├── telegram-grocery-main-flow.json
│   ├── telegram-grocery-database-query.json
│   ├── telegram-grocery-receipt-lookup.json
│   ├── telegram-grocery-vector-search.json
│   ├── telegram-grocery-nearby-offers.json
│   └── telegram-grocery-show-receipt.json
├── prompts/                      # AI model prompts and configurations
│   ├── ai-agent-system.json      # Main AI agent instructions
│   ├── ocr-prompt.json          # Receipt OCR configuration
│   ├── payload-extraction-prompt.json
│   └── tools/                    # Tool definitions
│       ├── database-query-tool.json
│       ├── receipt-lookup-tool.json
│       ├── similarity-search-tool.json
│       ├── nearby-offers-tool.json
│       └── get-receipt-image-tool.json
├── docs/                         # Generated documentation
├── generate-n8n-svg.js          # Workflow diagram generator
├── .github/workflows/           # CI/CD workflows
│   └── generate-diagrams.yml
├── LICENSE                       # GPL-3.0 license
└── README.md                     # This file
```

## 🔧 Configuration

### Environment Variables

Set these in your n8n instance:

- `GOOGLE_GEMINI_API_KEY`: Your Google Gemini API key
- `TELEGRAM_BOT_TOKEN`: Telegram bot token from @BotFather
- `DATABASE_URL`: Database connection string
- `PDF_CONVERSION_URL`: External PDF to image service URL

### Model Configuration

- **OCR Model**: `gemini-3.1-flash-lite-preview` (cost-effective, fast)
- **Extraction Model**: `gemini-3.1-pro-preview` (high accuracy, structured output)
- **Agent Model**: `gemini-3.1-pro-preview` (conversational, tool usage)

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Test workflows thoroughly before committing
- Update prompts and documentation for any changes
- Ensure all credentials are properly secured
- Follow n8n best practices for workflow design

## 📄 License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- [n8n](https://n8n.io/) - The workflow automation platform
- [Google Gemini](https://ai.google.dev/) - AI models for OCR and analysis
- [Telegram](https://telegram.org/) - Bot platform and API

## 📞 Support

If you encounter issues:

1. Check the n8n workflow logs
2. Verify API credentials and connections
3. Test individual workflow components
4. Review the prompts for any configuration issues

For questions or contributions, please open an issue on GitHub.