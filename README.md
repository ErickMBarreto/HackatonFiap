# Hackathon - FIAP - AI SECURITY ENGINE
Hackathon - Phase 05 - Pos-Tech (FIAP) / An artificial intelligence tool designed to act as an assistant Security Architect.
___

#### Hackathon - Phase 05 of Pos-Tech (FIAP)

> *... leveraging new technologies to identify and address vulnerabilities that could jeopardize the security of systems created by architects and developers.*

> *One of the key challenges is utilizing Artificial Intelligence to automatically perform threat modeling based on the STRIDE methodology from a software architecture diagram image. ...*

#
#


## Project Summary

⚙ AI SECURITY ENGINE

Automated Threat Modeling (STRIDE) using Generative Vision Language Models.
Project developed for the AI for Devs Hackathon (FIAP 2026).

💻 Overview

<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/1.png">

The AI Security Engine is an advanced Artificial Intelligence solution engineered to act as a Virtual Assistant Security Architect (vSA). The tool automates the critical threat modeling process by visually interpreting infrastructure and software architecture diagrams (AWS, Azure, GCP, On-premise) to extract actionable security insights.

The engine conducts a deep-dive analysis based on the STRIDE methodology (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service, and Elevation of Privilege), delivering a comprehensive technical report complete with attack vectors and their respective mitigations.

📢 Key Features

<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/2.png">

High-Fidelity Semantic Visual Analysis: The vision engine interprets complex architectures (Cloud and On-premise) purely through imagery. Unlike tag-based tools, this solution extracts security context without requiring underlying metadata.

STRIDE Reporting Engine: Automated generation of STRIDE-compliant technical documentation. The report consolidates asset identification, the threat matrix, and a strategic mitigation plan into an audit-ready PDF.

Scientific User Experience (UX): An intuitive graphical user interface (GUI) developed within the Google Colab environment. Designed to streamline the workflow for researchers and analysts, allowing uploads and analysis in just a few clicks.

Intelligent Bilingual Processing: The AI core consumes technical terminology using global standards (English), ensuring higher accuracy in component identification, while performing contextual translation to generate executive reports in Brazilian Portuguese (PT-BR).

🧠 Technical Architecture (Innovation)

<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/3.png">

To meet the "Model Training" requirement efficiently and scalably, we opted for a Dynamic In-Context Learning (Few-Shot Prompting) architecture.

Why Not Traditional Fine-Tuning?

Static Fine-Tuning (SFT) "freezes" the model's knowledge. In cybersecurity, where new cloud services emerge monthly, an SFT model would rapidly become obsolete.

The "In-Context" Approach

We utilize a curated dataset (`dataset_treino.json`) that is dynamically injected into the Gemini 2.5 Flash model's context at runtime.

JSON Dataset: Contains Diagram -> Ideal Analysis (Golden Master) pairs.

Injection: The system instructs the AI to use this dataset as a "reference memory."

Result: The model learns the expected analysis pattern (One-Shot/Few-Shot) without requiring heavy retraining, ensuring flexibility and low operational costs.

📂 Dataset Structure

The `dataset_treino.json` file was built using a Teacher-Student technique, where a larger model assisted in annotating real AWS and Azure diagrams.

Annotation structure example:
```json
{
    "description": "Architecture with AWS WAF and CloudFront...",
    "stride_analysis": {
        "assets": ["AWS WAF", "CloudFront", "ALB"],
        "threats": [
            {
                "category": "Denial of Service",
                "component": "ALB",
                "description": "DDoS attack overwhelming the balancer.",
                "mitigation": "Enable AWS Shield Standard..."
            }
        ]
    }
}
```


## 🛠️ How to Run

1. Clone this repository or download the files.
2. Open the notebook `AiSecurityEngine.ipynb` in Google Colab.
3. Upload the file `dataset/dataset_treino.json` to the root directory of your Colab workspace.
4. Run the cells sequentially. If you haven't uploaded the JSON file manually, the first cell will automatically download `dataset_treino.json`.
5. Enter your Google AI Studio API Key when prompted.

#### Note Regardless of the Method Used:

> The Google AI Studio API Key does not need to be on a paid plan; Google provides a free tier that is sufficient to run this application, provided you do not exceed the free usage limits:

Gemini 2.5 Flash Model:

* Maximum Requests Per Minute (RPM) = 5
* Maximum Input Tokens Per Minute (TPM) = 250K
* Maximum Requests Per Day (RPD) = 20

> This was verified on 01/23/2026.

> Just make sure to create an API key and use it within the current free limits.

#### AI Security Engine Output

> A PDF report is made available after completing these steps:

1. Click the `[Selecionar Diagrama]` (Select Diagram) button and choose your analysis file (image).
2. Click the `[INICIAR ANÁLISE ESTRATÉGICA]` (Start Strategic Analysis) button, wait for processing, and click the `[Download PDF]` button that appears at the end of the process.
