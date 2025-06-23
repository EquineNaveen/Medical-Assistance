# 🏥 SmartHealth Assistant

A personalized medical chatbot application that combines Google Gemini AI with Neo4j graph database to provide health assistance with persistent memory of your medical history.

## 📋 Overview

SmartHealth Assistant is an intelligent healthcare companion that:

- Remembers your medical history and symptoms over time
- Automatically extracts health information from natural conversations
- Tracks symptoms and vitals with temporal relationships
- Provides context-aware health advice based on your data history
- Maintains user-specific health profiles for personalized interactions

## 🚀 Features

- **Interactive Chat Interface**: Natural conversation with a medical assistant
- **Automatic Data Extraction**: Identifies symptoms and vitals from your messages
- **Historical Health Tracking**: Builds a timeline of your health information
- **Context-Aware Responses**: AI considers your past data for better advice
- **User-Specific Profiles**: Separate health records for each user
- **Temporal Data Organization**: Organizes health data by date
- **Secure Credential Management**: Environment variables for secure API keys

## 🏗️ Architecture

- **Frontend**: Streamlit web interface with chat functionality
- **AI Engine**: Google Gemini (gemini-1.5-flash) for natural language processing
- **Database**: Neo4j graph database for structured health data storage
- **Workflow**: LangGraph for conversation state management and memory

## 🔄 Data Flow

1. User enters health information through chat interface
2. AI extracts symptoms and vitals from natural language input
3. Data is stored in Neo4j with user-specific nodes and date relationships
4. Historical context is retrieved for personalized responses
5. AI provides health advice based on current input and past data

## 💻 Technology Stack

- **Python**: Core application language
- **Streamlit**: Web application framework for the user interface
- **LangChain**: Framework for LLM application development
- **LangGraph**: Conversation state management
- **Neo4j**: Graph database for storing health data
- **Google Gemini API**: AI model for natural language processing

## 🛠️ Installation & Setup

### Prerequisites

- Python 3.9+
- Neo4j database instance (local or cloud)
- Google Gemini API key

### Environment Setup

1. Clone the repository:
   ```
  git clone https://github.com/EquineNaveen/Medical-Assistance.git
   cd SmartHealth-Assistant
   ```

2. Install required packages:
   ```
   pip install -r requirements.txt
   ```

3. Create a `.env` file in the root directory with the following variables:
   ```
   NEO4J_URI=your_neo4j_uri
   NEO4J_USERNAME=your_neo4j_username
   NEO4J_PASSWORD=your_neo4j_password
   GOOGLE_API_KEY=your_google_api_key
   ```

### Database Initialization

Run the database initialization script to set up constraints and indexes:
```
python init_db.py
```

## 🚀 Running the Application

Start the Streamlit web interface:
```
streamlit run app.py
```

Or run the command-line version:
```
python main.py
```

## 👤 Usage

1. Enter your username in the sidebar
2. Enter your Google API key (if not already set in the `.env` file)
3. Start chatting about your health concerns
4. The assistant will:
   - Extract and store relevant health data
   - Consider your past health information
   - Provide personalized responses

## 📊 Data Structure

The application uses a graph database with the following main nodes:
- **Patient**: Stores user information
- **Date**: Temporal nodes connected to patients
- **Symptoms**: Lists of symptoms connected to dates
- **Vitals**: Measurements like temperature, blood pressure connected to dates

Relationships between nodes:
- `(patient)-[:ON_THE_DAY]->(date)`
- `(date)-[:HAS_SYMPTOMS]->(symptoms)`
- `(date)-[:HAS_VITALS]->(vitals)`

## 🔐 Security Considerations

- API keys and database credentials are stored in environment variables
- User data is segregated by username
- No sensitive authentication data is stored in the session state

