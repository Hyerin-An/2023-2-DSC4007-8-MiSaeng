## 2023-2-DSC4007-8-MiSaeng
2023-2 동국대학교 데이터사이언스 캡스톤디자인 8조 

## 💊Introduction
주제 : 기존 약물의 기타 질병치료로의 활용 가능성 확장(약물 재창출)

## 👩🏻‍💻팀원
- 미디어커뮤니케이션학과 안혜린
- 생명과학과 김예원
- 생명과학과 이성경
- 생명과학과 전진아

## 📊분석 데이터
데이터 출처 : 생물 지식 그래프 오픈 네트워크 [HETIONET](https://github.com/hetio/hetionet)

<img src= "https://het.io/about/metagraph.png" width = 300>

➡️이 중 compound, gene, disease의 세 노드와 서로 연관된 엣지만을 이용합니다.

###### 약물(compound)은 유전자(gene)의 발현을 up/down시키거나(upregulates/downregulates), 단백질에 결합(binds)합니다.

###### 질병(disease)은 유전자(gene)의 발현을 up/down시키거나(upregulates/downregulates), 의학적으로 관련(associates)이 있습니다.

###### 약물(compound)은 질병(disease)을 완화(palliates)시키거나 치료(treats)합니다.

###### 약물은 화학적으로 서로 유사한(resembles) 약물이 있으며, 질병은 화학적으로 서로 유사한 질병(resembles)이 있습니다.

###### 유전자(gene)는 서로 유사한 진화적 변화를 겪었거나(covaries), 서로 상호작용하는 단백질을 생성하거나(interacts), 다른 유전자 발현에 관여(regulates)합니다.


## 💡"유사한 유전자는 유사한 기능을 공유한다"
생물학적으로 유사한 유전자는 유사한 기능을 공유합니다.  
우리는 데이터 내 약물의 유전자와의 관계, 그 유전자의 관계들을 이용해  
약물의 기존에 밝혀진 질병 치료뿐만 아니라 ***데이터 내 기타 질병 치료로의 활용 가능성***을 확인하는 것을 목표로 합니다.


## [Node2Vec](https://github.com/aditya-grover/node2vec)
Node2Vec은 그래프 데이터 내의 약물, 유전자, 질병의 관계를 이용해 임베딩할 수 있도록 하는 알고리즘입니다.  
word2vec은 문장 안에서 단어 사이의 유사도를 이용해 임베딩한다면  
node2vec은 그래프 안에서 다른 노드와의 관계를 이용해 노드를 저차원의 벡터 공간으로 투영시켜 임베딩합니다.

## ⏩진행방향
node2vec은 random walk로 그래프 내의 노드를 랜덤하게 이동해서 노드를 임베딩합니다.  
우리는 파라미터를 조정해 완전 무작위 학습이 아닌, 필요한 정보를 이용해 노드 임베딩을 하는 것을 목표로 합니다.  
임베딩된 각각의 약물, 질병 임베딩 값을 한 쌍으로 결합한 벡터를 input으로, 치료/완화 관계가 있는지 없는지의 2class classification을 진행합니다.


<img src="https://github.com/CSID-DGU/2023-2-DSC4007-8-MiSaeng/files/14799742/drug.table.pdf">


