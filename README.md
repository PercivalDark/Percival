# Adobe Stock Analyzer

A comprehensive Adobe Stock contributor analyzer with Chrome Extension frontend, Node.js backend with Puppeteer scraping, and Python-powered data analysis.

## 🚀 Features

### **Chrome Extension (Frontend)**
- **User-Friendly Interface**: Clean, modern popup interface with tabbed navigation
- **Multiple Input Methods**: Support for contributor username, URL, or profile page analysis
- **Real-Time Analysis**: Live progress tracking with step-by-step indicators
- **Comprehensive Results**: Overview, analytics, keywords, and insights tabs
- **Export Functionality**: JSON and CSV export options
- **Settings Management**: Backend URL configuration and API key management
- **Offline Capability**: Fallback to local scraping when backend is unavailable

### **Node.js Backend (API Server)**
- **Puppeteer Scraping**: Advanced web scraping with headless Chrome
- **Python Integration**: Seamless integration with Python analysis scripts
- **RESTful API**: Clean API endpoints for analysis, scraping, and keyword suggestions
- **Rate Limiting**: Built-in protection against abuse
- **CORS Support**: Configured for Chrome extension communication
- **Error Handling**: Comprehensive error handling and fallback mechanisms
- **Railway Ready**: Configured for easy Railway deployment

### **Python Analysis Engine**
- **Advanced Analytics**: Comprehensive portfolio scoring and metrics calculation
- **Keyword Analysis**: Intelligent keyword extraction and trend analysis
- **Category Classification**: Automatic content categorization
- **Market Insights**: AI-powered insights and opportunity identification
- **Performance Metrics**: Portfolio maturity and market position analysis
- **Trend Detection**: Identification of trending keywords and themes

## 📊 Data Analysis Capabilities

### **Portfolio Metrics**
- Total items and download counts
- Average downloads per item
- Portfolio score (0-100)
- Market position classification
- Content quality assessment

### **Keyword Intelligence**
- Automatic keyword extraction from asset titles
- Trend analysis (high/medium/low trending)
- Category classification
- Frequency analysis
- AI-powered keyword suggestions

### **Market Insights**
- Dominant category identification
- Performance benchmarking
- Growth opportunities
- Trending topic recommendations
- SEO optimization suggestions

### **Advanced Analytics**
- Portfolio maturity assessment
- Content diversity analysis
- Market positioning
- Competitive analysis
- Trend alignment scoring

## 🛠️ Technical Architecture

```
┌─────────────────┐    ┌──────────────────┐    ┌─────────────────┐
│  Chrome         │    │  Node.js         │    │  Python         │
│  Extension      │◄──►│  Backend         │◄──►│  Analysis       │
│                 │    │                  │    │  Engine         │
│  - Popup UI     │    │  - Express API   │    │  - Data         │
│  - Content      │    │  - Puppeteer     │    │    Processing   │
│    Scripts      │    │    Scraping      │    │  - Keyword      │
│  - Background   │    │  - Python        │    │    Analysis     │
│    Service      │    │    Integration   │    │  - Insights     │
│                 │    │  - Railway       │    │    Generation   │
│                 │    │    Deployment    │    │                 │
└─────────────────┘    └──────────────────┘    └─────────────────┘
```

## 📁 Project Structure

```
adobe-stock-analyzer/
│
├── extension/                     # Chrome Extension (Frontend)
│   ├── manifest.json              # Extension configuration
│   ├── popup.html                 # Main UI
│   ├── popup.js                   # Frontend logic
│   ├── style.css                  # Styling
│   ├── background.js              # Service worker
│   ├── content_script.js          # Page scraping
│   └── icons/                     # Extension icons
│
├── server/                        # Backend Server
│   ├── server.js                  # Express server with Puppeteer
│   ├── analyze.py                 # Python analysis script
│   ├── package.json               # Node.js dependencies
│   └── requirements.txt           # Python dependencies
│
├── package.json                   # Root package configuration
├── Procfile                       # Railway deployment config
├── .env.example                   # Environment variables template
└── README.md                      # This file
```

## 🚀 Quick Start

### **1. Clone the Repository**
```bash
git clone https://github.com/your-username/adobe-stock-analyzer.git
cd adobe-stock-analyzer
```

