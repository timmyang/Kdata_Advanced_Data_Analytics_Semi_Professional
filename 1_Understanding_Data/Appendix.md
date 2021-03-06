최신 빅데이터 상식 (Appendix)
================

# 1\. DBMS와 SQL

## 가. DBMS

#### 1\. DBMS란 무엇인가

  - DBMS는 Data Base Management System의 약자로서 데이터베이스를 관리하여 응용 프로그램들이
    데이어베이스를 공유하며 사용할 수 있는 환경을 제공하는 소프트웨어다
  - 데이터베이스를 구축하는 틀을 제공하며, 효율적인 데이터 검색, 저장 기능 등을 제공한다
  - 대표적인 데이터베이스 관리시스템에는 Oracle, Informix, Access 등이 있다

#### 2\. 데이터베이스 관리시스템 종류

  - **관계형 DBMS**
    
      - 이 모델은 데이터를 column과 row를 이루는 하나 이상의 테이블(또는 관계)로 정리하며, 고유키(Primary
        Key)가 각 로우를 식별한다
      - Row는 레코드나 튜플로 부르며, 일반적으로 각 테이블/관계는 하나의 엔티티 타입(고객이나 제품과 같은)을 대표한다
      - Row는 그 엔티티 종류의 instance(예: “Lee” 등)를 대표하며 column은 그 instance의
        속성이 되는 값들(예: 주소나 가격)을 대표한다

  - **객체지향 DBMS**
    
      - 객체지향DB는 일반적으로 사용되는 테이블 기반의 관계형DB와 다르게 정보를 “객체” 형태로 표현하는 데이터베이스
        모델이다

  - **네트워크 DBMS**
    
      - 레코드들이 노드로, 레코드들 사이의 관계가 간선으로 표현되는 그래프를 기반으로 하는 데이터베이스 모델이다

  - **계층형 DBMS**
    
      - 트리 구조를 기반으로 하는 계층 데이터베이스 모델이다

## 나. SQL

#### 1\. SQL이란 무엇인가?

  - SQL은 Structured Query Language의 약자로, 데이터베이스를 사용할 때 데이터베이스에 접근할 수 있는
    **데이터 베이스 하부 언어**로, 단순한 질의 기능 뿐만 아니라 완전한 데이터의 정의와 조작 기능을 갖추고 있다
  - 테이블을 단위로 연산을 수행하며, **영어 문장과 비슷한 구문**으로 초보자들도 비교적 쉽게 사용할 수 있다

#### 2\. SQL 집계함수

  - **AVG:** 지정한 열의 평균 값을 반환 (수치형)
  - **COUNT:** 테이블의 특정 조건이 맞는 것의 개수를 반환 (수치형, 문자형)
  - **SUM:** 지정한 열의 총합을 반환 (수치형)
  - **STDDEV:** 지정한 열의 분산을 반환 (수치형)
  - **MIN:** 지정한 열의 가장 작은 값을 반환 (수치형)
  - **MAX:** 지정한 열의 가장 큰 값을 반환 (수치형)

#### 3\. 간단한 SQL 문장 해석

**SELECT** name, gender, salary  
**FROM** Customers  
**WHERE** age BETWEEN 20 AND 39

  - 첫 번째 줄의 SELECT는 하나 또는 그 이상의 테이블에서 데이터를 추출하는 명령어이다
      - name, gender, salary는 추출하고자하는 데이터명이다
  - FROM은 테이블을 지정해주는 명령어로서 Customers라는 테이블을 지정하고 있다
  - WHERE은 데이터를 추출하는 선택 조건식을 지정하는 명령어이다
      - age가 20과 39 사이의 데이터를 추출하는 것을 뜻한다

# 2\. Data에 관련한 기술

## 가. 개인정보 비식별 기술

  - 비식별 기술이란 데이터 셋에서 개인을 식별할 수 있는 요소를 전부 또는 일부를 삭제하거나 다른 값으로 대체하는 등의
    방법으로 개인을 알아볼 수 없도록 하는 기술을 일컫는다

