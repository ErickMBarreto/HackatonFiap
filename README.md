# Hackaton - FIAP - AI SECURITY ENGINE
Hackaton - Fase 05 - Pos-Tech (FIAP) / Uma ferramenta de inteligência artificial projetada para atuar como um Security Architect assistente.
___

#### Hackaton - Fase 05 da Pos-Tech (FIAP)

> *... usar de novas tecnologias para identificar e tratar
vulnerabilidades que possam colocar em risco a segurança dos sistemas criados pelos
arquitetos e desenvolvedores.*

> *Um dos desafios é utilizar a Inteligência Artificial para realizar automaticamente a modelagem de ameaças, baseado na metodologia STRIDE de um sistema a partir de um diagrama de arquitetura de software em imagem. ...*

#
#
#

## Resumo do Projeto

⚙ AI SECURITY ENGINE

Automated Threat Modeling (STRIDE) using Generative Vision Language Models.
Projeto desenvolvido para o Hackathon I.A. para Devs (FIAP 2026).

💻 Visão Geral

<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/01.png">

O AI Security Engine é uma solução avançada de Inteligência Artificial concebida para atuar como um Arquiteto de Segurança Assistente (vSA). A ferramenta automatiza o processo crítico de Threat Modeling, interpretando visualmente diagramas de infraestrutura e arquitetura de software (AWS, Azure, GCP, On-premise) para extrair insights acionáveis de segurança.

A engine realiza uma análise profunda baseada na metodologia STRIDE (Spoofing, Tampering, Repudiation, Information Disclosure, Denial of Service e Elevation of Privilege), entregando um relatório técnico detalhado com vetores de ataque e respectivas mitigações.

📢 Funcionalidades Principais

<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/02.png">

Análise Visual Semântica de Alta Fidelidade: O motor de visão interpreta arquiteturas complexas (Cloud e On-premise) puramente através da imagem. Ao contrário de ferramentas baseadas em tags, a solução extrai o contexto de segurança sem a necessidade de metadados.

Engine de Relatórios STRIDE: Geração automatizada de documentação técnica em conformidade com o STRIDE. O relatório consolida a identificação de ativos, a matriz de ameaças e o plano de mitigação estratégica em um PDF pronto para auditoria.

User Experience (UX) Científica: Interface gráfica intuitiva (GUI) desenvolvida no ambiente Google Colab. Projetada para facilitar o fluxo de trabalho de pesquisadores e analistas, permitindo o upload e a análise em poucos cliques.

Processamento Bilíngue Inteligente: O núcleo da IA consome a terminologia técnica no padrão global (Inglês), garantindo maior precisão na identificação de componentes, mas realiza a tradução contextualizada para gerar relatórios executivos em Português do Brasil (PT-BR).

🧠 Arquitetura Técnica (Inovação)


<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/03.png">

Para atender ao requisito de "Treinamento do Modelo" de forma eficiente e escalável, optamos pela arquitetura de Dynamic In-Context Learning (Few-Shot Prompting).

Por que não Fine-Tuning Tradicional?

O Fine-Tuning estático (SFT) "congela" o conhecimento do modelo. Em segurança cibernética, onde novos serviços de nuvem surgem mensalmente, um modelo SFT ficaria obsoleto rapidamente.

A Abordagem "In-Context"

Utilizamos um dataset curado (dataset_treino_completo.json) que é injetado dinamicamente no contexto do modelo Gemini 2.5 Flash em tempo de execução.

Dataset JSON: Contém pares de Diagrama -> Análise Ideal (Golden Master).

Injeção: O sistema instrui a IA a usar esse dataset como "memória de referência".

Resultado: O modelo aprende o padrão de análise esperado (One-Shot/Few-Shot) sem a necessidade de re-treinamento pesado, garantindo flexibilidade e baixo custo.

📂 Estrutura do Dataset

O arquivo dataset_treino.json foi construído utilizando uma técnica de Teacher-Student, onde um modelo maior auxiliou na anotação de diagramas reais da AWS e Azure.

Exemplo de estrutura de anotação:
```
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

#
#
#

## 🛠️ Como Executar

<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/04.png">


1. Clone este repositório ou baixe os arquivos.

2. Abra o notebook [AiSecurityEngine.ipynb] no Google Colab.

3. Faça o upload do arquivo [dataset/dataset_treino.json] para a raiz do Colab.

4. Execute as células sequencialmente. Caso não tenha feito o upload do json, a primeira célula baixará o arquivo [dataset_treino.json]

5. Insira sua Google AI Studio API Key quando solicitado.

#### Observação Independente do Método Usado:
> A Google AI Studio API Key, não precisa ser em um plano pago; a Google disponibiliza uma utilização gratuita o suficiente para executar esta aplicação, desde que você não ultrapasse os limites gratuitos de utilização:

Modelo gemini-2.5-flash:

* Máximo de solicitações por minuto (RPM) = 5.
* Máximo de tokens de entrada por minuto (TPM) = 250K.
* Máximo de solicitações por dia (RPD) = 20.
 
> Isso foi verificado em 23/01/2026.

> Apenas atente que você tem que criar uma api-key e usá-la aqui dentros dos limites gratuitos vigentes.

#### Saída do Ai Security Engine

> Um relatório em formato PDF é disponibilizado após:

1. Clicar no botão [Selecionar Diagrama] e escolher seu aruqivo de análise (imagem). 
2. Clicar no botão [INICIAR ANÁLISE ESTRATÉGICA], aguardar o processamento e clicar no botão [Download PDF] que aparece no fim do processo.

<img src="https://raw.githubusercontent.com/ErickMBarreto/HackatonFiap/refs/heads/main/assets/report.png">


