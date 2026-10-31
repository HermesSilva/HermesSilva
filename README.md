# Hermes Silva

Goiânia, Brasil · 40 anos em TI · trabalho remoto

Comecei em infraestrutura, passei por COBOL e Assembly, construí sistemas de alto volume em .NET, e hoje trabalho com sistemas de baixo nível, ERP e modernização de legado em mainframe.

O fio comum entre os projetos abaixo: código sem atalho, comportamento verificado, e o número medido no README — não o prometido.

> **Aberto a novas oportunidades** como Engenheiro de Software Sênior, especialmente em modernização de legado (COBOL/mainframe, .NET Framework → .NET moderno, Oracle → PostgreSQL), sistemas de baixo nível e integração com IA. Remoto, CLT ou PJ.

<details>
<summary><b>English summary</b></summary>

Senior software engineer based in Brazil, available for remote work. Four decades across infrastructure, COBOL, Assembly, high-volume .NET systems, Windows internals and, today, low-level systems and mainframe legacy modernization (z/OS, CICS, Db2). I build things end to end and measure them: an LLM inference engine in C, Windows system tools in C++/Rust, a PostgreSQL CDC engine, a multi-tenant SaaS ERP, and MCP tools for AI agents. Fluent in learning new stacks fast; I've been teaching developers since the mid-1990s. Open to senior roles in modernization, systems programming and AI integration.

</details>

---

## O que eu faço bem

- **Modernização de legado** — entender o sistema antigo antes de mexer nele: testes de caracterização, exposição como serviço sem recompilar o original, migração incremental
- **Sistemas de baixo nível** — C, C++17/20 e Rust no Windows: Win32, COM, shell namespace, Media Foundation, ODBC, CNG
- **Sistemas de negócio** — ERP multi-tenant em .NET, fiscal brasileiro (NF-e, NFC-e, NFS-e, Reforma Tributária), integrações bancárias
- **IA aplicada à engenharia** — inferência em CPU, servidores MCP, agentes integrados ao fluxo de desenvolvimento
- **Ensinar** — dou treinamento técnico desde meados dos anos 1990

---

## TootegaEngine

Engine de inferência para modelos MoE, escrito em C. 10.900 linhas, 28 arquivos, sem dependência externa.

- Forward verificado contra oráculo independente em numpy: **32/32 tokens idênticos**
- Logits **byte-idênticos** de 1 a 24 threads — a ordem de redução é fixa, então o número de threads muda o tempo e nada mais
- Tokenizer conferido contra a implementação da HuggingFace: **36/36 casos exatos**
- Quantização int4 com busca de escala: **−11,9%** de erro relativo no matmul, sem mudança de formato nem de kernel

Cada kernel otimizado tem uma implementação de referência ao lado, e a versão SIMD só entra em uso se reproduzir a referência. Os comentários do código citam o documento que justifica cada decisão numérica.

- Código: https://github.com/HermesSilva/TootegaInference
- Modelo quantizado e medições completas: https://huggingface.co/HermesX21/GLM-4.7-Flash-tootega-int4

## Modernização de legado em mainframe

Laboratório em z/OS 3.1, CICS TS 6.1, Db2 13.

- CRUD em COBOL + Db2, versão batch (JCL, precompile, bind, plan/package) e versão CICS com tela BMS pseudo-conversacional
- Exposição do sistema como serviço JSON nativo do CICS — pipeline JSON, wsbind gerado por DFHLS2JS e Link3270 bridge — **sem alterar nem recompilar o programa original**
- Em andamento: mesma técnica aplicada ao CardDemo (aplicação de cartão de crédito em COBOL/CICS/VSAM/JCL publicada pela AWS), com testes de caracterização antes de qualquer mudança

## TootegaERP · Master Sist

ERP SaaS multi-tenant para pequenas e médias empresas brasileiras, em produto comercial como [Master Sist](https://mastersist.com.br). .NET 9, C#, EF Core, MySQL.

- Emissão de NF-e, NFC-e e NFS-e Nacional, com integrações SEFAZ
- Camada de conformidade para a Reforma Tributária (LC 214/2025): classificação IBS/CBS/IS assistida por IA, como serviço assíncrono com contrato OpenAPI
- Módulo financeiro com integração bancária: Pix, boleto registrado, CNAB 240/400, Open Finance
- **Jaci** — assistente de IA embutido que ajuda o usuário dentro do sistema, respeitando o perfil de acesso de cada um

## fastdel

Apaga árvores de arquivos no Windows na velocidade que o `rm -rf` tem no Linux. Escrito em Rust.

Nasceu de um trabalho real do Explorer: 851.552 itens, 88,7 GB, estimativa de 8h30, travado em 2%.

Medido em árvore sintética de 150.000 arquivos: **2,32 s** contra 3,72 s do `rmdir /s /q` — 64.732 arquivos por segundo.

https://github.com/HermesSilva/PastDel

## Tootega Windows Tools

Utilitários nativos, extensões de shell e ferramentas de sistema em C++17/20, com CRT ligado estaticamente. Win32, COM, shell namespace, Media Foundation, ODBC e CNG.

Três extensões do Explorer que transformam arquivos opacos em pastas navegáveis: `.7z`, bancos SQLite e arquivos `.mdf` do SQL Server LocalDB. Mais um aplicativo de captura e edição de vídeo sobre Media Foundation.

https://github.com/HermesSilva/TootegaWinTools

## DataCrusher

Motor de Change Data Capture para PostgreSQL, em C++20. Assina o WAL por logical decoding (`pgoutput`), captura INSERT, UPDATE, DELETE e TRUNCATE, e grava journal imutável com `COPY FROM STDIN`. Sem ORM, sem middleware, sem broker externo.

https://github.com/HermesSilva/CDC

## Tootega AIAD

Projeto de CAD/CAE em que o usuário e a IA operam o mesmo modelo — o agente não descreve a peça, ele trabalha nela junto com você. Em desenvolvimento ativo.

https://github.com/HermesSilva/TootegaAIAD

## Ferramentas para agentes de IA e desenvolvedores

Publicadas como open source gratuito no VS Code Marketplace (publisher **Hermes Silva**):

- **Tootega Cockpit** / **Cockpit4VS** — interface para o Claude Code CLI no VS Code e no Visual Studio
- **DASE ORM Designer MCP** — 43 ferramentas MCP que dão a um agente controle do diagrama ORM aberto no DASE
- **MSSQL LocalDB MCP** — servidor MCP em Rust para SQL Server LocalDB; binário único, sem runtime externo
- **Nheengetá Notebook** e **Tootega AsciiDoc**

---

## Stack

`C` · `C++17/20` · `Rust` · `C#` · `.NET 9` · `.NET Framework` · `COBOL` · `JCL` · `CICS` · `Db2` · `z/OS` · `PostgreSQL` · `MySQL` · `SQL Server` · `Oracle` · `Win32/COM` · `MCP` · `React`

## Vamos conversar

Se o seu time precisa de alguém que entenda o sistema antigo, construa o novo e consiga explicar os dois — me chame.

LinkedIn: https://www.linkedin.com/in/hermesjsilva/
