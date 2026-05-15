#  — Intelligent Drug Prediction System

## ML Model
- **Algorithm**: Random Forest Classifier (300 trees)
- **Test Accuracy**: 97.50%
- **Cross-Validation Accuracy**: 97.25% (5-fold)
- **Training Records**: 1,200 patients
- **Drug Classes**: 49 unique medications

## Project Structure
```
app/
├── backend/
│   ├── app.py               ← Flask API server
│   ├── model.pkl            ← Trained RandomForest model + encoders
│   └── drug_descriptions.json
└── frontend/
    └── index.html           ← Complete single-file React-like frontend
```

## Setup & Run

### 1. Install Python dependencies
```bash
pip install flask scikit-learn numpy
```

### 2. Start the Flask backend
```bash
cd backend
python app.py
# Server runs on http://localhost:5000
```

### 3. Open the frontend
Open `frontend/index.html` in your browser directly, or serve it:
```bash
cd frontend
python -m http.server 3000
# Visit http://localhost:3000
```

## API Endpoints

### POST /predict
```json
{
  "age": 45,
  "sex": "M",
  "bp": "HIGH",
  "cholesterol": "HIGH",
  "na_to_k": 14.5
}
```
Returns:
```json
{
  "drug": "Amlodipine 5mg",
  "drug_class": "Calcium Channel Blocker",
  "description": "...",
  "confidence": 94.3,
  "alternatives": [...],
  "model_info": {...}
}
```

### GET /model-info
Returns model metadata: name, accuracy, drug count.
