# 🩺🛡️ MedShield AI — HIPAA-Compliant Clinical Copilot

[![Streamlit App](https://static.streamlit.io/badges/streamlit_badge_black_white.svg)](https://medshield-ai-jzzal6fn3ty9govidakazx.streamlit.app/)
[![AWS Architecture](https://img.shields.io/badge/AWS-Architecture%20Spec-232F3E?logo=amazon-aws)](docs/AWS_ARCHITECTURE.md)
[![CloudFormation](https://img.shields.io/badge/IaC-CloudFormation%20Stack-FF9900?logo=amazon-aws)](infrastructure/medshield_aws_stack.yaml)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

> **Enterprise Clinical Intelligence Platform powered by Amazon Bedrock (Nova), Bedrock Guardrails, Amazon S3, and Amazon Redshift**  
> 🔗 **Live Demo URL:** [https://medshield-ai-jzzal6fn3ty9govidakazx.streamlit.app/](https://medshield-ai-jzzal6fn3ty9govidakazx.streamlit.app/)

## 🎯 What It Does
MedShield AI is a production-grade clinical copilot that helps doctors and healthcare professionals:
1. **Analyze patient charts & lab reports** using Amazon Nova via Bedrock RAG
2. **Generate structured SOAP clinical notes** (Subjective, Objective, Assessment, Plan)
3. **Query hospital-wide patient data** using natural language → Amazon Redshift (Text-to-SQL)
4. **Enforce HIPAA compliance** with Amazon Bedrock Guardrails (PHI/PII masking, anti-hallucination grounding)

## 🏗️ Architecture
```
┌──────────────────────────────────────────────────────────────────┐
│                    MedShield AI (Streamlit UI)                   │
├─────────────────────────┬────────────────────────────────────────┤
│   📄 Document Q&A       │   📊 Hospital Analytics (Text-to-SQL) │
│   Upload patient charts │   "How many diabetic patients were     │
│   Ask clinical questions│    admitted last month?"               │
├─────────────────────────┴────────────────────────────────────────┤
│                    Amazon Bedrock (boto3)                        │
│  ┌─────────────┐  ┌──────────────┐  ┌─────────────────────────┐ │
│  │ Amazon Nova │  │   Bedrock    │  │  Titan Text Embeddings  │ │
│  │ (Inference) │  │  Guardrails  │  │  v2 (Vector Embeddings) │ │
│  └─────────────┘  └──────────────┘  └─────────────────────────┘ │
├──────────────────────────────────────────────────────────────────┤
│  Amazon S3 (Document Storage)  │  Amazon Redshift Serverless    │
│  Patient charts & lab PDFs     │  Structured EHR Data Warehouse │
└──────────────────────────────────────────────────────────────────┘
```

## 🛠️ Tech Stack
| Layer | Technology |
|---|---|
| Cloud AI | Amazon Bedrock (Nova Lite, Nova Micro, Titan Embeddings v2) |
| AI Safety | Amazon Bedrock Guardrails (PHI masking, Contextual Grounding) |
| Data Warehouse | Amazon Redshift Serverless (Text-to-SQL via Redshift Data API) |
| Storage | Amazon S3 |
| Backend | Python 3.10+, boto3, botocore |
| Frontend | Streamlit, Plotly |
| Security | AWS IAM (Least Privilege), python-dotenv |

## 🚀 Quick Start
```bash
# 1. Clone & enter project
cd medshield-ai

# 2. Create virtual environment
python -m venv venv
venv\Scripts\activate

# 3. Install dependencies
pip install -r requirements.txt

# 4. Configure credentials
# Edit .env with your AWS keys

# 5. Run the app
streamlit run app.py
```

## 📋 AWS Certification Alignment
This project directly demonstrates skills from the **AWS Certified AI Practitioner (AIF-C01)** exam:
- **Domain 2:** Amazon Bedrock, Foundation Models, Prompt Engineering
- **Domain 3:** RAG, Knowledge Bases, Bedrock Agents
- **Domain 4:** Responsible AI, Guardrails, PII/PHI Protection
- **Domain 5:** IAM Security, S3 Encryption, CloudWatch Monitoring

## 📄 License
MIT License — Built as a portfolio project for AI Engineering roles.
