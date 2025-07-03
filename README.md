# personal-career-conversations-agent

This project is an interactive AI agent that talks about your background, skills, and experience, drawing from your LinkedIn profile and other sources. The future of resumes is conversational—this agent demonstrates how!

Try it live on Hugging Face Spaces:  
[https://huggingface.co/spaces/harish-anandaramanujam/carrer_conversations_gpt](https://huggingface.co/spaces/harish-anandaramanujam/carrer_conversations_gpt)

---

## 📣 The Future of Resumes

This project demonstrates how AI can represent your professional story interactively. Instead of static resumes, imagine recruiters and collaborators having a conversation with your digital persona!

## 🧑‍💼 What does it do?

- Answers questions about your career, background, and skills as if it were you.
- Uses your LinkedIn profile (PDF) and a summary text file as its knowledge base.
- Records user interest (email, name, notes) and logs any questions it can't answer.
- Pushes notifications for user actions and unknown questions via Pushover.
- Runs as a Gradio chat app for easy web deployment.

---

## 🚀 Deployment Instructions

### 1. Hugging Face Setup

- Visit [https://huggingface.co](https://huggingface.co) and create an account.
- From your avatar menu (top right), choose **Access Tokens**.
- Click **Create New Token** and give it **WRITE** permissions.
- Add this token to your `.env` file as:
  ```
  HF_TOKEN=hf_xxx
  ```
  *(Replace `hf_xxx` with your actual token.)*

### 2. Prepare Your Environment

- Ensure your `.env` file also contains:
  ```
  OPENAI_API_KEY=your_openai_key
  PUSHOVER_USER=your_pushover_user
  PUSHOVER_TOKEN=your_pushover_token
  ```
- Place your LinkedIn PDF at `me/linkedin.pdf` and your summary at `me/summary.txt`.

### 3. Deploy

- Clone this repo, replace details under me/ with your resources, run:
  ```sh
  uv run gradio deploy
  ```
- If prompted for your HF token and it doesn't get picked up, interrupt with `Ctrl+C` and run:
  ```sh
  uv run dotenv -f ../.env run -- uv run gradio deploy
  ```
  This ensures all your environment variables are set.

- Follow the deployment instructions:
  - Name it `career_conversation`
  - Specify `app.py` as the entry point
  - Choose `cpu-basic` as the hardware
  - Say **Yes** to needing to supply secrets
  - Provide your OpenAI API key, Pushover user, and token
  - Say **No** to GitHub Actions

---

## 🗂️ Project Structure

- `app.py` — Main application file (Gradio chat interface)
- `me/linkedin.pdf` — Your LinkedIn profile (PDF)
- `me/summary.txt` — Your career summary (text)
- `.env` — Environment variables (API keys, tokens)

---

## 💡 Notes

- The agent uses OpenAI's function calling to record user details and unknown questions.
- Pushover is used for real-time notifications.
- All user interactions are handled through a friendly Gradio chat interface.

---

## 🔮 Future Improvements

- Integrate additional data sources (e.g., GitHub, personal website) for richer context.
- Expand notification options beyond Pushover.
- Create more friendly version, with updated contents
- Create a workflow to deploy this to HuggingFace instead of manual updates