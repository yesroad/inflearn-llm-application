# Inflearn LLM Application (학습용)

인프런 LLM 강의 실습 레포입니다.  
LangChain 기초, RAG, Streamlit 챗봇을 다룹니다.

## 프로젝트 구성

```text
.
├── 01.tutorial
│   ├── langchain_llm_test.ipynb
│   └── langchain_chatupstage.ipynb
├── 02.rag_with_chroma
│   ├── rag_with_chroma_openai.ipynb
│   ├── rag_with_chroma_upstage.ipynb
│   ├── rag_with_pinecone.ipynb
│   ├── tax.docx
│   ├── tax_with_markdown.docx
│   └── tax_with_table.docx
├── 03.streamlit
│   ├── chat.py
│   ├── llm.py
│   └── config.py
├── requirements.txt
└── runtime.txt
```

## 권장 학습 순서

1. `01.tutorial`  
   LLM 호출과 기본 체인 실습
2. `02.rag_with_chroma`  
   문서 로딩, 임베딩, 벡터 DB(Chroma/Pinecone) 기반 RAG 실습
3. `03.streamlit`  
   소득세 질의응답 챗봇 실행

## 사전 준비

- Python `3.11` (`runtime.txt` 기준)
- API 키 설정

예시 `.env`:

```bash
OPENAI_API_KEY=your_openai_api_key
PINECONE_API_KEY=your_pinecone_api_key
# Upstage 실습 시
UPSTAGE_API_KEY=your_upstage_api_key
```

## 설치

```bash
python3.11 -m venv .venv
source .venv/bin/activate
pip install -U pip
pip install -r requirements.txt
```

## 실행 방법

### 1) 노트북 실습

```bash
jupyter notebook
```

아래 순서로 실행하세요.

- `01.tutorial/langchain_llm_test.ipynb`
- `02.rag_with_chroma/rag_with_chroma_openai.ipynb`
- `02.rag_with_chroma/rag_with_pinecone.ipynb`

### 2) Streamlit 챗봇 실행

챗봇은 Pinecone 인덱스 `tax-markdown-index`를 사용합니다(`03.streamlit/llm.py`).

```bash
cd 03.streamlit
streamlit run chat.py
```

## Streamlit 앱 동작 요약

- 사용자 질문을 사전(Dictionary) 체인으로 보정
- 대화 히스토리를 반영해 독립 질문(standalone question) 생성
- Pinecone Retriever로 관련 문서 검색
- Few-shot 예시 + 검색 문맥으로 최종 답변 생성
- 세션 히스토리 기반으로 대화 맥락 유지

## 참고

- 외부 API 상태/모델 버전에 따라 응답이 달라질 수 있습니다.
- Pinecone 인덱스가 없으면 `02.rag_with_chroma/rag_with_pinecone.ipynb`를 먼저 실행하세요.

## 강의 출처

- [인프런: RAG LLM Application 개발 with LangChain](https://www.inflearn.com/course/rag-llm-application%EA%B0%9C%EB%B0%9C-langchain/dashboard?cid=333796)
