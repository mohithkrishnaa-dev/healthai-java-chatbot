# 🏥 HealthAI Pro+

**HealthAI Pro+** is a full-stack AI-powered medical assistant built with a lightweight Java backend and a modern web interface. It provides instant, structured medical information about diseases, symptoms, and prevention using Google Gemini AI with a smart offline medical database fallback.

⚠️ This project is for educational purposes only and is not a substitute for professional medical advice.

---

## 🚀 Features

### Backend (Java)

- Google Gemini AI integration for medical Q&A  
- Offline disease knowledge base fallback  
- Intelligent in-memory caching (6-hour TTL)  
- Lightweight Java HTTP server (no Spring overhead)  
- REST API endpoint: `/ask`  
- Automatic CORS handling  
- Production-style error handling and timeouts  

### Frontend (HTML + JavaScript)

- Professional medical-grade UI  
- Login, Register, Forgot Password, Guest mode  
- Persistent chat history (LocalStorage)  
- Voice input using Web Speech API  
- Dark / Light theme toggle  
- Chat export & clear history  
- Typing animation and copy-to-clipboard replies  

---

## 🧠 How It Works

```
User Browser (index.html)
          ↓
      POST /ask
          ↓
   Java HTTP Server
          ↓
 Local DB → Cache → Gemini AI
```

1. User sends a question  
2. Server checks cache  
3. If not cached, checks local medical DB  
4. If not found, queries Gemini AI  
5. Response is cached and returned  

---

## 📂 Project Structure

```
healthai-pro-plus/
│
├── HealthAIProPlus.java   # Java backend server
├── index.html             # Frontend UI
├── README.md
└── LICENSE
```

---

## ⚙️ Requirements

- Java 17+  
- Google Gemini API Key  
- org.json library  

Download JSON library:  
https://repo1.maven.org/maven2/org/json/json/20230227/json-20230227.jar  

---

## 🔧 Setup Instructions

### 1. Clone Repository

```bash
git clone https://github.com/yourusername/healthai-pro-plus.git
cd healthai-pro-plus
```

---

### 2. Add Gemini API Key

Edit in `HealthAIProPlus.java`:

```java
private static final String GEMINI_API_KEY = "YOUR_API_KEY_HERE";
```

---

### 3. Compile

**Windows**

```bash
javac -cp ".;json-20230227.jar" HealthAIProPlus.java
```

**Linux / macOS**

```bash
javac -cp ".:json-20230227.jar" HealthAIProPlus.java
```

---

### 4. Run Server

```bash
java -cp ".;json-20230227.jar" HealthAIProPlus
```

Server starts at:

```
http://localhost:8080
```

---

## 🔌 API Usage

### Endpoint

```
POST /ask
```

### Request

```json
{
  "message": "Tell me about malaria"
}
```

### Response

```json
{
  "timestamp": "2026-01-17T12:30:22Z",
  "query": "Tell me about malaria",
  "structured": true,
  "reply": "Malaria is a life-threatening infectious disease...",
  "source": "local"
}
```

Sources:

- `local` → Offline database  
- `cache` → In-memory cache  
- `gemini` → Google Gemini AI  

---

## 🗄 Built-in Medical Database

Includes offline knowledge for:

- Malaria  
- Dengue  
- COVID-19  
- Typhoid  
- Asthma  
- Diarrhea  
- Pink Eye  
- Jock Itch  
- Stomach Flu  

---

## 🔐 Safety Design

- No prescriptions generated  
- No emergency instructions  
- Medical disclaimer added to responses  
- AI restricted strictly to medical topics  

---

## 🛣 Roadmap

- JWT authentication system  
- Persistent database (PostgreSQL)  
- Doctor-reviewed datasets  
- User profiles & history sync  
- Admin analytics dashboard  

---

## 👨‍💻 Author

**Mohith Krishnaa Putta**  
Backend & Automation Developer  

---

## 📜 License

MIT License
