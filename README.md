# Trabalho Prático --- Inteligência Artificial (FACOM/UFMS, 2026/1)

**Aluno:** _Anderson Moreira Cordeiro_
**Matrícula:** _202606598_
**Nível:** _Mestrado_
**Tema da coleção:** _maritime-target-detection_

## Estrutura do repositório

```
.. ├── README.md 
   ├── requirements.txt 
   ├── LINKS.txt 
   │ 
   ├── data/ 
   │   ├── arxiv_raw.jsonl 
   │   └── corpus.jsonl 
   │ 
   ├── notebooks/ 
   │   ├── 01_coleta_arxiv.ipynb 
   │   ├── 02_baseline_bm25.ipynb 
   │   ├── 03_retrieval_knn.ipynb 
   │   ├── 04_modulo_aprofundamento.ipynb 
   │   └── runs/ 
   │       ├── bm25.trec 
   │       ├── knn.trec 
   │       └── hybrid.trec 
   └── hybrid.trec 
   │    ├── eval/ 
        ├── queries.tsv 
        ├── qrels.tsv 
        └── evaluate.py
```

## Reprodução

```bash
# 1. Criar ambiente e instalar dependências
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# 2. Coletar dados (ajuste as palavras-chave no notebook 01)
jupyter notebook notebooks/01_coleta_arxiv.ipynb

# 3. Rodar o baseline BM25
jupyter notebook notebooks/02_baseline_bm25.ipynb

# 4. Rodar avaliação
python eval/evaluate.py \
    --qrels eval/qrels.tsv \
    --runs notebooks/runs/bm25.trec notebooks/runs/knn.trec \
    --k 10
```

## Decisões de projeto

_(Coleção de aproximadamente 2.000 artigos do ArXiv (2018–2026), pré-processamento com normalização, tokenização e remoção de stopwords, BM25 como baseline, recuperação vetorial com TF-IDF e Similaridade do Cosseno, ranking híbrido baseado em RRF e avaliação por meio de qrels manuais e métricas P@10, R@10, MAP e nDCG@10.)_

- **Tema/escopo da coleção:** artigos científicos relacionados à detecção e ao reconhecimento de alvos marítimos utilizando Inteligência Artificial, com foco em vigilância marítima, busca e salvamento (SAR), visão computacional, sensores EO/IR, radares e aprendizado de máquina.
- **Categorias do ArXiv consideradas:** cs.AI (Artificial Intelligence), cs.CV (Computer Vision and Pattern Recognition), cs.LG (Machine Learning), eess.IV (Image and Video Processing) e eess.SP (Signal Processing).
- **Janela temporal:** 2018 a 2026.
- **Tamanho final da coleção:** aproximadamente 2.000 artigos científicos coletados do ArXiv e utilizados nos experimentos de recuperação e avaliação.
- **Pré-processamento:** conversão para letras minúsculas, remoção de caracteres não relevantes, tokenização por expressões regulares e remoção de stopwords da língua inglesa com NLTK; não foram aplicados stemming ou lematização. 
- **Modelos implementados:** BM25 como baseline probabilístico, KNN com representação TF-IDF e Similaridade do Cosseno, e modelo híbrido baseado em Reciprocal Rank Fusion (RRF).
- **Módulo(s) de aprofundamento:** M5 – Ranking Híbrido, implementado por meio da técnica Reciprocal Rank Fusion (RRF) para combinar os rankings gerados pelos recuperadores BM25 e KNN..

## Uso de assistentes de IA generativa

_(Foi utilizada IA Generativa (ChatGPT) como apoio à escrita e revisão textual do relatório, organização da estrutura do artigo, esclarecimento de conceitos de Recuperação de Informação, auxílio na implementação e depuração de trechos de código, além de sugestões para configuração dos experimentos e documentação do projeto. As decisões técnicas, implementação, coleta de dados, avaliação experimental e interpretação dos resultados foram realizadas pelo autor.)_

## Vídeo de apresentação

URL: _https://..._
Não consegui realizar a gravação do vídeo de apresentação dentro do prazo devido ao meu envolvimento em uma viagem de trabalho durante o período de conclusão da disciplina. Mesmo assim, procurei garantir a entrega completa do projeto, incluindo coleta dos dados, implementação dos modelos, avaliação experimental, documentação do código e elaboração do relatório final.