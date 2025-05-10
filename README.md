# Blog GPT: AI-Powered Multilingual Blog Generator

## Overview

**Blog GPT** is a serverless web application that enables users to generate AI-written blog content on custom topics and translate it into multiple languages. Designed for content creators, marketers, and organizations aiming to scale their global content outreach, Blog GPT utilizes modern AWS services to automate content generation and multilingual publishing.

---

## Features

* ✨ **AI-Powered Blog Generation**: Generates high-quality, structured blog posts using foundational models via Amazon Bedrock.
* 🌐 **Multilingual Support**: Automatically translates blog content into selected languages using AWS Translate.
* 💡 **Simple UI**: Lightweight frontend (HTML/JS) for entering prompts and displaying results.
* ⚡ **Serverless Architecture**: Built with AWS Lambda and API Gateway for efficient, scalable processing.
* 📂 **Cloud Storage**: Stores original and translated blog content in Amazon S3 with secure pre-signed URLs.
* 🔄 **Extensible Design**: Modular Lambda functions allow for easy enhancements like PDF export, tone control, or category targeting.

---

## System Architecture

### High-Level Flow

1. User inputs a blog topic and selects a target language (optional).
2. Frontend sends a request to API Gateway.
3. API Gateway triggers a Lambda function.
4. Lambda uses Amazon Bedrock to generate content.
5. If selected, AWS Translate translates the content.
6. Lambda saves the final blog to S3.
7. A pre-signed URL and content are returned to the frontend.

### AWS Services Used

* **Amazon API Gateway**: Handles HTTP requests securely.
* **AWS Lambda**: Contains logic for content generation and translation.
* **Amazon Bedrock**: Provides access to foundational models (e.g., Claude, Titan).
* **AWS Translate**: Translates the generated content.
* **Amazon S3**: Stores original and translated blog content.
* **IAM**: Manages permissions and access control.

---

## Project Structure

```
blog-gpt/
├── frontend/
│   ├── index.html
│   ├── script.js
│   └── styles.css
├── backend/
│   └── lambda_function.py
├── architecture/
│   └── diagram.png
└── README.md
```

---

## Setup Instructions

### Prerequisites

* AWS account
* IAM user with permissions for Lambda, API Gateway, Bedrock, Translate, and S3
* AWS CLI configured

### 1. Clone the Repository

```bash
git clone https://github.com/SanskarSharma1008/blog-gpt.git
cd blog-gpt
```

### 2. Deploy Backend

* Create an S3 bucket for storing blog outputs
* Create a Lambda function from `lambda_function.py`
* Configure API Gateway to trigger the Lambda
* Grant Lambda permissions for Bedrock, Translate, and S3 via IAM Role

### 3. Launch Frontend

* Open `frontend/index.html` in a browser
* Use local server (`Live Server` extension or Python HTTP server)

---

## Lambda Function Responsibilities

* Receives POST request with blog prompt and language
* Calls Amazon Bedrock with custom prompt template
* Optionally calls AWS Translate for language conversion
* Stores result in S3
* Returns blog content + pre-signed URL

---

## Security

* S3 access controlled by IAM and bucket policies
* Pre-signed URLs ensure temporary and secure access
* API Gateway throttling and validation for abuse prevention
* Lambda roles restricted to necessary services only

---

## Future Enhancements

* 📉 PDF and Word export of blogs
* 🔑 User authentication via Cognito
* ⚖️ Blog tone and length control
* 🌐 Frontend hosted on S3 + CloudFront
* 💊 Add category-specific blog generation
* 📲 Mobile responsive UI

---

## Acknowledgments

* Special thanks to **Dr. Naween Kumar** for guidance throughout the project
* Gratitude to **School of CSET, Bennett University** and **Prof. (Dr.) Abhay Bansal** for their support and mentorship

---

## License

This project is licensed under the MIT License.
