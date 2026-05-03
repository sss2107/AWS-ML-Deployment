# AWS ML Deployment

A compact Flask application that serves a trained machine learning model through a web form. The app collects candidate inputs, sends them to a serialized scikit-learn model, and returns a predicted salary estimate.

## What This Project Shows

- Training a simple regression model with scikit-learn
- Saving and loading a model with `pickle`
- Serving predictions from a Flask application
- Rendering a lightweight HTML form with Jinja templates
- Preparing a Python web app for deployment with Gunicorn and a `Procfile`

## Tech Stack

- Python
- Flask
- NumPy
- pandas
- scikit-learn
- Gunicorn

## Repository Structure

```text
.
├── app.py                 # Flask app and prediction route
├── model.py               # Model training script
├── model.pkl              # Serialized trained model
├── request.py             # Example request script
├── Procfile               # Gunicorn start command
├── requirements.txt       # Python dependencies
└── templates/
    └── index.html         # Web form UI
```

## Run Locally

Clone the repository:

```bash
git clone https://github.com/sss2107/AWS-ML-Deployment.git
cd AWS-ML-Deployment
```

Create and activate a virtual environment:

```bash
python -m venv .venv
source .venv/bin/activate
```

Install dependencies:

```bash
pip install -r requirements.txt
```

Start the Flask app:

```bash
python app.py
```

Open the local URL shown in your terminal, enter the experience, test score, and interview score values, then submit the form to generate a salary prediction.

## Deployment Notes

The included `Procfile` runs the app with Gunicorn:

```text
web: gunicorn app:app
```

This structure can be adapted for Heroku-style platforms, AWS Elastic Beanstalk, EC2, App Runner, or a container deployment. For production use, avoid `debug=True`, add request validation, and keep model artifacts versioned through a proper model registry or object store.

## Current Limitations

- `model.py` references `hiring.csv`, which is not currently included in the repository.
- The form route accepts only integer inputs.
- `request.py` calls `/predict_api`, but the Flask app currently exposes `/predict`.
- There are no automated tests yet.

## Improvement Ideas

- Add the training dataset or document where to obtain it
- Add input validation and error messages
- Add a JSON prediction API route
- Add tests for the web and API prediction paths
- Add Docker or AWS deployment templates

## License

This project is licensed under the terms in [LICENSE](LICENSE).