### **2. Install Dependencies**
```bash
# Install Node.js dependencies
npm run setup

# Or install manually:
cd server
npm install
pip install -r requirements.txt
```

### **3. Environment Setup**
```bash
# Copy environment template
cp .env.example .env

# Edit .env file with your configuration
# PORT=3000 (default)
# NODE_ENV=development
```

### **4. Start the Backend Server**
```bash
# Development mode with auto-reload
npm run dev

# Or production mode
npm start
```

The server will start at `http://localhost:3000`

### **5. Install Chrome Extension**
1. Open Chrome and navigate to `chrome://extensions/`
2. Enable "Developer mode" in the top right
3. Click "Load unpacked" and select the `extension` folder
4. The extension icon will appear in your Chrome toolbar

### **6. Configure Extension Settings**
1. Click the extension icon
2. Click "Settings"
3. Enter your backend URL: `http://localhost:3000` (for local development)
4. Save settings

## 🌐 Railway Deployment

### **Deploy to Railway**
1. **Connect Repository**: Link your GitHub repository to Railway
2. **Environment Variables**: Set any required environment variables
3. **Deploy**: Railway will automatically detect the Procfile and deploy

### **Environment Variables for Production**
```bash
NODE_ENV=production
PORT=3000  # Railway sets this automatically
PUPPETEER_HEADLESS=true
```

### **Update Extension for Production**
After deployment, update your Chrome extension settings:
1. Open extension settings
2. Update backend URL to your Railway URL: `https://your-app.railway.app`
3. Save settings

## 📖 Usage Guide

### **Basic Usage**
1. **Navigate** to any Adobe Stock contributor page
2. **Click** the extension icon in your Chrome toolbar
3. **Choose** analysis method:
   - Click "Analyze Current Page" for the current contributor
   - Or enter a contributor username/URL/ID manually
4. **View Results** in the comprehensive interface

### **Advanced Features**

#### **Backend API Analysis**
- Enable "Use Backend API" in settings for enhanced analysis
- Provides more detailed insights and AI-powered recommendations
- Includes advanced keyword suggestions and trend analysis

#### **Data Export**
- **JSON Export**: Complete analysis data for further processing
- **CSV Export**: Spreadsheet-compatible format for reporting
- **Copy to Clipboard**: Quick data sharing

#### **Keyword Suggestions**
- Click "Get AI Suggestions" in the Keywords tab
- Receive trending keyword recommendations
- Based on current portfolio and market trends

### **API Endpoints**

#### **Health Check**
```bash
GET /api/health
```

#### **Comprehensive Analysis**
```bash
POST /api/analyze
Content-Type: application/json

{
  "contributorInfo": {
    "type": "url",
    "url": "https://stock.adobe.com/contributor/123456/username"
  },
  "analysisType": "comprehensive"
}
```

#### **Data Scraping Only**
```bash
POST /api/scrape
Content-Type: application/json

{
  "contributorInfo": {
    "type": "id",
    "id": "123456"
  }
}
```

#### **Keyword Suggestions**
```bash
POST /api/suggest-keywords
Content-Type: application/json

{
  "keywords": [
    {"word": "business", "frequency": 15},
    {"word": "technology", "frequency": 12}
  ],
  "category": "Business"
}
```

## 🔧 Development

### **Local Development Setup**
```bash
# Start backend in development mode
cd server
npm run dev

# The server will restart automatically on file changes
```

### **Testing the Extension**
1. Make changes to extension files
2. Go to `chrome://extensions/`
3. Click the refresh icon on your extension
4. Test the changes

### **Python Script Testing**
```bash
# Test Python analysis directly
cd server
echo '{"scrapedData": {"contributorName": "Test"}, "contributorInfo": {"name": "Test"}}' | python analyze.py
```

### **API Testing**
```bash
# Test health endpoint
curl http://localhost:3000/api/health

# Test analysis endpoint
curl -X POST http://localhost:3000/api/analyze \
  -H "Content-Type: application/json" \
  -d '{"contributorInfo": {"type": "id", "id": "123456"}}'
```

## 🛡️ Security Features

- **Rate Limiting**: 100 requests per 15 minutes per IP
- **CORS Protection**: Configured for Chrome extension origins
- **Input Validation**: Comprehensive request validation
- **Error Handling**: Secure error messages without sensitive data exposure
- **Helmet.js**: Security headers for Express server

