# Hermes Silva

Goiânia, Brasil · 40 anos em TI

Comecei em infraestrutura, passei por COBOL e Assembly, construí sistemas de alto
volume em .NET, e hoje trabalho com sistemas de baixo nível e modernização de
legado em mainframe.

O fio comum entre os projetos abaixo: C, C++ e Rust, sem framework, com o número
medido no README.

---

## TootegaEngine

Engine de inferência para modelos MoE, escrito em C. 10.900 linhas, 28 arquivos,
sem dependência externa.

- Forward verificado contra oráculo independente em numpy: **32/32 tokens idênticos**
- Logits **byte-idênticos** de 1 a 24 threads — a ordem de redução é fixa, então o
  número de threads muda o tempo e nada mais
- Tokenizer conferido contra a implementação da HuggingFace: **36/36 casos exatos**
- Quantização int4 com busca de escala: **−11,9%** de erro relativo no matmul, sem
  mudança de formato nem de kernel

Cada kernel otimizado tem uma implementação de referência ao lado, e a versão SIMD
só entra em uso se reproduzir a referência. Os comentários do código citam o
documento que justifica cada decisão numérica.

- Código: https://github.com/HermesSilva/TootegaInference
- Modelo quantizado e medições completas:
  https://huggingface.co/HermesX21/GLM-4.7-Flash-tootega-int4

## fastdel

Apaga árvores de arquivos no Windows na velocidade que o `rm -rf` tem no Linux.
Escrito em Rust.

Nasceu de um trabalho real do Explorer: 851.552 itens, 88,7 GB, estimativa de
8h30, travado em 2%.

Medido em árvore sintética de 150.000 arquivos: **2,32 s** contra 3,72 s do
`rmdir /s /q` — 64.732 arquivos por segundo.

https://github.com/HermesSilva/PastDel

## Tootega Windows Tools

Utilitários nativos, extensões de shell e ferramentas de sistema em C++17/20, com
CRT ligado estaticamente. Win32, COM, shell namespace, Media Foundation, ODBC e CNG.

Três extensões do Explorer que transformam arquivos opacos em pastas navegáveis:
`.7z`, bancos SQLite e arquivos `.mdf` do SQL Server LocalDB. Mais um aplicativo de
captura e edição de vídeo sobre Media Foundation.

https://github.com/HermesSilva/TootegaWinTools

## DataCrusher

Motor de Change Data Capture para PostgreSQL, em C++20. Assina o WAL por logical
decoding (`pgoutput`), captura INSERT, UPDATE, DELETE e TRUNCATE, e grava journal
imutável com `COPY FROM STDIN`. Sem ORM, sem middleware, sem broker externo.

https://github.com/HermesSilva/CDC

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

## Ferramentas para agentes de IA

- **DASE-MCP** — 43 ferramentas MCP que dão a um agente controle do diagrama ORM
  aberto no DASE
- **LocalDB-MCP** — servidor MCP em Rust para SQL Server LocalDB; binário único,
  sem runtime externo
- **Cockpit** / **Cockpit4VS** — interface para o Claude Code CLI no VS Code e no
  Visual Studio

## Contato

LinkedIn: https://www.linkedin.com/in/hermesjsilva/
