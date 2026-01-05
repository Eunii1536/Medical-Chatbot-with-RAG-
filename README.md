Here’s a professional and detailed project description you can use for your GitHub README page. It explains what your code does, how it works, and the technologies involved.  

***

# 🧠 Enhanced Multilingual AI Health Chatbot

This project is an **intelligent AI chatbot system** that seamlessly integrates **Character.AI**, **Groq’s LLaMA-3.3 model**, and **FastEmbed embeddings** to provide **emotionally safe, multilingual, and contextually aware** conversations with healthcare-related assistance.  

It is built in **Python (async/await design)** and can understand, translate, paraphrase, and respond in English, Hindi, or Hinglish—while detecting and handling sensitive or medical contexts with care.

***

## 🚀 Key Features

### 💬 1. Character.AI Integration
The bot connects to a specific **Character.AI persona** using `PyCharacterAI`. It engages in natural, dynamic conversation powered by Character.AI’s chat interface, while your Groq model ensures intelligent preprocessing and filtering before messages are sent.

### 🔠 2. Multilingual & Hinglish Support
The chatbot detects the **language and style** of the user’s message (English, Hindi, or Hinglish) using Groq’s large language model.  

It then:
- Translates non-English messages into English before interaction.  
- Converts Character.AI’s English responses back into the original language or Hinglish.  
- Maintains tone, informality, and cultural nuances.

### 💉 3. Smart Medical Intent Detection
A **medical assistant submodule** analyzes the user’s input to extract:
- The **illness or symptom** mentioned.
- The appropriate **doctor specialties** for that condition.

If the input indicates **serious health risks** (like chest pain, high fever, or passing out), the system fetches relevant doctors from a structured dataset (`dataset.json`) using an **embedding-based retriever** powered by FastEmbed and NumPy similarity search.

### 🩺 4. Doctor Recommendation Engine
The **DoctorRetriever** class embeds doctor descriptions and retrieves the **top 3 relevant specialists** using cosine similarity.  

Displayed doctor details include:
- Name  
- Specialization and category  
- Qualifications  
- Availability  
- Contact information  
- Consultation fee  

This acts as a **lightweight offline RAG (Retrieval-Augmented Generation)** component.

### 🧩 5. Sensitive Message Censorship and Paraphrasing
The **MessageCensor** class identifies self-harm or suicidal expressions using a keyword detector.  
If any violation indicators are found, the message is **paraphrased via Groq’s LLaMA model** to:
- Preserve the user’s emotional tone.  
- Remove filtered or trigger phrases (like *“I want to die”* → *“I feel like I can’t go on”*).  
- Maintain empathy and conversational flow.  

If API calls fail, a safe **rule-based fallback** handles censorship gracefully.

### 🧠 6. Emotionally Safe Chat Flow
Each chat message follows a carefully structured flow:
1. Detect language and user style.  
2. Translate the user message to English (if needed).  
3. Check for serious medical or self-harm phrases.  
4. Retrieve doctor info if health risk is detected.  
5. Censor self-harm phrases safely.  
6. Send the sanitized input to Character.AI.  
7. Translate Character.AI’s final response to original language or Hinglish.  

***

## 🏗️ Tech Stack

| Component | Technology Used |
|------------|------------------|
| **Core** | Python (asyncio based) |
| **Language Model** | Groq API – LLaMA 3.3 70B |
| **Chat Connection** | PyCharacterAI |
| **Embeddings** | FastEmbed |
| **Vector Math** | NumPy |
| **Environment Management** | dotenv |
| **Data** | JSON-based doctor dataset (`dataset.json`) |

***

## ⚙️ Setup and Usage

### Prerequisites
- Python 3.9 or above  
- Groq API key  
- Character.AI token  
- `dataset.json` file with doctor details  

### Installation
```bash
git clone https://github.com/yourusername/enhanced-ai-doctor-chatbot.git
cd enhanced-ai-doctor-chatbot
pip install -r requirements.txt
```

### Environment Variables
Create a `.env` file and add:
```env
GROQ_API_KEY=your_groq_api_key_here
```

### Run the Chatbot
```bash
python main.py
```

***

## 🧩 Project Structure

```
📦 enhanced-ai-doctor-chatbot/
 ┣ 📜 main.py                  # Entry point; initializes and runs chatbot
 ┣ 📜 dataset.json             # Doctor database
 ┣ 📜 requirements.txt         # Dependencies
 ┣ 📜 .env                     # Environment variables
 ┗ 📂 modules/
    ┣ DoctorRetriever.py       # Doctor search with embeddings
    ┣ MessageCensor.py         # Self-harm detector & paraphraser
    ┣ EnhancedChatBot.py       # Main conversational logic
```



***

Would you like me to format this as a **ready-to-use GitHub README.md** (with emojis, table of contents, and badges)?
