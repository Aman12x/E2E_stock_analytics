Link to Access: https://e2e-stock-analytics.onrender.com


Reddit Discussions based Stock Sentiment Analyzer

A web application that analyzes Reddit sentiment for stock symbols using natural language processing and provides visual sentiment insights from popular investment/finance subreddits.

Features

- Real-time sentiment analysis of Reddit posts from r/stocks, r/investing, and r/wallstreetbets
- Visual sentiment gauge showing sentiment on a -1.0 to +1.0 scale
- Interactive web interface with responsive design
- Top posts display with sentiment scores
- Post distribution analytics (positive/neutral/negative breakdown)
- Stock price integration (if implemented)

How It Works

The application uses TextBlob for sentiment analysis, which returns polarity scores between -1.0 (very negative) and +1.0 (very positive). The sentiment is categorized as:

- Very Positive: 0.5 to 1.0
- Slightly Positive: 0.1 to 0.5
- Neutral: -0.1 to 0.1
- Slightly Negative: -0.5 to -0.1
- Very Negative: -1.0 to -0.5

Prerequisites

- Python 3.10+
- Reddit API credentials
- Required Python packages (see requirements.txt)

Installation

Step 1: Clone the Repository

```
git clone <repository-url>
cd reddit-stock-sentiment-analyzer
```

Step 2: Set Up Virtual Environment

For Windows:

```
python -m venv venv
venv\Scripts\activate
```

For Linux/Mac:

```
python3.10 -m venv venv
source venv/bin/activate
```

Step 3: Install Dependencies

```
pip install -r requirements.txt
```

Step 4: Environment Configuration

Create a .env file in the project root with your Reddit API credentials:

```
REDDIT_CLIENT_ID=your_client_id_here
REDDIT_CLIENT_SECRET=your_client_secret_here
REDDIT_USER_AGENT=your_app_name_here
```

Getting Reddit API Credentials:

1. Go to https://www.reddit.com/prefs/apps
2. Click "Create App" or "Create Another App"
3. Choose "script" as the app type
4. Note down your client ID and client secret

Usage

Running the Application

1. Activate your virtual environment
2. Run the Python backend server
3. Open your web browser and navigate to the application URL
4. Enter a stock symbol (e.g., AAPL, TSLA, GME)
5. Click "Analyze" to get sentiment results

Example Analysis Output

For a stock like AAPL with a sentiment score of 0.101:
- Sentiment Label: "Slightly Positive"
- Visual gauge showing position on the sentiment scale
- Distribution showing 15 positive posts, 0 neutral, 1 negative
- Interpretation explaining cautious optimism

Project Structure

```
reddit-stock-sentiment-analyzer/
├── app.py                  # Main Flask/backend application
├── index.html             # Frontend web interface
├── requirements.txt       # Python dependencies
├── .env                   # Environment variables (create this)
├── reddit_sentiment.py   # Reddit sentiment analysis class
└── README.md             # This file
```

Key Components

Backend (reddit_sentiment.py)

- RedditSentimentAnalyzer class
- Text cleaning and preprocessing
- TextBlob sentiment analysis
- Reddit API integration using PRAW
- Data aggregation and formatting

Frontend (index.html)

- Responsive web interface
- Interactive sentiment gauge
- Real-time results display
- Mobile-friendly design
- Visual sentiment distribution charts

API Endpoints

- POST /analyze - Analyzes sentiment for a given stock symbol
  - Parameters: stock_symbol (string)
  - Returns: JSON with sentiment analysis results

Understanding Sentiment Scores

The sentiment analysis provides both individual post sentiments and an overall average:

- Individual Post Sentiment: Each post gets a score from -1.0 to +1.0
- Average Sentiment: Mean of all post sentiments
- Post Distribution: Count of positive, neutral, and negative posts

Note: A stock can have mostly positive posts but still show a low average sentiment if the positive sentiment is mild rather than enthusiastic.

Limitations

- Analysis limited to recent posts (last 30 days)
- Dependent on Reddit API rate limits
- Sentiment analysis accuracy varies with text quality and context
- Results may not reflect overall market sentiment

Dependencies

```
praw>=7.0.0
textblob>=0.17.0
pandas>=1.5.0
python-dotenv>=0.19.0
flask>=2.0.0
requests>=2.25.0
```

Troubleshooting

Common Issues:

1. Reddit API Authentication Error
   - Verify your .env file credentials
   - Check if your Reddit app is properly configured

2. No Posts Found
   - Try different stock symbols
   - Check if the stock symbol is commonly discussed on Reddit

3. Sentiment Score Seems Off
   - Remember TextBlob uses -1.0 to +1.0 scale, not percentages
   - Low positive scores (0.1) indicate mild positive sentiment

Rate Limiting

If you encounter rate limiting issues:
- Reduce the post limit in the search query
- Add delays between requests
- Use Reddit's API guidelines for optimal performance

Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

License

This project is licensed under the MIT License - see the LICENSE file for details.