## 🔍 Troubleshooting

### **Extension Issues**

#### **"No data extracted" Error**
- Ensure you're on a valid Adobe Stock contributor page
- Check browser console for detailed error messages
- Try refreshing the page and running analysis again

#### **Backend Connection Failed**
- Verify backend server is running (`http://localhost:3000/api/health`)
- Check extension settings for correct backend URL
- Ensure CORS is properly configured

### **Server Issues**

#### **Puppeteer Launch Failed**
```bash
# Install missing dependencies (Linux)
sudo apt-get install -y gconf-service libasound2 libatk1.0-0 libc6 libcairo2 libcups2 libdbus-1-3 libexpat1 libfontconfig1 libgcc1 libgconf-2-4 libgdk-pixbuf2.0-0 libglib2.0-0 libgtk-3-0 libnspr4 libpango-1.0-0 libpangocairo-1.0-0 libstdc++6 libx11-6 libx11-xcb1 libxcb1 libxcomposite1 libxcursor1 libxdamage1 libxext6 libxfixes3 libxi6 libxrandr2 libxrender1 libxss1 libxtst6 ca-certificates fonts-liberation libappindicator1 libnss3 lsb-release xdg-utils wget
```

#### **Python Script Errors**
- Ensure Python 3.8+ is installed
- Install required packages: `pip install -r requirements.txt`
- Check Python script permissions

### **Railway Deployment Issues**

#### **Build Failures**
- Check that all dependencies are listed in `package.json`
- Ensure Python requirements are in `requirements.txt`
- Verify Procfile is correctly configured

#### **Runtime Errors**
- Check Railway logs for detailed error messages
- Ensure environment variables are set correctly
- Verify Puppeteer works in Railway's environment

## 📈 Performance Optimization

### **Backend Optimization**
- **Browser Reuse**: Puppeteer browser instance is reused across requests
- **Request Caching**: Consider implementing Redis for caching results
- **Rate Limiting**: Prevents server overload
- **Timeout Handling**: Prevents hanging requests

### **Extension Optimization**
- **Lazy Loading**: Content scripts load only when needed
- **Efficient DOM Queries**: Optimized selectors for fast data extraction
- **Background Processing**: Heavy operations run in background script
- **Storage Management**: Automatic cleanup of old analysis data

## 🤝 Contributing

### **Development Workflow**
1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes
4. Test thoroughly with real Adobe Stock pages
5. Commit your changes: `git commit -m 'Add amazing feature'`
6. Push to the branch: `git push origin feature/amazing-feature`
7. Open a Pull Request

### **Testing Guidelines**
- Test with multiple contributor pages
- Verify data accuracy against actual page content
- Check console logs for errors
- Test both local scraping and backend API modes
- Validate export functionality

### **Code Style**
- Use consistent indentation (2 spaces)
- Add comments for complex logic
- Follow JavaScript/Python best practices
- Update documentation for new features

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔗 Links

- **Adobe Stock**: [Official Website](https://stock.adobe.com)
- **Chrome Extensions**: [Developer Documentation](https://developer.chrome.com/docs/extensions/)
- **Railway**: [Deployment Platform](https://railway.app)
- **Puppeteer**: [Documentation](https://pptr.dev/)

## 📞 Support

For support, please:
1. Check the troubleshooting section above
2. Search existing [GitHub Issues](https://github.com/your-username/adobe-stock-analyzer/issues)
3. Create a new issue with detailed information about your problem

---

**Version**: 1.0.0  
**Last Updated**: January 2024  
**Compatibility**: Adobe Stock 2024, Chrome Extensions Manifest V3  
**Status**: Production Ready ✅

## 🎯 Roadmap

### **Upcoming Features**
- [ ] Historical data tracking and trend analysis
- [ ] Batch analysis for multiple contributors
- [ ] Advanced AI insights with GPT integration
- [ ] Portfolio comparison tools
- [ ] Automated reporting and alerts
- [ ] Mobile app companion
- [ ] Integration with other stock platforms

### **Technical Improvements**
- [ ] Database integration for data persistence
- [ ] Redis caching for improved performance
- [ ] WebSocket support for real-time updates
- [ ] Advanced error recovery mechanisms
- [ ] Comprehensive test suite
- [ ] Docker containerization
- [ ] Kubernetes deployment support