#### 1\. 비식별 기술의 종류와 예

  - **데이터 마스킹:** 데이터의 길이, 유형, 형식과 같은 속성을 유지한 채, 새롭고 읽기 쉬운 데이터를 익명으로 생성하는
    기술
      - 홍길동, 35세, 서울 거주, 한국대 재학  
        **-\>** 홍xx, 35세, 서울 거주, xx대학 재학
  - **가명처리:** 개인정보 주체의 이름을 다른 이름으로 변경하는 기술, 다른 값으로 대체할 시 일정한 규칙이 노출되지
    않도록 주의해야 함
      - 홍길동, 35세, 서울거주, 한국대 재학  
        **-\>** 임꺽정, 30대, 서울거주, 국내대 재학
  - **총계처리:** 데이터의 총합 값을 보임으로서 개별 데이터의 값을 보이지 않도록 함. 단, 특정 속성을 지닌 개인으로
    구성된 단체의 속성 정보를 공개하는 것은 개인 정보를 공개하는 것과 마찬가지의 결과임으로 주의해야함
      - 임꺽정 180cm, 홍길동 170cm, 이콩쥐 160cm, 김팥쥐 150cm  
        **-\>** 물리학과 학생 키 합: 660cm, 평균키 165cm
  - **데이터값 삭제:** 데이터 공유, 개방 목적에 따라 데이터 셋에 구성된 값 중에 필요 없는 값 또는 개인식별에 중요한
    값을 삭제. 개인과 관련된 날짜 정보(자격취득일자, 합격일 등)은 연단위로 처리
      - 홍길동, 35세, 서울 거주, 한국대 졸업  
        **-\>** 35세, 서울 거주
      - 주민등록번호 901206-1234567  
        **-\>** 90년대 생, 남자
  - **데이터 범주화:** 데이터의 값을 범주의 값으로 변환하여 값을 숨김
      - 홍길동, 35세  
        **-\>** 홍씨, 30\~40세

## 나. 무결성과 레이크

#### 1\. 데이터 무결성 (Data Integrity)

  - 데이터베이스 내의 데이터에 대한 정확한 일관성, 유효성, 신뢰성을 보장하기 위해 데이터 변경/수정 시 여러 가지 제한을
    두어 데이터의 정확성을 보증하는 것을 말한다.
  - 무결성제한의 유형은 개체 무결성 (Entity Integrity), 참조 무결성 (Referential
    Integrity), 범위 무결성 (Domain Integrity)가 있다

#### 2\. 데이터 레이크 (Data Lake)

  - 수 많은 정보 속에서 의미있는 내용을 찾기 위해 방식에 상관없이 데이터를 저장하는 시스템
  - 대용량의 정형 및 비정형 데이터를 저장할 뿐만 아니라 접근도 쉽게 할 수 있는 대규모의 저장소를 의미
  - Apache Hadoop, Teradata Integrated Big Data Platform 1700 등과 같은
    플랫폼으로 구성된 솔루션 제공

# 3\. 빅데이터 분석 기술

## 가. 하둡 (Hadoop)

  - 하둡은 여러 개의 컴퓨터를 하나인 것처럼 묶어 대용량 데이터를 처리하는 기술
  - 분산파일 시스템(HDFS)을 통해 수 천대의 장비에 대용량 파일을 저장할 수 있는 기능 제공
  - 맵리듀스(Map Reduce)로 HDFS에 저장된 대용량의 데이터들을 대상으로 SQL을 이용해 사용자의 질의를 실시간으로
    처리하는 기술로 이루어짐
  - 하둡의 부족한 기능을 서로 보완하는 “하둡 에코시스템”이 등장하여 다양한 솔루션 제공

## 나. Apache Spark

  - 실시간 분산형 컴퓨팅 플랫폼으로서 Scala로 작성되어 있지만 Scala, Java, R, Python, API를 지원한다
  - In-Memory 방식으로 처리를 하기 떄문에 하둡에 비해 처리속도가 빠른 것이 특징이다

## 다. Smart Factory

  - 공장 내 설비와 기계에 사물인터넷(IoT)이 설치되어, 공정 데이터가 실시간으로 수집되고 데이터에 기반한 의사결정이
    이루어짐으로써 생산성을 국대화 할 수 있는 기술

## 라. Machine Learning & Deep Learning

  - 머신 러닝은 인공지능의 연구 분야 중 하나로, 인간의 학습 능력과 같은 기능을 컴퓨터에 실현하고자하는 기술 및 기업이다
  - 딥 러닝은 컴퓨터가 많은 데이터를 이용해 사람처럼 스스로 학습할 수 있게 하기 위하여 인공신경망(ANN:
    Artificial Neural Network) 등의 기술을 기반하여 구축한 기계 학습 기술 중 하나이다

# 4\. 기타

## 가. 데이터양의 단위

1.  바이트 (B) x 1,024  
2.  킬로바이트 (KB) x 1,024  
3.  메가바이트 (MB) x 1,024  
4.  기가바이트 (GB) x 1,024  
5.  테라바이트 (TB) x 1,024  
6.  페타바이트 (PB) x 1,024  
7.  엑사바이트 (EB) x 1,024  
8.  제타바이트 (ZB) x 1,024  
9.  요타바이트 (YB)

## 나. B2B와 B2C

