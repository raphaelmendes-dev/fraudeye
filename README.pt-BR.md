<div align="center">
  <img src="assets/Rs4Machine.png" alt="Rs4Machine Logo" width="380" />
  <h1>🔍 FraudEye — Rs4Machine</h1>
  <img src="assets/fraudeye.gif" alt="FraudEye Demo" width="100%" />
  <p><strong>Sistema de análise forense para documentos fiscais brasileiros (NF-e)</strong></p>
  <p>Validação determinística e avaliação de fraude com evidências para revisão operacional.</p>
  <p>
    <a href="https://fraudeye-frontend.vercel.app/fraud-eye" target="_blank"><strong>🚀 App Online</strong></a> •
    <a href="https://fraudeye-backend.onrender.com/docs" target="_blank"><strong>📡 API Docs</strong></a> •
    <a href="https://github.com/raphaelmendes-dev"><strong>GitHub</strong></a>
  </p>
  <p><em>README em <a href="README.md">English</a></em></p>
</div>

---

## 🎯 Visão Geral

O **FraudEye** é um sistema de análise forense para documentos fiscais brasileiros (NF-e / DANFE). Ele combina extração de PDF, regras determinísticas de validação e classificação orientada por evidências para apoiar a revisão humana em contextos operacionais de alto risco.

O sistema é intencionalmente limitado a lógica mensurável: valida padrões conhecidos de falha, expõe a evidência por trás de cada decisão e evita comportamento generativo opaco.

Isso é consistente com o princípio do RS4 Lab de que o humano permanece como decisor final e que toda decisão crítica deve ser auditável.

---

## 🏗️ Arquitetura

```text
fraudeye/
├── frontend/                        → Next.js 16 (Vercel)
│   └── app/
│       ├── fraud-eye/
│       │   └── page.jsx             → Orquestrador principal
│       ├── components/FraudEye/
│       │   ├── RiskMeter.jsx
│       │   ├── DropZone.jsx
│       │   ├── EvidenceCard.jsx
│       │   ├── AuditTerminal.jsx
│       │   ├── MetricPills.jsx
│       │   └── VerdictPanel.jsx
│       ├── hooks/
│       │   └── useFraudAnalysis.js
│       ├── constants/
│       │   └── tokens.js            → Tokens de design da Rs4Machine
│       └── styles/
│           └── fraudeye.css
└── backend/                         → Python + FastAPI (Render)
    ├── api.py                       → Endpoints principais
    ├── requirements.txt
    └── core/
        ├── validators.py            → Lógica antifraude
        └── scorer.py                → Cálculo do Risk Score
```

---

## ✨ Funcionalidades

- Upload de PDF (NF-e / DANFE / contratos)
- Extração de texto com `pdfplumber`
- Validações determinísticas:
  - CNPJ/CPF — dígito verificador oficial
  - Datas retroativas ou suspeitas
  - Chave NF-e ausente (44 dígitos)
  - Inconsistência de soma (itens vs total)
- Risk Score 0–100 com gauge animado
- Painel de evidências com severidade (critical / high / medium / low)
- Terminal de auditoria em tempo real
- Laudo forense automático

---

## 🛠️ Stack Técnica

| Camada | Tecnologia |
|---|---|
| Frontend | Next.js 16 + React |
| Estilo | CSS-in-JS + tokens de design da Rs4Machine |
| Backend | Python 3.12+ + FastAPI + uvicorn |
| Extração | pdfplumber |
| Validação | re, unicodedata, pandas |
| Deploy Frontend | Vercel |
| Deploy Backend | Render |

---

## 🚀 Como Rodar Localmente

### Backend

```bash
cd backend
python -m venv venv
venv\Scripts\activate      # Windows
pip install -r requirements.txt
uvicorn api:app --reload
```

API disponível em: `http://localhost:8000/docs`

### Frontend

```bash
cd frontend
npm install
npm run dev
```

App disponível em: `http://localhost:3000/fraud-eye`

> Rode os dois terminais ao mesmo tempo.

---

## 📡 Endpoints da API

| Método | Rota | Descrição |
|---|---|---|
| GET | `/` | Health check |
| GET | `/health` | Status da API |
| POST | `/analyze` | Análise de documento PDF |

---

## 📬 Contato

**Raphael Mendes**  
**AI Systems Engineer & Founder · Rs4Machine**

- 📧 [python.dev.raphael@gmail.com](mailto:python.dev.raphael@gmail.com)
- 🔗 [LinkedIn](https://www.linkedin.com/in/raphaelmendes-dev/)
- 🌐 [Portfolio](https://portfolio-modular-rs4-machine.vercel.app/)

---

⭐ Dê uma estrela se o projeto te ajudou.

*Última atualização: Setembro 2026*
