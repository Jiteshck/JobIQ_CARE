# JobIQ CARE

JobIQ CARE is an AI-powered career advisor that analyzes uploaded CVs, generates personalized interview questions, and recommends the most suitable jobs based on your skills and experience.

**Live Frontend:** [jiteshck.github.io/JobIQ_CARE](https://jiteshck.github.io/JobIQ_CARE/)  
**Backend:** Hosted on [Render](https://render.com)

---

## 🗂️ Project Structure

```
JobIQ_CARE/
│
├── backend/
│   ├── main.py             # FastAPI backend (API routes, Gemini, email)
│   ├── models.py           # Pydantic models
│   ├── requirements.txt    # Python dependencies
│   └── .env                # Environment variables (never commit this)
│
├── frontend/
│   ├── index.html          # Landing page
│   ├── index.css           # Styles
│   ├── login.html          # Login / Signup
│   ├── analyze.html        # Interview questions
│   ├── result.html         # Job recommendations
│   └── upload_cv.html      # CV upload page
│
├── render.yaml             # Render deployment config
├── .env.example            # Environment variable template
└── .gitignore
```

---

## 🚀 Tech Stack

| Layer     | Technology                          |
|-----------|-------------------------------------|
| Frontend  | HTML, CSS, JavaScript (GitHub Pages)|
| Backend   | Python, FastAPI, Uvicorn            |
| AI        | Google Gemini 2.5 Flash             |
| Database  | MongoDB Atlas                       |
| Email     | Brevo HTTP API                      |
| Hosting   | Render (backend), GitHub Pages (frontend) |

---

## ⚙️ Local Setup

### 1️⃣ Clone the Repository
```bash
git clone https://github.com/Jiteshck/JobIQ_CARE.git
cd JobIQ_CARE/backend
```

### 2️⃣ Create & Activate Virtual Environment
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python -m venv venv
source venv/bin/activate
```

### 3️⃣ Install Dependencies
```bash
pip install -r requirements.txt
```

### 4️⃣ Set Up Environment Variables
Create a `.env` file inside the `backend/` folder (use `.env.example` as a template):

```env
MONGO_URI=mongodb+srv://<user>:<password>@<cluster>.mongodb.net/<dbname>
DB_NAME=JobIQ

# Brevo HTTP API key (app.brevo.com → SMTP & API → API Keys)
BREVO_API_KEY=your-api-key-here

# Must be a verified sender in Brevo → Senders & Domains
MAIL_FROM=your@email.com
MAIL_FROM_NAME=JobIQ CARE

GEMINI_API_KEY=your-gemini-api-key
OTP_EXPIRE_SECONDS=300

# Comma-separated, no spaces
ALLOWED_ORIGINS=https://jiteshck.github.io,http://localhost:8000
```

### 5️⃣ Run the Backend
```bash
uvicorn main:app --reload
```

Server runs at `http://127.0.0.1:8000`

---

## ☁️ Deploying to Render

1. Push your code to GitHub
2. Go to [render.com](https://render.com) → New → Web Service → connect your repo
3. Render will auto-detect `render.yaml` — just fill in the secret env vars in the dashboard:
   - `MONGO_URI`, `BREVO_API_KEY`, `MAIL_FROM`, `GEMINI_API_KEY`
4. Set **Root Directory** to `backend`
5. Deploy

To redeploy after changes:
```bash
git add .
git commit -m "your message"
git push
```

---

## 🔑 Getting API Keys

**Brevo (email):**
1. Sign up at [app.brevo.com](https://app.brevo.com)
2. Go to SMTP & API → API Keys → Generate a new key (`xkeysib-...`)
3. Go to Senders & Domains → verify your sender email

**Google Gemini:**
1. Go to [aistudio.google.com](https://aistudio.google.com)
2. Get API Key

**MongoDB Atlas:**
1. Go to [cloud.mongodb.com](https://cloud.mongodb.com)
2. Create a cluster → Connect → Get your connection string

---

## 🧰 Notes

- Never commit `.env` or `venv/` to GitHub (already in `.gitignore`)
- Render's free plan spins down after inactivity — first request may be slow
- Frontend API calls must point to your Render backend URL

---

## 👤 Creater

**Jitesh Choudhary**  
