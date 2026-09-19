# 🎧 Audio Summarizer using Hugging Face and Gradio

This project converts an **audio file into text** and then creates a **short summary** of that text.

The final summary is generated in **Telugu**.

## 🚀 How It Works

The project has 3 main steps:

```text
Audio File
    ↓
Whisper
    ↓
Text / Transcript
    ↓
Llama 3.2
    ↓
Summary in Telugu
```

### 1. 🎤 Upload Audio

You upload an audio file using the Gradio interface.

### 2. 📝 Speech to Text

The project uses **OpenAI Whisper Medium English** to convert the audio into text.

```text
openai/whisper-medium.en
```

Whisper is configured to handle longer audio using 30-second chunks and timestamps.

### 3. 🤖 Generate Summary

The transcript is sent to:

```text
meta-llama/Llama-3.2-3B-Instruct
```

Llama reads the transcript and generates:

* Short summary
* Important points
* Key conclusions

The output is requested in **Telugu**.

### 4. 🖥️ Gradio Interface

Gradio provides a simple web interface where you can:

1. Upload an audio file
2. Wait for processing
3. Get the transcript
4. Get the summary

## 🛠️ Technologies Used

* **Python**
* **Google Colab**
* **Hugging Face Transformers**
* **Whisper**
* **Llama 3.2**
* **Gradio**
* **PyTorch**
* **BitsAndBytes**
* **Librosa**
* **SoundFile**

## 📦 Installation

Install the required libraries:

```bash
pip install transformers accelerate bitsandbytes gradio librosa soundfile huggingface_hub
```

These are the packages used in the project.

## 🔑 Hugging Face Token

This project uses a Hugging Face token to access the Llama model.

In Google Colab, add your token as:

```text
HF_TOKEN
```

The notebook reads the token and logs in to Hugging Face.

**Important:** Never put your Hugging Face token directly inside the GitHub code.

## ⚡ Model Quantization

Llama is loaded using **4-bit quantization** to reduce memory usage.

The project uses:

```text
4-bit quantization
NF4
Double Quantization
Float16 computation
```

This is configured using `BitsAndBytesConfig`.

## 📂 Project Flow

The main functions are:

```text
transcribe_audio()
        ↓
summarize_text()
        ↓
audio_summarizer()
```

### `transcribe_audio()`

Converts the uploaded audio into text using Whisper.

### `summarize_text()`

Sends the transcript to Llama and generates the summary.

### `audio_summarizer()`

Combines transcription and summarization into one process.

## ▶️ Run the Project

The project is designed to run in **Google Colab with a GPU**.

The notebook was configured with a **T4 GPU**.

Run the cells from top to bottom.

At the end, Gradio creates a web interface for uploading audio.

## 📌 Example

### Input

An English audio recording such as:

```text
A podcast
A lecture
A meeting
An interview
```

### Output

The application provides:

```text
TRANSCRIPT
==========

Converted audio text...


SUMMARY
=======

సంక్షిప్త సారాంశం...

ముఖ్యమైన పాయింట్లు...

ముఖ్య నిర్ణయాలు...
```

## 🎯 Purpose

This project demonstrates how to combine:

**Speech Recognition + Large Language Models + Generative AI + Gradio**

to build a simple AI-powered audio summarization application.

## 👨‍💻 Author

**Nethra910**

GitHub:
https://github.com/Nethra910

## ⭐ Future Improvements

Possible improvements:

* Support more languages
* Support more audio formats
* Improve Telugu summary quality
* Add English/Telugu language selection
* Add downloadable summaries
* Deploy the application on Hugging Face Spaces
