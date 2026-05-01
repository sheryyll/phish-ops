# Phish Ops (Network Security Phishing Detection)

## Project Overview
Phish Ops is an end-to-end Machine Learning Operations (MLOps) project designed to detect network security threats, specifically phishing attacks. The project encompasses a complete ML pipeline, from data ingestion using MongoDB to model training, evaluation, and deployment via a FastAPI application.

## Features
- **Data Ingestion Pipeline**: Extracts data from MongoDB for processing.
- **Automated ML Pipeline**: Implements data validation, data transformation, and model training.
- **REST API**: Serves predictions and triggers training pipelines via FastAPI.
- **Experiment Tracking**: Integrated with MLflow and Dagshub for tracking experiments and model metrics.
- **Containerization**: Includes a Dockerfile for easy containerization and deployment.
- **CI/CD Ready**: Configured with GitHub Actions (`.github`) for continuous integration and deployment.

## Tech Stack
- **Programming Language**: Python 3
- **Web Framework**: FastAPI, Uvicorn
- **Machine Learning**: Scikit-Learn, Pandas, NumPy
- **Database**: MongoDB (PyMongo)
- **MLOps & Tracking**: MLflow, Dagshub
- **Containerization**: Docker

## Installation

### Prerequisites
- Python 3.8+
- MongoDB instance (local or Atlas)

### Steps
1. **Clone the repository**
   ```bash
   git clone https://github.com/sheryyll/phish-ops.git
   cd phish-ops
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows use `venv\Scripts\activate`
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Set up environment variables**
   Create a `.env` file in the root directory and add your MongoDB connection strings:
   ```env
   MONGODB_URL_KEY="your-mongodb-url"
   MONGO_DB_URL="your-mongodb-url"
   ```

## Usage

### 1. Push Data to Database
If starting fresh, push your local CSV data to MongoDB using the provided script:
```bash
python push_data.py
```

### 2. Run the Training Pipeline
You can manually run the training pipeline to generate the model artifacts (`model.pkl`, `preprocessor.pkl`):
```bash
python main.py
```

### 3. Start the FastAPI Application
Start the server to expose the API endpoints:
```bash
python app.py
```
The application will run on `http://localhost:8000`.

### API Endpoints
- **GET `/docs`**: Access the Swagger UI for the API.
- **GET `/train`**: Triggers the model training pipeline.
- **POST `/predict`**: Upload a CSV file to get phishing predictions. The output will be displayed as an HTML table.

## Project Structure
```
phish-ops/
├── networksecurity/       # Core package containing ML pipeline components
│   ├── components/        # Ingestion, validation, transformation, trainer
│   ├── entity/            # Config and artifact entities
│   ├── exception/         # Custom exception handling
│   ├── logging/           # Custom logging setup
│   ├── pipeline/          # Training pipeline logic
│   └── utils/             # Helper functions
├── Network_Data/          # Raw data directory
├── final_model/           # Directory storing trained model artifacts
├── prediction_output/     # Directory for outputting prediction results
├── templates/             # HTML templates for the web interface
├── notebooks/             # Jupyter notebooks for data exploration
├── app.py                 # FastAPI application entry point
├── main.py                # Script to execute the ML pipeline
├── push_data.py           # Script to load CSV data into MongoDB
├── requirements.txt       # Project dependencies
├── setup.py               # Package setup configuration
└── Dockerfile             # Docker container configuration
```

## Contributing
Contributions are welcome! If you would like to contribute to this project, please follow these steps:
1. Fork the repository.
2. Create a new branch (`git checkout -b feature/YourFeatureName`).
3. Commit your changes (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature/YourFeatureName`).
5. Open a Pull Request.

