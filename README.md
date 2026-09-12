# Hermes Silva

Goiânia, Brasil · 40 anos em TI

Comecei em infraestrutura, passei por COBOL e Assembly, construí sistemas de alto
volume em .NET, e hoje trabalho com modernização de legado em mainframe.

---

## TootegaEngine

Engine de inferência para modelos MoE, escrito em C, sem framework e sem dependência
externa.

- Forward verificado contra oráculo independente em numpy: **32/32 tokens idênticos**
- Logits **byte-idênticos** de 1 a 24 threads — a ordem de redução é fixa, então o
  número de threads muda o tempo e nada mais
- Tokenizer conferido contra a implementação da HuggingFace: **36/36 casos exatos**
- Quantização int4 com busca de escala: **−11,9%** de erro relativo no matmul, sem
  mudança de formato nem de kernel

Código: https://github.com/HermesSilva/TootegaInference

Modelo quantizado e medições completas:
https://huggingface.co/HermesX21/GLM-4.7-Flash-tootega-int4

---

## Modernização de legado em mainframe

Laboratório em z/OS 3.1, CICS TS 6.1, Db2 13.

- CRUD em COBOL + Db2, versão batch (JCL, precompile, bind, plan/package) e versão
  CICS com tela BMS pseudo-conversacional
- Exposição do sistema como serviço JSON nativo do CICS — pipeline JSON, wsbind
  gerado por DFHLS2JS e Link3270 bridge — **sem alterar nem recompilar o programa
  original**
- Em andamento: mesma técnica aplicada ao CardDemo (aplicação de cartão de crédito
  em COBOL/CICS/VSAM/JCL publicada pela AWS), com testes de caracterização antes
  de qualquer mudança

---

## Outros projetos

- **Cockpit** — extensão para VS Code / Visual Studio
- **LocalDB-MCP** — servidor MCP em Rust
- **FrameworksPerformanceComparison** — comparação de desempenho entre frameworks
  de Web API

---

## Contato

LinkedIn: https://www.linkedin.com/in/hermesjsilva/
