# RAG(Retrieval-Augmented Generation) Q&A

## 1. RAG의 의미

**Q: RAG에서 R, A, G는 각각 무슨 의미인가요?**

A:
- R: Retrieval (검색)
- A: Augmented (증강)
- G: Generation (생성)

RAG는 "검색으로 증강된 생성"을 의미합니다.

## 2. RAG 파이프라인

**Q: RAG 파이프라인의 기본 단계는 무엇인가요?**

A: RAG 파이프라인의 기본 단계는 다음과 같습니다:
1. Load Data
2. Text Split
3. Indexing
4. Retrieval
5. Generation

**Q: 이 과정을 간단히 설명할 수 있나요?**

A: 네, 다음과 같이 설명할 수 있습니다:
1. 데이터 읽기
2. 문서 나누기
3. 문서 내 데이터 벡터화하기
4. 벡터화한 문서(또는 텍스트)에서 사용자가 원하는 내용 검색하기
5. 검색한 내용 생성하기

## 3. WebBaseLoader와 load() 메서드

**Q: WebBaseLoader()와 load()는 각각 어떤 역할을 하나요?**

A:
- `WebBaseLoader()`: 웹 페이지를 불러오는 데 필요한 설정을 준비하고, URL을 저장하며, 웹 페이지를 가져오고 처리하는 데 필요한 메서드들을 포함한 객체를 생성합니다.
- `load()`: 실제로 웹 페이지를 가져오고, 내용을 파싱하며, 그 결과를 Document 객체로 변환합니다. 이는 requests와 BeautifulSoup의 기능을 모두 수행하는 것과 유사합니다.

## 4. Indexing과 임베딩

**Q: Indexing은 임베딩과 같은 의미인가요?**

A: 정확히 같지는 않습니다.
- 임베딩: 텍스트를 벡터화하는 과정
- Indexing: 임베딩된 벡터를 효율적으로 저장하고 검색할 수 있도록 구조화하는 과정

## 5. 텍스트 분할 (Text Splitting)

**Q: RecursiveCharacterTextSplitter의 chunk_size와 chunk_overlap의 단위는 무엇인가요?**

A: 단위는 '문자(character)'입니다.
- `chunk_size = 1000`: 각 청크의 최대 길이가 1000자
- `chunk_overlap = 200`: 각 청크 사이에 200자의 중복을 허용

## 6. RunnablePassthrough()

**Q: RunnablePassthrough()는 무엇이고, 어떻게 작동하나요?**

A: RunnablePassthrough()는 입력을 받아서 그대로 출력으로 전달하는 유틸리티 클래스입니다. 주로 체인의 한 부분에서 다른 부분으로 데이터를 그대로 전달할 때 사용됩니다.

**Q: RAG Chain에서 RunnablePassthrough()는 어떤 역할을 하나요?**

A: RAG Chain에서 RunnablePassthrough()는 원래의 질문을 변경 없이 그대로 전달하는 역할을 합니다. 이를 통해 검색된 컨텍스트 정보와 함께 원래의 질문을 모델에 제공할 수 있습니다.

**Q: RunnablePassthrough()를 사용하는 주된 이유는 무엇인가요?**

A: RunnablePassthrough()를 사용하는 주된 이유는:
- 유연성 제공
- Chain의 재사용성 향상
- LangChain 파이프라인의 일관성 유지
- 입력 처리의 지연 평가 가능

이는 오류 방지보다는 코드의 유연성과 재사용성을 높이기 위한 것입니다.