#### 1\. B2B

  - 기업과 기업 사이의 거래를 기반으로 한 비즈니스 모델
  - 기업이 필요로 하는 장비, 재료나 공사입찰 등

#### 2\. B2C

  - 기업과 고객사이의 거래를 기반으로 한 비즈니스 모델
  - 이동통신사, 여행회사, 신용 카드회사, 옥션, 지마켓 등

## 다. 블록체인 (Block Chain)

  - 거래정보를 하나의 덩어리로 보고 이를 차례로 연결한 거래장부
  - 기존 금융회사의 경우 중앙 집중형 서버에 거래 기록을 보관
  - 이에 반해 블록체인은 거래에 참여하는 모든 사용자에게 거래 내역을 보내 주며 거래 때마다 이를 대조해 데이터 위조를 막는
    방식

## 라. 데이터의 유형

  - **정형데이터 (Structured)**
      - 형태(고정된 필드)가 있으며 연산이 가능
      - 주로 관계형 데이터베이스(RDBMS)에 저장됨
      - 데이터 수집 난이도가 낮고 형식이 정해져 있어 처리가 쉬운 편
      - **예시:** RDBMS, spreadsheet, csv 등
  - **반정형데이터 (Semi-structured)**
      - 형태(스키마, 메타데이터)가 있으며 연산이 불가능
      - 주로 파일로 저장됨
      - 데이터 수집 난이도가 중간, 보통 API 형태로 제공되기 때문에 데이터처리 기술(파싱)이 요구됨
      - **예시:** XML, HTML, JSON, 로그형태(웹로그, 센서 데이터) 등
  - **비정형데이터 (Unstructured)**
      - 형태가 없으며 연산이 불가능
      - 주로 NoSQL에 저장됨
      - 데이터 수집 난이도가 높음
      - 텍스트 마이닝 혹은 파일일 경우 파일을 데이터 형태로 파싱해야 하기 떄문에 수집 데이터 처리가 어려움
      - **예시:** 소셜데이터(트위터, 페이스북), 영상, 이미지, 음성, 텍스트(word, PDF) 등

# 예상문제1

#### 10번

  - **메타데이터:** 데이터에 관한 구조화된 데이터로, *다른 데이터를 설명해 주는 데이터*
  - **인덱스:** 데이터베이스 내의 데이터를 신속하게 정렬하고 탐새갛게 해주는 구조

#### 15번

  - **ERP (Enterprise Resource Planning)** - 제조 부문
      - 제조업을 포함한 다양한 비즈니스 분야에서 생산, 구매, 재고, 주문, 공급자와의 거래, 고객서비스 제공 등 주요
        프로세스 관리를 돕는 여러 모듈로 구성된 **통합** 애플리케이션 소프트웨어 패케지를 의미
      - 기업 전체를 경영자원의 효과적 이용이라는 관점에서 **통합적**으로 관리하고 경영의 효율을 기하기 위한 시스템

#### 26번

  - **난수화:** 사생활 침해를 막기 위해 개인정보를 **무작위** 처리하는 등 데이터가 본래 목적 외에 가공되고 처리되는
    것을 방지하는 기술

#### 30번

  - **신용평가(Credit Raiting):** 핀테크 분야에서 빅데이터 활용이 가장 핵심적인 분야

#### 31번

다음 중 딥러닝(Deep Learning)과 가장 관련 없는 분석 기법은?

  - LSTM(Long Short-Term Memory)
  - Autoencoder
  - **K-NN(K Nearest Neighborhood)** -\> ANN(Artifical Neural Network)
  - RNN(Recurrent Neural Network)

#### 32번

최근에 딥러닝(Deep Learning)에 대한 관심이 전 세계적으로 높아지고 있다. 딥러닝을 활용하기 위해 다양한 오픈소스가
개발되어 제공되고 있다. 다음 중 이와 가장 관련이 없는 것은?

  - Caffe
  - Tensorflow
  - **Anaconda**
  - Theano

#### 37번

  - **객체지향 DBMS:** 사용자 정의 데이터 및 멀티미디어 데이터 등 **복잡한 데이터 구조**를 표현, 관리할 수 있는
    데이터베이스 관리 시스템

주관식

#### 44번

  - **정보**는 데이터 가공 및 “상관관계” 간 이해를 통해 패턴을 인식하고 그 “의미”를 부여한 것이며, 지식을 도출하기
    위한 “재료”가 된다

#### 45번

  - 기업의 의사결정 과정을 지원하기 위해 주제 중심적으로 통합하며 시간성을 가지는 비휘발성 데이터의 집합을 **Data
    Warehouse**라고 한다

