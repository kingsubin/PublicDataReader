# 소상공인시장진흥공단 상가(상권)정보 사용 가이드

[공공데이터포털](https://www.data.go.kr)에서 제공하는 오픈 API 서비스를 이용하려면 인증키가 필요합니다. 인증키를 얻기 위해서는 [공공데이터포털](https://www.data.go.kr)에 회원가입을 하고 원하는 오픈 API 서비스를 신청해야 합니다. 공공데이터포털에서 API를 신청하면 일반적으로 1~2시간 이내에 호출이 가능합니다. 그러나 일부 API의 경우 인증 절차가 24시간 이상 소요될 수 있습니다.


## 소상공인 상가업소 정보 조회 서비스

- [소상공인 상가업소 정보 조회 서비스 신청 페이지](https://www.data.go.kr/tcs/dss/selectApiDataDetailView.do?publicDataPk=15012005)

<div align="center">

| **서비스 이름**               | **인자 이름** |
| -------------------------- | -------------- |
| 지정 상권조회              | 지정상권       |
| 반경내 상권조회            | 반경상권       |
| 사각형내 상권조회          | 사각형상권     |
| 행정구역 단위 상권조회     | 행정구역상권   |
| 단일 상가업소 조회         | 단일상가       |
| 건물단위 상가업소 조회     | 건물상가       |
| 지번단위 상가업소 조회     | 지번상가       |
| 행정동 단위 상가업소 조회  | 행정동상가     |
| 상권내 상가업소 조회       | 상권상가       |
| 반경내 상가업소 조회       | 반경상가       |
| 사각형내 상가업소 조회     | 사각형상가     |
| 다각형내 상가업소 조회     | 다각형상가     |
| 업종별 상가업소 조회       | 업종별상가     |
| 수정일자기준 상가업소 조회 | 수정일자상가   |
| 상권정보 업종 대분류 조회  | 업종대분류     |
| 상권정보 업종 중분류 조회  | 업종중분류     |
| 상권정보 업종 소분류 조회  | 업종소분류     |

<br>


</div>

```python
# 상가업소 정보 조회 클래스 임포트하기
from PublicDataReader import SmallShop

# 공공 데이터 포털 오픈 API 서비스 인증키 입력하기
service_key = "공공 데이터 포털에서 발급받은 서비스 키"

# 데이터 조회 API 인스턴스 만들기
api = SmallShop(service_key)

# 서비스 별 데이터 조회하기

## 지정 상권조회
df = api.get_data(
    service_name = "지정상권",
    key = "9301",
)

## 반경내 상권조회
df = api.get_data(
    service_name = "반경상권",
    cx = 127.042325940821,
    cy = 37.5272105674053,
    radius = 500,
)

## 사각형내 상권조회
df = api.get_data(
    service_name = "사각형상권",
    minx = 127.0327683531071,
    miny = 37.495967935149146,
    maxx = 127.04268179746694,
    maxy = 37.502402894207286
)

## 행정구역 단위 상권조회
df = api.get_data(
    service_name = "행정구역상권",
    divId = 'adongCd',
    key = '1168058000'
)

## 단일 상가업소 조회
df = api.get_data(
    service_name = "단일상가",
    divId = 'adongCd',
    key = '11757465'
)

## 건물단위 상가업소 조회
df = api.get_data(
    service_name = "건물상가",
    key = '1168011000104940000004966'
)

## 지번단위 상가업소 조회
df = api.get_data(
    service_name = "지번상가",
    key = '1165010100108120002'
)

## 행정동 단위 상가업소 조회
df = api.get_data(
    service_name = "행정동상가",
    divId = 'adongCd',
    key = '1168064000',
    indsLclsCd = 'Q'
)

## 상권내 상가업소 조회
df = api.get_data(
    service_name = "상권상가",
    key = '9368',
    indsLclsCd = 'Q'
)

## 반경내 상가업소 조회
df = api.get_data(
    service_name = "반경상가",
    radius = '500',
    cx = 127.03641615737838,
    cy = 37.50059843782878,
    indsLclsCd = 'Q'
)

## 사각형내 상가업소 조회
df = api.get_data(
    service_name = "사각형상가",
    minx = 127.0327683531071,
    miny = 37.495967935149146,
    maxx = 127.04268179746694,
    maxy = 37.502402894207286,
    indsLclsCd = 'Q'
)

## 다각형내 상가업소 조회
df = api.get_data(
    service_name = "다각형상가",
    key = 'POLYGON((127.02355609555755 37.504264372557095, 127.02496157306963 37.50590702991155, 127.0270858825753 37.50486867039889, 127.02628121988377 37.503489842823114))',
    indsLclsCd = 'Q'
)

## 업종별 상가업소 조회
df = api.get_data(
    service_name = "업종별상가",
    divId = 'indsLclsCd',
    key = 'Q'
)

## 수정일자기준 상가업소 조회
df = api.get_data(
    service_name = "수정일자상가",
    key = '20200101',
    indsLclsCd = 'Q'
)

## 상권정보업종 대분류 조회
df = api.get_data(
    service_name = "업종대분류",
)

## 상권정보업종 중분류 조회
df = api.get_data(
    service_name = "업종중분류",
    indsLclsCd = 'Q'
)

## 상권정보업종 소분류 조회
df = api.get_data(
    service_name = "업종소분류",
    indsLclsCd = 'Q',
    indsMclsCd = 'Q01'
)
```

## 한국자산관리공사 공매물건 조회 서비스


<div align="center">


| **서비스명**      | **서비스(파라미터)** | **기능(파라미터)**                                                                                                                                                                                                          |
| ------------- | ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| [온비드코드조회서비스](https://www.data.go.kr/tcs/dss/selectApiDataDetailView.do?publicDataPk=15000920)    | 온비드코드         | 용도상위코드, 용도중간코드, 용도하위코드, 시도, 시군구, 읍면동, 상세주소                                                                                                                                                                            |
| [캠코공매물건조회서비스](https://www.data.go.kr/data/15000851/openapi.do)   | 캠코공매물건        | 물건목록, 공고목록, 일정, 공고기본정보, 공고공매일정, 공고첨부파일                                                                                                                                                                                |
| [이용기관공매물건조회서비스](https://www.data.go.kr/data/15000849/openapi.do) | 이용기관공매물건      | 공고목록, 물건목록, 통합공고목록, 매각공고목록, 임대공고목록, 마감임박공고목록                                                                                                                                                                          |
| [정부재산정보공개조회서비스](https://www.data.go.kr/data/15000907/openapi.do) | 정부재산정보공개      | 정부재산정보공개정보목록, 정부재산정보공개정보상세, 캠코관리재산정보공개목록정보, 캠코관리재산정보공개정보상세                                                                                                                                                            |
| [물건정보조회서비스](https://www.data.go.kr/data/15000837/openapi.do)     | 물건정보          | 통합용도별물건목록, 통합새로운물건목록, 통합마감임박물건목록, 통합수의계약가능물건목록, 통합50%체감물건목록, 통합클릭탑20물건목록, 통합관심탑20물건목록, 통합용도별물건기본정보상세, 통합용도별물건감정평가서정보상세, 통합용도별물건임대차정보상세, 통합용도별물건권리종류정보상세, 통합용도별물건공매일정상세, 통합용도별물건입찰이력상세, 통합용도별물건주주정보상세, 통합용도별물건법인현황정보상세 |

</div>

```python
import PublicDataReader as pdr
print(pdr.__version__)

# 공공 데이터 포털 OpenAPI 서비스 인증키 입력하기
serviceKey = "공공 데이터 포털에서 발급받은 서비스 키"

# OpenAPI 인스턴스 생성
API = pdr.Kamco(serviceKey)

# 사용가능한 서비스의 파라미터 값 확인
print(API.meta_dict.keys())

# 서비스 별 사용가능한 기능의 파라미터 값 확인
print(API.meta_dict['이용기관공매물건']['기능'].keys())

# 파라미터 정의
service = "캠코공매물건"
function = "물건목록"
params = {
    "DPSL_MTD_CD": "0001",
    "CTGR_HIRK_ID": "10000",
    "CTGR_HIRK_ID_MID": "10200",
    "SIDO": "서울특별시",
}

df = API.get_data(service, function, **params)
df.head()
```


## 국세청 사업자등록정보 진위확인 및 상태조회 서비스

- [국세청 사업자등록정보 진위확인 및 상태조회 서비스 신청 페이지](https://www.data.go.kr/tcs/dss/selectApiDataDetailView.do?publicDataPk=15081808)

- 사업자등록정보 진위확인 서비스

```python
import PublicDataReader as pdr
print(pdr.__version__)

# 공공 데이터 포털 OpenAPI 서비스 인증키 입력하기
serviceKey = "공공 데이터 포털에서 발급받은 서비스 키"

# OpenAPI 인스턴스 생성
API = pdr.Nts(serviceKey)

# 조회 대상 목록
businesses = [{
  'b_no': '0000000000',
  'start_dt': '20000101',
  'p_nm': '홍길동',
  'p_nm2': '',
  'b_nm': '',
  'corp_no': '',
  'b_sector': '',
  'b_type': ''},
 {'b_no': '1111111111',
  'start_dt': '20100101',
  'p_nm': '홍길동',
  'p_nm2': '',
  'b_nm': '',
  'corp_no': '',
  'b_sector': '',
  'b_type': ''},
 {'b_no': '2222222222',
  'start_dt': '20200101',
  'p_nm': '홍길동',
  'p_nm2': '',
  'b_nm': '',
  'corp_no': '',
  'b_sector': '',
  'b_type': ''
}]

# 진위확인
df = API.validate(businesses)
```

- 사업자등록정보 상태조회 서비스

```python
import PublicDataReader as pdr
print(pdr.__version__)

# 공공 데이터 포털 OpenAPI 서비스 인증키 입력하기
serviceKey = "공공 데이터 포털에서 발급받은 서비스 키"

# OpenAPI 인스턴스 생성
API = pdr.Nts(serviceKey)

# 조회 대상 목록 (사업자등록번호 리스트)
b_no = ['0000000000', '1111111111']

# 상태조회
df = API.status(b_no)
```