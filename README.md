# E-commerce AI Agent.

An intelligent AI agent that answers questions about e-commerce data using natural language processing and SQL query generation.

## 🚀 Features

- **Natural Language Processing**: Ask questions in plain English
- **Automatic SQL Generation**: Converts questions to SQL queries using Gemini 2.5 Flash
- **Real-time Responses**: Get instant answers to your e-commerce data questions
- **Streaming Responses**: Live typing effect for enhanced user experience
- **Data Visualization**: Automatic chart generation for relevant queries
- **RESTful API**: Easy integration with existing systems

## 📊 Supported Data

The system works with three main datasets:

1. **Product Eligibility Table**: Product information and ad eligibility
2. **Product Ad Metrics**: Advertising performance data (CPC, CTR, conversions, etc.)
3. **Product Total Metrics**: Overall sales and business metrics

## 🛠️ Setup Instructions

### Prerequisites

- Node.js (v16 or higher)
- npm or yarn
- Gemini API key from Google AI Studio

### Installation

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd ecommerce-ai-agent
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Configure environment variables**
   ```bash
   cp .env.example .env
   ```
   
   Edit `.env` and add your Gemini API key:
   ```
   GEMINI_API_KEY=your_gemini_api_key_here
   ```

4. **Setup the database**
   ```bash
   npm run setup-db
   ```

5. **Start the server**
   ```bash
   npm start
   ```

   For development with auto-reload:
   ```bash
   npm run dev
   ```

## 🔧 API Endpoints

### POST /api/ask
Ask a question and get a complete response.

**Request:**
```json
{
  "question": "What is my total sales?"
}
```

**Response:**
```json
{
  "question": "What is my total sales?",
  "answer": "Your total sales across all products is $40,267.60...",
  "data": [...],
  "sql_query": "SELECT SUM(total_revenue) as total_sales FROM product_total_metrics",
  "timestamp": "2024-01-15T10:30:00.000Z",
  "visualization": {
    "chart_config": {...},
    "chart_url": "..."
  }
}
```

### POST /api/ask-stream
Ask a question with streaming response (live typing effect).

### GET /api/schema
Get the database schema information.

### GET /api/sample-data/:table
Get sample data from a specific table.

## 📝 Example Questions

The AI agent can answer various types of questions:

### Sales & Revenue
- "What is my total sales?"
- "Show me revenue by product category"
- "Which product has the highest revenue?"

### Advertising Metrics
- "Calculate the RoAS (Return on Ad Spend)"
- "Which product had the highest CPC?"
- "What is the average conversion rate?"
- "Show me ad spend by campaign"

### Performance Analysis
- "Which products have conversion rate above 5%?"
- "Compare revenue between Electronics and Sports categories"
- "What is the total profit margin?"

### Product Insights
- "List all products in Electronics category"
- "Which products are not eligible for ads?"
- "Show me inventory levels for all products"

## 🧪 Testing

Run the test suite to verify all functionality:

```bash
npm test
```

This will test all example questions and display the results.

## 🏗️ Architecture

```
src/
├── server.js              # Main Express server
├── routes/
│   └── questions.js        # API route handlers
├── services/
│   ├── llmService.js       # Gemini LLM integration
│   ├── databaseService.js  # SQLite database operations
│   └── visualizationService.js # Chart generation
├── database/
│   └── setup.js           # Database initialization
└── test/
    └── test-queries.js     # API testing suite
```

## 🎯 Key Components

### LLM Service
- Integrates with Google Gemini 2.5 Flash
- Converts natural language to SQL queries
- Generates human-readable responses

### Database Service
- SQLite database with e-commerce schema
- Handles query execution and data retrieval
- Provides sample data for testing

### Visualization Service
- Automatic chart generation for relevant queries
- Supports bar charts, pie charts, and line graphs
- Plotly.js integration ready

## 🔒 Security Features

- Input validation and sanitization
- SQL injection prevention
- Error handling and logging
- CORS configuration

## 📈 Performance

- Local LLM processing (no internet required for inference)
- Efficient SQLite database
- Streaming responses for better UX
- Caching mechanisms for repeated queries

## 🚀 Deployment

### Local Development
```bash
npm run dev
```

### Production
```bash
npm start
```

### Docker (Optional)
```bash
docker build -t ecommerce-ai-agent .
docker run -p 3000:3000 ecommerce-ai-agent
```

## 📊 Demo Video Requirements

For the demo video, make sure to show:

1. **API calls** using tools like Postman or curl
2. **Terminal output** showing the processing
3. **All three required questions**:
   - What is my total sales?
   - Calculate the RoAS (Return on Ad Spend)
   - Which product had the highest CPC?

### Example curl commands:

```bash
# Test 1: Total Sales
curl -X POST http://localhost:3000/api/ask \
  -H "Content-Type: application/json" \
  -d '{"question": "What is my total sales?"}'

# Test 2: RoAS Calculation
curl -X POST http://localhost:3000/api/ask \
  -H "Content-Type: application/json" \
  -d '{"question": "Calculate the RoAS (Return on Ad Spend)"}'

# Test 3: Highest CPC
curl -X POST http://localhost:3000/api/ask \
  -H "Content-Type: application/json" \
  -d '{"question": "Which product had the highest CPC?"}'
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests
5. Submit a pull request