#### 46번

  - 지난 몇 년간 여러 사일로 대신 하나의 데이터 소스를 추구하는 경향이 생겼다. 전사적으로 쉽게 인사이트를 공유하는 데
    도움이 되기 때문이다. 다시 말해 별도로 정제되지 않은 “자연스로운 상태”의 아주 큰 데이터 세트인 **데이터
    레이크**

#### 48번

  - **SCM(Supply Chain Management)** 는 기업이 외부 공급업체 또는 제휴업체와 통합된 정보시스템으로
    연계하여 시간과 비용을 “최적화”시키기 위한 것으로, 자재 구매, 생산, 제고, 유통, 판매, 고객 데이터로 구성된다

# 예상문제 2

#### 22번. 다음 중 데이터 웨어하우스(DW)의 특성이 아닌 것은?

1.  데이터 주제 지향성  
2.  데이터 통합  
3.  데이터의 시계열성  
4.  데이터의 휘발성

(정답): 4번  
(해설): 비휘발성

#### 29번

  - **데이터베이스:** 여러 사람이 공유하고 사용할 목적으로 통합 관리되는 정보의 집합

#### 30번

  - 빅데이터 과제의 주된 걸림돌은 비용이 아니라 분석적 방법에 대한 이해 부족이다

#### 33\. 다음 중 전략적 통찰력을 얻기 위해 분석을 사용하는 방법으로 알맞지 “않은” 것은?

  - 기업은 일차적인 문제점을 기업 내부 분석으로 집중하고, 계층저긍로 대외적인 솔루션을 찾아가는 것이 빅데이터 분석의 일반적
    접근 방법이다

(해설): 기업 내부 분석 집중 X

#### 단답 3번

  - 빅데이터의 가치 창출 방식이 기업, 정부, 소비자에게 미치는 영향은 다양하게 나타난다. 빅데이터에서 추출된 가치는 먼저
    기업에게 혁신과 경쟁력 제고, (**생산성 향상**)을 가져다 준다.

#### 단답 5번

  - (**플랫폼**)이란 다양한 차원에서 활용되는 개념이지만, 비즈니스 측면에서는 일반적으로 “공용 활용의 목적으로 구축된
    유무형의 구조물”을 의미한다. 전에는 흔히 OS(Operation System)을 (**플랫폼**)이라고 했다.

#### 단답 6번

  - 데이터 사이언스는 정형 또는 비정형을 막론하고 인터넷, 휴대전화, 감시용 카메라 등에서 생성되는 숫자와 문자, 영상 정보
    등 다양한 유형의 데이터를 대상으로 한다. 데이터 사이언스가 기존의 통계학과 다른 점은 데이터 사이언스는
    (**총체적**) 접근법을 사용한다는 점이다.

#### 단답 7번

  - (**클라우드 컴퓨팅**)은 빅데이터 분석에 경제성을 제공해준 결정적인 기술이며, 인터넷 기반 컴퓨팅의 일종으로 정보를
    자신의 컴퓨터가 아닌 인터넷에 연결된 다른 컴퓨터로 처리하는 기술을 의미한다.

#### 단답 8번

  - 빅데이터 분석과 향후 IoT의 발전으로 데이터는 더욱 증가할 것으로 전망된다. 그리고 이렇게 모은 데이터를 개인정보로
    활용하여 새로운 비즈니스를 창출함으로써 데이터 활용의 중요성이 점점 높아질 것으로 생각된다. 그러나 개인정보는
    민감한 정보를 포함할 수 있고 잘못 취급하면 비즈니스에 큰 타격을 줄 수 있다. 따라서 개인정보 보호에 대한
    **익명화(Anonymity)** 가 요구되고 있다.

#### 단답 10번

  - **연결(Connection):** 시대의 총아 빌 게이츠도 이것의 가치 페러다임의 변화를 제대로 보지 못했고, 야후가
    구글이란 기업에 밀려난 것도 이것 때문이었다. 구글은 이것을 이용하여 정보들을 매우 정확하고 손쉽게 검색할 수 있게
    되었다.

#### 단답 13번

  - 링크드인 데이터 책임자 Sunil는 데이터를 분석하여 의미있는 결과를 도출하고 이를 적용하기 위한 능력 4가지를 무엇이라
    하는가?

  - **호기심, 직관력, 비주얼라이제이션, 커뮤니케이션**

#### 단답 14번

  - 대출금을 돌려줄지 안 돌려줄지를 그 사람의 이전의 신용행동을 근거로 판단한다. 일정기간의 대출 신청자의 신용 관련 데이터를
    확보한 후 이를 통계적으로 분석해 사람들의 부도 유형을 계산하고, 결국 이를 근거로 대출여부를 결정하는 방식은 인간의 어떤
    관점에서 바라보고 있는 것인가?

  - **행동적 관점**
