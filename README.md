# 🚆 AI Train & Trip Planner ✈️

An AI-powered travel assistant that plans trips and finds trains for any city, state or country. It runs fully on your own computer using a local language model, so there are no paid APIs and no data leaves your machine.

## Features

- 💬 Chat interface: type a place or a full request like "Plan 3 days in Goa"
- 🌍 Works for any city, state or country
- 🚆 Train search between cities from a CSV dataset
- 📍 Semantic place search: finds tourist places by meaning using embeddings
- 🖼️ Shows photos of the destination (fetched from Wikipedia)
- 🗓️ Day-by-day itineraries with estimated costs in INR
- 🎨 Colourful Streamlit UI with background image and quick-start buttons

## How it works

1. The user types a message.
2. Llama 3.2 extracts the place names from it.
3. The app searches the local dataset (trains and tourist places).
   Places are matched using `nomic-embed-text` embeddings and cosine similarity.
4. The matching data is passed to Llama 3.2 as reference data.
5. If the dataset has nothing for that place, the model answers from general knowledge and says so.
6. Destination photos are fetched from the Wikipedia API and shown above the answer.

## Tech stack

| Part | Tool |
|---|---|
| Language | Python |
| LLM | Llama 3.2 via Ollama |
| Embeddings | nomic-embed-text |
| Data handling | pandas, NumPy |
| Frontend | Streamlit |
| Images | Wikipedia API |

## Project structure

```
Ai_trip_assistant/
├── data/
│   ├── trains.csv
│   └── places.csv
├── agent.py      # LLM logic and context building
├── app.py        # Streamlit UI
├── images.py     # Fetches destination photos
├── rag.py        # Embeddings and place search
├── tools.py      # Train and place search functions
├── background.jpg
└── requirements.txt
```

## Installation

1. Install [Python 3.12+](https://www.python.org/) and [Ollama](https://ollama.com/).
2. Pull the models:
```
   ollama pull llama3.2
   ollama pull nomic-embed-text
```
3. Install the packages:
```
   pip install -r requirements.txt
```
4. Run the app:
```
   python -m streamlit run app.py
```

## Example prompts

- `Plan 3 days in Goa`
- `Trains from Hyderabad to Mumbai`
- `Kerala trip for 5 days`
- `Plan a week in Japan`

## Limitations

- Train data comes from a small sample CSV. Always verify timings on [IRCTC](https://www.irctc.co.in) or [NTES](https://enquiry.indianrail.gov.in/ntes/).
- For places not in the dataset, answers come from the model's general knowledge and may contain mistakes.
- Booking and payments are not supported.

## Future improvements

- Full Indian Railways dataset or live train status API
- Weather and budget estimator tools
- Voice input and Telugu/Hindi support
- Save trips and export itinerary as PDF

## Author

Najeeba Fathima
