# Linkedin Scraper

[![Promo](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.co.kr/products/web-scraper/linkedin) 

이 리포지토리는 LinkedIn에서 데이터를 수집하는 두 가지 방법을 제공합니다:
1. **무료**: 소규모 프로젝트, 실험 및 학습 목적에 적합한 훌륭한 옵션입니다.
2. **LinkedIn Scraper API**: 대규모, 신뢰할 수 있으며 실시간 데이터 추출을 위해 설계되었습니다.

스크레이핑을 건너뛰고 싶으신가요? 전체 [LinkedIn dataset](https://brightdata.co.kr/products/datasets/linkedin)을 구매하실 수 있습니다.

## Table of Contents
- [Method 1: Free LinkedIn Scraper](#method-1-free-linkedin-scraper)
    - [Jobs Scraper](#1-jobs-scraper)
    - [Profile Checker](#2-profile-checker)
    - [Quick Start](#quick-start)
    - [Usage Examples](#usage-examples)
- [Common Scraping Challenges with Free Method](#common-scraping-challenges-with-free-method)
- [Method 2: Bright Data LinkedIn Scraper API](#method-2-bright-data-linkedin-scraper-api)
    - [Key Benefits](#key-benefits)
- [Getting Started with the LinkedIn Scraper API](#getting-started-with-the-linkedin-scraper-api)
  - [1. Company Information Scraper](#1-company-information-scraper)
  - [2. Profile by URL](#2-profile-by-url)
  - [3. Profile Discovery](#3-profile-discovery)
  - [4. Posts by URL](#4-posts-by-url)
  - [5. Posts Discovery by URL](#5-posts-discovery-by-url)
  - [6. Posts Discovery by Profile](#6-posts-discovery-by-profile)
  - [7. Posts Discovery by Company](#7-posts-discovery-by-company)
  - [8. Job Listings Collection by URL](#8-job-listings-collection-by-url)
  - [9. Job Listings Discovery by Keyword](#9-job-listings-discovery-by-keyword)
  - [10. Job Listings Discovery by URL](#10-job-listings-discovery-by-url)
- (More info) [Data Collection Approaches](#data-collection-approaches)

## Method 1: Free LinkedIn Scraper
이 무료 도구는 두 가지 주요 기능을 제공합니다:
1. **LinkedIn Jobs Scraper**: 포괄적인 메타데이터와 함께 채용 공고 목록을 수집합니다.
2. **LinkedIn Profile Validator**: LinkedIn 프로필 및 회사 URL을 검증합니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin-jobs" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin-jobs.png" />

### 1. Jobs Scraper
LinkedIn의 채용 검색에서 채용 공고 목록을 수집합니다.

**주요 기능**:
- 상세 채용 공고(직무명, 회사, 위치, URL, 게시 날짜)를 스크레이핑합니다.
- 내장 속도 제한 및 오류 처리
- 깔끔한 JSON 출력

### 2. Profile Checker
LinkedIn 프로필 또는 회사 페이지가 존재하는지 확인합니다.

**주요 기능**:
- 프로필/회사 URL 확인
- 실패한 요청 자동 재시도
- 각 URL에 대한 상세 상태 표시
- 여러 URL을 한 번에 확인 가능

### Quick Start
몇 분 안에 실행할 수 있도록 안내해 드리겠습니다:

#### Prerequisites
- Python 3.9 이상
- [requirements.txt](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/requirements.txt)에 나열된 필수 패키지

#### Installation
시작을 위한 간단한 3단계입니다:
```bash
git clone https://github.com/bright-kr/LinkedIn-Scraper.git
cd LinkedIn-Scraper
pip install -r requirements.txt
```
### Usage Examples
스크레이퍼를 사용하는 방법은 다음과 같습니다:

#### 1. Jobs Scraper
검색 매개변수를 구성합니다:
```python
# In jobs_scraper.py
params = {
    "keywords": "AI/ML Engineer",  # Job title/keywords to search
    "location": "London",          # Location to search in
    "max_jobs": 100               # Maximum number of jobs to collect
}

# Run: python jobs_scraper.py
```

스크레이퍼는 채용 상세 정보를 포함하는 JSON 파일을 생성합니다:
```json
{
    "title": "Research Engineer, AI/Machine Learning",
    "company": "Google",
    "location": "London, England, United Kingdom",
    "job_link": "https://uk.linkedin.com/jobs/view/research-engineer-ai-machine-learning-at-google-4086259724",
    "posted_date": "3 weeks ago",
}
```

#### 2. Profile Checker
검증할 URL을 구성합니다:
```python
# In profile_checker.py
test_urls = [
    "https://www.linkedin.com/company/bright-data/",
    "https://www.linkedin.com/company/aabbccdd/"
]

# Run: python profile_checker.py
```

각 URL에 대한 명확한 상태 표시를 확인할 수 있습니다:
```bash
✓ linkedin.com/company/bright-data - Status: 200
✗ linkedin.com/company/aabbccdd - Status: 400
```

## Common Scraping Challenges with Free Method
LinkedIn에서 데이터를 수집할 때 다양한 안티 스크레이핑 조치를 만나게 됩니다. 알아두셔야 할 내용은 다음과 같습니다:
1. **Rate Limiting**: LinkedIn은 IP 주소당 요청 빈도를 엄격하게 모니터링합니다. 이러한 제한을 초과하면 일시적 또는 영구적인 IP 차단으로 이어집니다.
2. **CAPTCHA Detection**: LinkedIn은 비정상적인 브라우징 패턴을 감지하면 CAPTCHA 챌린지를 제시하여 자동화된 접근을 차단합니다.
3. **Authentication Barriers**: 가장 가치 있는 LinkedIn 데이터의 대부분은 인증이 필요합니다. 플랫폼은 자동화된 로그인 시도를 쉽게 감지하고 차단합니다.
4. **Technical Challenges**: 추가 장벽으로는 페이지네이션 처리, 동적 콘텐츠 로딩, 불완전한 데이터 포인트, LinkedIn 광고 탐색 등이 포함됩니다.

수동 Web스크레이핑은 소규모 프로젝트에는 작동하지만, 규모가 커질수록 점점 더 어려워집니다. 신뢰할 수 있고 효율적이며 확장 가능한 LinkedIn 데이터 수집을 위해 **Bright Data**는 시간과 리소스를 절감하면서 더 높은 품질의 결과를 제공하는 우수한 솔루션을 제공합니다.

[![Promo](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/Proxies%20and%20scrapers%20GitHub%20bonus%20banner.png)](https://brightdata.co.kr/products/web-scraper/linkedin) 

## Method 2: Bright Data LinkedIn Scraper API
견고하고 확장 가능한 LinkedIn 스크레이핑 솔루션을 위해 [Bright Data LinkedIn Scraper API](https://brightdata.co.kr/products/web-scraper/linkedin)를 고려해 보시기 바랍니다. 고려할 가치가 있는 이유는 다음과 같습니다:

### Key Benefits
- **인프라 설정 불필요:** 프록시, CAPTCHA, 스로틀링을 자동으로 처리합니다.
- **확장 가능하고 신뢰할 수 있음:** 대용량 및 실시간 데이터 추출에 최적화되어 있습니다.
- **포괄적 커버리지:** 프로필, 채용, 회사, 게시물에서 데이터를 추출합니다.
- **글로벌 접근:** 모든 지역과 언어를 지원합니다.
- **개인정보 준수:** GDPR 및 CCPA 표준을 완전히 준수합니다.
- **종량제(Pay-as-You-Go):** 성공한 응답에 대해서만 비용을 지불합니다.
- **무료 체험:** 시작을 위한 무료 API 호출 20회를 포함합니다.

## Getting Started with the LinkedIn Scraper API
Bright Data LinkedIn Scraper API는 개발자가 LinkedIn 프로필, 회사, 채용 공고, 게시물의 공개 데이터를 프로그래밍 방식으로 추출할 수 있게 합니다. 이 엔터프라이즈급 솔루션은 프록시 관리, 요청 스로틀링, 데이터 파싱을 포함한 복잡한 인프라 요구사항을 처리합니다.

시작하기 전에 다음이 필요합니다:
- Bright Data 계정
    - [Start a free trial](https://brightdata.co.kr/) 후 로그인합니다.
    - **Billing** 페이지에서 결제 수단을 추가하여 계정을 활성화합니다.
- API Token
    - API token을 얻으려면 [Follow this guide](https://docs.brightdata.com/general/account/api-token)를 따르십시오.

### 1. Company Information Scraper
LinkedIn URL을 사용하여 회사에 대한 상세 데이터를 추출합니다.

<img width="797" alt="linkedin-scraper-bright-data-screenshot-linkedin-company-information-by-url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin-company-information-by-url.png" />


#### Input Parameters
| Field    | Type   | Required | Description                      |
|----------|--------|----------|----------------------------------|
| `url`      | string | Yes      | 정보를 추출할 LinkedIn 회사 URL |

#### Sample Response
```json
{
    "name": "Kraft Heinz",
    "about": "The Kraft Heinz Company is one of the largest food and beverage companies in the world, with eight $1 billion+ brands and global sales of approximately $25 billion. We're a globally trusted producer of high-quality, great-tasting, and nutritious foods for over 150 years.",
    "key_info": {
        "headquarters": "Chicago, IL",
        "founded": 2015,
        "company_size": "10,001+ employees",
        "organization_type": "Public Company",
        "industries": "Food and Beverage Services",
        "website": "https://www.careers.kraftheinz.com/",
    },
    "metrics": {"linkedin_followers": 1557451, "linkedin_employees": 25254},
    "stock_info": {
        "ticker": "KHC",
        "exchange": "NASDAQ",
        "price": "$30.52",
        "last_updated": "December 21, 2024",
    },
    "specialties": "Food, Fast Moving Consumer Packaged Goods, CPG, and Consumer Packaged Goods",
    "locations": ["200 E. Randolph St. Suite 7600 Chicago, IL 60601, US"],
    "slogan": "Let's make life delicious!",
}
```

👉 여기에는 주요 필드만 표시되어 있습니다. 전체 데이터셋은 [JSON response sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/linkedin_company_info.json)을 참조하십시오.

#### Code Example
데이터를 추출하려면 목록의 회사 URL을 수정하십시오:
```python
companies = [
    {"url": "https://il.linkedin.com/company/ibm"},
    {"url": "https://www.linkedin.com/company/stalkit"},
    {
        "url": "https://www.linkedin.com/organization-guest/company/the-kraft-heinz-company"
    },
    {"url": "https://il.linkedin.com/company/bright-data"},
]
```

👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_company_info_by_url.py) 보기

### 2. Profile by URL
개별 LinkedIn 프로필에서 상세 정보를 가져옵니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin-people-profiles-by-url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin-people-profiles-by-url.png" />

#### Input Parameters
| Parameter   | Type   | Required | Description                           |
|-------------|--------|----------|---------------------------------------|
| `url`       | string | Yes      | 데이터 추출 대상 LinkedIn 프로필 URL|

#### Sample Response
```json
{
    "name": "Richard Branson",
    "profile_info": {
        "position": "Founder at Virgin Group",
        "followers": 18730516,
        "connections": 2,
        "avatar": "https://media.licdn.com/dms/image/v2/C4D03AQHh6_Wth5f3rQ/profile-displayphoto-shrink_200_200/profile-displayphoto-shrink_200_200/0/1625181963183?e=2147483647&v=beta&t=oiGK2oBQ3r3COkRR0z62i7CbnqXKw_1ujZ9X4-SKheo",
    },
    "experience": [
        {
            "title": "Founder",
            "company": "Virgin Group",
            "duration": "Jan 1968 - Present (57 years)",
            "description": "Tie-loathing adventurer and thrill seeker, who believes in turning ideas into reality. Otherwise known as Dr Yes at Virgin!",
        }
    ],
    "current_company": {"name": "Virgin Group", "title": "Founder at Virgin Group"},
    "url": "https://www.linkedin.com/in/rbranson/",
}
```

👉 여기에는 주요 필드만 표시되어 있습니다. 전체 데이터셋은 [JSON response sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/profiles_by_url.json)을 참조하십시오.

#### Code Example
분석하려는 LinkedIn 프로필로 URL을 교체하십시오.
```python
profiles = [
    {"url": "https://www.linkedin.com/in/williamhgates"},
    {"url": "https://www.linkedin.com/in/rbranson/"},
    {"url": "https://www.linkedin.com/in/justinwelsh/"},
    {"url": "https://www.linkedin.com/in/simonsinek/"},
]
```

👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_profile_by_url.py) 보기

### 3. Profile Discovery
이름 기반 쿼리를 사용하여 LinkedIn 프로필을 검색합니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin-people-profiles-by-name" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin-people-profiles-by-name.png" />

#### Input Parameters
| Parameter     | Type   | Required | Description                                         |
|---------------|--------|----------|-----------------------------------------------------|
| `first_name`  | string | Yes      | 사용자의 이름(First name)                         |
| `last_name`   | string | Yes      | 사용자의 성(Last name)                       |

#### Sample Response
```json
{
    "profile_info": {
        "id": "richard-branson-8a38866",
        "name": "Richard Branson",
        "location": {"city": "Cincinnati", "state": "Ohio", "country": "US"},
        "about": "Respiratory therapist with 40 years of experience. Over 300 peer-reviewed publications...",
        "metrics": {"followers": 868, "connections": 500, "recommendations": 1},
    },
    "professional": {
        "current_position": {
            "company": "University of Cincinnati",
            "company_link": "https://www.linkedin.com/school/university-of-cincinnati",
        },
        "education": {
            "school": "The George Washington University School of Medicine and Health Sciences",
            "years": "2001-2003",
        },
    },
    "recommendations": [
        "Tracy OConnell Well known pro active valuable assett to the professon of respiratory care."
    ],
    "similar_professionals": [
        {
            "name": "Walter J. Jones, PhD, MHSA",
            "title": "Professor at Medical University of South Carolina",
            "location": "Mount Pleasant, SC",
        },
        {
            "name": "Vincent Arlet",
            "title": "Professor of Orthopaedic Surgery",
            "location": "Philadelphia, PA",
        },
    ],
    "url": "https://www.linkedin.com/in/richard-branson-8a38866",
}
```
👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/profiles_by_name.json) 보기

#### Code Example
프로필을 찾기 위해 이름과 성 필드를 수정하십시오.
```python
people = [
    {"first_name": "Richard", "last_name": "Branson"},
    {"first_name": "Bill", "last_name": "Gates"},
]
```
👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_profile_by_name.py) 보기

### 4. Posts by URL
특정 LinkedIn 게시물에 대한 상세 정보를 수집합니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin-posts-by-url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin-posts-by-url.png" />

#### Input Parameters
| Parameter | Type   | Required | Description              |
|-----------|--------|----------|--------------------------|
| `url`     | string | Yes      | LinkedIn 게시물 URL        |

#### Sample Response
```json
{
    "post_info": {
        "id": "7176601589682434049",
        "url": "https://www.linkedin.com/posts/karin-dodis_web-data-collection-for-businesses-bright-activity-7176601589682434049-Aakz",
        "date_posted": "2024-03-21T15:32:33.770Z",
        "post_type": "post",
        "engagement": {"num_likes": 12, "num_comments": 4},
    },
    "content": {
        "title": "Karin Dodis on LinkedIn: Web data collection for Businesses. Bright Data",
        "text": "Hey data enthusiasts, Bright Data has an awesome collection of free datasets waiting for you to dive into. Whether you're a seasoned analyst or just starting out, these datasets are a goldmine of potential for your projects. From Wikipedia to ESPN and beyond, there's something here for everyone. Use them to fuel your next big idea, hone your skills, and add some serious value to your resume",
    },
    "author": {
        "user_id": "karin-dodis",
        "profile_url": "https://il.linkedin.com/in/karin-dodis",
        "followers": 4131,
        "total_posts": 28,
    },
    "repost_info": {
        "original_author": "Or Lenchner",
        "original_author_id": "orlenchner",
        "original_text": "Free Datasets! Not just samples, but complete datasets with millions of records. Before investing in acquiring specific large-scale data to train your LLM, start with free datasets. Wikipedia dataset, ESPN dataset, Goodreads, IMDB, and more.. Check it out -->",
        "original_date": "2024-03-27T15:39:54.497Z",
        "original_post_id": "7176470998987214848",
    },
}
```

👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/linkedin_posts_url.json) 보기

#### Code Example
분석하려는 LinkedIn 게시물 링크로 URL을 교체하십시오.

```python
posts = [
    {
        "url": "https://www.linkedin.com/pulse/ab-test-optimisation-earlier-decisions-new-readout-de-b%C3%A9naz%C3%A9?trk=public_profile_article_view"
    },
    {
        "url": "https://www.linkedin.com/posts/orlenchner_scrapecon-activity-7180537307521769472-oSYN?trk=public_profile"
    },
    {
        "url": "https://www.linkedin.com/posts/karin-dodis_web-data-collection-for-businesses-bright-activity-7176601589682434049-Aakz?trk=public_profile"
    },
    {
        "url": "https://www.linkedin.com/pulse/getting-value-out-sunburst-guillaume-de-b%C3%A9naz%C3%A9?trk=public_profile_article_view"
    },
]
```
👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_posts_by_url.py) 보기

### 5. Posts Discovery by URL
사용자가 작성했거나 상호작용한 LinkedIn 아티클에 대한 상세 데이터를 찾습니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin-posts-discover-by-url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin-posts-discover-by-url.png" />

#### Input Parameters
| Parameter | Type   | Required | Description                     |
|-----------|--------|----------|---------------------------------|
| `url`     | string | Yes      | LinkedIn 작성자/아티클 URL |
| `limit`   | number | No       | 가져올 아티클의 최대 개수 |

#### Sample Response
```json
{
    "article_info": {
        "id": "fare-business-con-la-propria-identità-cristian-brunori",
        "url": "https://it.linkedin.com/pulse/fare-business-con-la-propria-identità-cristian-brunori",
        "title": "Fare Business con la propria Identità",
        "date_posted": "2017-03-01T17:27:26.000Z",
        "post_type": "article",
        "engagement": {"num_likes": 18, "num_comments": 0},
    },
    "author": {
        "user_id": "cristianbrunori",
        "profile_url": "https://it.linkedin.com/in/cristianbrunori",
        "followers": 5205,
    },
    "content": {
        "headline": "Quali sono i fattori che permettono ad un prodotto, ad un servizio e ad un'azienda di distinguersi nei nuovi scenari di mercato dove quasi tutto è tecnicamente e facilmente riproducibile? Mai come in questo momento storico, l'identità di Marca è un valore imprescindibile per tutelare il proprio lavo",
        "text": "Quali sono i fattori che permettono ad un prodotto, ad un servizio e ad un'azienda di distinguersi nei nuovi scenari di mercato dove quasi tutto è tecnicamente e facilmente riproducibile? Mai come in questo momento storico, l' identità di Marca è un valore imprescindibile per tutelare il proprio lavoro e per aprire nuovi scenari economici ideali per la propria attività...",
    },
    "related_articles": [
        {
            "headline": "La differenza tra Marketing e Branding",
            "date_posted": "2017-06-29T00:00:00.000Z",
        },
        {
            "headline": "Ecco perché un contenuto diventa virale",
            "date_posted": "2017-03-24T00:00:00.000Z",
        },
    ],
}
```
👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/discovered_posts_by_url.json) 보기

#### Code Example
특정 LinkedIn 프로필에서 아티클을 가져오려면 `url` 및 `limit` 필드를 업데이트하십시오.
```python
authors = [
    {
        "url": "https://www.linkedin.com/today/author/cristianbrunori?trk=public_post_follow-articles",
        "limit": 50,
    },
    {
        "url": "https://www.linkedin.com/today/author/stevenouri?trk=public_post_follow-articles"
    },
]
```
👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_posts_discover_by_url.py) 보기


### 6. Posts Discovery by Profile
특정 LinkedIn 프로필이 작성했거나 상호작용한 모든 게시물을 탐색합니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin_posts_by_profile_url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin_posts_by_profile_url.png" />

#### Input Parameters
| Parameter    | Type   | Required | Description                                                             |
|--------------|--------|----------|-------------------------------------------------------------------------|
| `url`        | string | Yes      | LinkedIn 프로필 URL                                                   |
| `start_date` | date   | No       | 게시물을 필터링할 시작 날짜(ISO 8601 형식) |
| `end_date`   | date   | No       | 게시물을 필터링할 종료 날짜(ISO 8601 형식) |

#### Sample Response
```json
{
    "article_info": {
        "id": "fare-business-con-la-propria-identità-cristian-brunori",
        "url": "https://it.linkedin.com/pulse/fare-business-con-la-propria-identità-cristian-brunori",
        "title": "Fare Business con la propria Identità",
        "date_posted": "2017-03-01T17:27:26.000Z",
        "post_type": "article",
        "engagement": {"num_likes": 18, "num_comments": 0},
    },
    "author": {
        "user_id": "cristianbrunori",
        "profile_url": "https://it.linkedin.com/in/cristianbrunori",
        "followers": 5205,
    },
    "content": {
        "headline": "Quali sono i fattori che permettono ad un prodotto, ad un servizio e ad un'azienda di distinguersi nei nuovi scenari di mercato dove quasi tutto è tecnicamente e facilmente riproducibile? Mai come in questo momento storico, l'identità di Marca è un valore imprescindibile per tutelare il proprio lavo",
        "text": "Quali sono i fattori che permettono ad un prodotto, ad un servizio e ad un'azienda di distinguersi nei nuovi scenari di mercato dove quasi tutto è tecnicamente e facilmente riproducibile? Mai come in questo momento storico, l' identità di Marca è un valore imprescindibile per tutelare il proprio lavoro e per aprire nuovi scenari economici ideali per la propria attività...",
    },
    "related_articles": [
        {
            "headline": "La differenza tra Marketing e Branding",
            "date_posted": "2017-06-29T00:00:00.000Z",
        },
        {
            "headline": "Ecco perché un contenuto diventa virale",
            "date_posted": "2017-03-24T00:00:00.000Z",
        },
    ],
}
```
👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/posts_by_profile.json) 보기

#### Code Example
특정 LinkedIn 프로필에서 게시물을 수집하려면 프로필 URL과 날짜 범위를 수정하십시오.
```python
profiles = [
    {
        "url": "https://www.linkedin.com/in/luca-rossi-0aa497bb",
        "start_date": "2024-10-01T00:00:00.000Z",
        "end_date": "2024-10-09T00:00:00.000Z",
    },
    {
        "url": "https://www.linkedin.com/in/srijith-gomattam-401059214",
        "start_date": "2024-09-01T00:00:00.000Z",
        "end_date": "2024-10-01T00:00:00.000Z",
    },
    {
        "url": "https://www.linkedin.com/in/anna-clarke-0a342513",
        "start_date": "2024-10-01T00:00:00.000Z",
    },
]
```
👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_posts_by_profile_url.py) 보기

### 7. Posts Discovery by Company
회사 페이지의 게시물 및 업데이트를 수집합니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin_posts_by_company_url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin_posts_by_company_url.png" />

#### Input Parameters
| Parameter    | Type   | Required | Description                                                             |
|--------------|--------|----------|-------------------------------------------------------------------------|
| `url`        | string | Yes      | LinkedIn 회사 URL                                                   |
| `start_date` | date   | No       | 게시물을 필터링할 시작 날짜(ISO 8601 형식) |
| `end_date`   | date   | No       | 게시물을 필터링할 종료 날짜(ISO 8601 형식) |

#### Sample Response
```json
{
    "post_info": {
        "id": "7254476883906482179",
        "url": "https://it.linkedin.com/posts/lanieri_lanieri-torna-in-lussemburgo-siamo-lieti-activity-7254476883906482179-8dW8",
        "date_posted": "2024-10-22T13:01:10.754Z",
        "post_type": "post",
    },
    "content": {
        "title": "Lanieri on LinkedIn: Lanieri torna in Lussemburgo. Siamo lieti di annunciare che dal 7 al 9…",
        "text": "Lanieri torna in Lussemburgo. Siamo lieti di annunciare che dal 7 al 9 novembre il nostro Trunk Show Su Misura fa tappa in Lussemburgo. Crea il tuo pezzo unico insieme ai nostri Style Advisor: scegli il tessuto, i dettagli e la vestibilità del tuo capo: noi lo realizzeremo per te in sole quattro settimane. Ci vediamo all'Hotel Le Royal, Boulevard Royal 12. Prenota il tuo appuntamento qui https://bit.ly/4hgYgyk",
        "images": [
            "https://media.licdn.com/dms/image/v2/D4D22AQHbmc9Vn-NP5Q/feedshare-shrink_2048_1536/feedshare-shrink_2048_1536/0/1729602070140?e=2147483647&v=beta&t=gt-rNjUJR_ZMVDjNfwmtx3mwBpR3UjCdtVjoj2ZsAv0"
        ],
    },
    "engagement": {"likes": 12, "comments": 0},
    "company_info": {
        "name": "Lanieri",
        "followers": 5768,
        "account_type": "Organization",
        "profile_url": "https://it.linkedin.com/company/lanieri",
    },
}
```

👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/linkedin_posts_company_url.json) 보기

#### Code Example
특정 회사 페이지에서 게시물을 가져오려면 회사 URL 및 날짜 범위를 사용자 지정하십시오.
```python
companies = [
    {"url": "https://www.linkedin.com/company/green-philly"},
    {"url": "https://www.linkedin.com/company/lanieri"},
    {"url": "https://www.linkedin.com/company/effortel"},
]
```

👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_posts_by_company_url.py) 보기

### 8. Job Listings Collection by URL
URL을 사용하여 특정 채용 공고에 대한 전체 정보를 추출합니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin_jobs_by_url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin_jobs_by_url.png" />

#### Input Parameters
| Parameter | Type   | Required | Description                  |
|-----------|--------|----------|------------------------------|
| `url`     | string | Yes      | LinkedIn 채용 공고 URL    |

#### Sample Response
```json
{
    "job_info": {
        "id": "4073552631",
        "title": "Data Platform Engineer",
        "location": "Tel Aviv-Yafo, Tel Aviv District, Israel",
        "posted_date": "2024-11-22T09:41:10.107Z",
        "posted_time": "1 month ago",
        "employment_type": "Full-time",
        "function": "Engineering and Information Technology",
        "seniority_level": "Not Applicable",
        "industries": "Computer and Network Security",
        "applicants": 85,
        "apply_link": "https://www.linkedin.com/jobs/view/externalApply/4073552631?url=https%3A%2F%2Fcycode%2Ecom%2Fcareers%2Fposition%2F%3Fpos_title%3Ddata-platform-engineer%26pos_id%3D53%2ED48%26coref%3D1%2E11%2Ep9D_4217&urlHash=c1hm",
    },
    "company": {
        "name": "Cycode | Complete ASPM",
        "id": "40789623",
        "logo": "https://media.licdn.com/dms/image/v2/D4D0BAQFsSsfzqEVWtw/company-logo_100_100/company-logo_100_100/0/1689682315729/cycode_logo?e=2147483647&v=beta&t=h91f6XM-5MGHa5FDhMCVtXy7Me0S8YQIPRAYUc4UVC0",
        "url": "https://www.linkedin.com/company/cycode",
    },
    "description": {
        "summary": "This is a unique opportunity to join an exciting early-stage startup experiencing hypergrowth in a white-hot segment of the cybersecurity space. Cycode is a fast-growing cybersecurity startup and the creator of the first comprehensive software supply chain security solution...",
        "requirements": [
            "Bachelor's degree in a relevant field such as Statistics, Mathematics, Computer Science, or Economics",
            "Proven experience in building, deploying, and monitoring of ETLs",
            "Proficiency in data analysis tools such as SQL, Python, Pandas, Apache Spark / Beam",
            "Good understanding of data modeling principles",
            "Familiarity with data visualization tools",
        ],
        "advantages": ["MongoDB", "AWS Cloud", "CICD, Docker Kubernetes"],
    },
}
```

👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/linkedin_jobs_url.json) 보기

#### Code Example
특정 채용 공고에 대한 정보를 수집하려면 채용 URL을 업데이트하십시오.
```python
job_searches = [
    {"url": "https://www.linkedin.com/jobs/view/4073552631"},
    {"url": "https://www.linkedin.com/jobs/view/4073729630"},
]
```

👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_jobs_by_url.py) 보기


### 9. Job Listings Discovery by Keyword
고급 검색 기준 및 필터를 사용하여 채용 공고를 추출하고 관련 기회를 찾습니다.

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin_jobs_by_keyword" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin_jobs_by_keyword.png" />

#### Input Parameters
| Parameter          | Type    | Required | Description                                                                                      |
|--------------------|---------|----------|--------------------------------------------------------------------------------------------------|
| `location`         | string  | Yes      | 특정 위치에서 채용 공고를 수집합니다                                                             |
| `keyword`          | string  | No       | 키워드 또는 직무명으로 채용을 검색합니다(예: "Product Manager"). 정확히 일치시키려면 따옴표를 사용하십시오. |
| `country`          | string  | No       | 2자리 국가 코드(예: US 또는 FR)                                                   |
| `time_range`       | string  | No       | 채용 공고 게시 시간 범위(예: 지난 24시간, 지난 주)                      |
| `job_type`         | string  | No       | 직무 유형으로 필터링합니다(예: full-time, part-time, contract)                                        |
| `experience_level` | string  | No       | 요구 경력 수준으로 필터링합니다(예: entry, mid, senior)                                  |
| `remote`           | string  | No       | 원격 근무 옵션으로 채용을 필터링합니다                                                              |
| `company`          | string  | No       | 특정 회사의 채용을 검색합니다                                                               |
| `selective_search` | boolean | No       | `true`로 설정하면 지정한 키워드를 포함하지 않는 제목을 제외합니다                  |


#### Sample Response
```json
{
    "job_info": {
        "id": "4096670538",
        "title": "Remote Part-Time Focus Group Participants (Up To $750/Week)",
        "posted_date": "2024-12-15T09:16:55.932Z",
        "posted_time": "1 week ago",
        "location": {"city": "Bronx", "state": "NY", "country": "US"},
        "type": {
            "employment": "Part-time",
            "level": "Entry level",
            "function": "Other",
            "industry": "Market Research",
            "remote": true,
        },
        "applicants": 25,
        "apply_link": "https://www.linkedin.com/jobs/view/externalApply/4096670538?url=https%3A%2F%2Fwww%2Ecollegerecruiter%2Ecom%2Fjob%2F1447234465%3Fr%3D1%26source%3D101%26ids%3D513&urlHash=Nagt",
    },
    "company": {
        "name": "Apex Focus Group",
        "id": "89885194",
        "logo": "https://media.licdn.com/dms/image/v2/C560BAQHmbh3iXrrrEA/company-logo_100_100/company-logo_100_100/0/1670524954585?e=2147483647&v=beta&t=n2mnVpQTNpofk7mrixyy7aBax0fXqhY031fijCPtp14",
        "url": "https://www.linkedin.com/company/apex-focus-group",
    },
    "compensation": {
        "per_session": "$75-$150 (1 hour)",
        "multi_session": "$300-$750",
        "frequency": "weekly",
    },
    "requirements": {
        "technical": [
            "Smartphone with working camera or desktop/laptop with webcam",
            "High speed internet connection",
        ],
        "responsibilities": [
            "Show up 10 mins before discussion start time",
            "Complete written and oral instructions",
            "Complete surveys for each panel",
            "Use and discuss provided products/services",
        ],
    },
    "search_parameters": {
        "keyword": "data analyst",
        "location": "New York",
        "job_type": "Part-time",
        "experience": "Entry level",
        "remote": "Remote",
        "country": "US",
    },
}
```

👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/linkedin_jobs_keyword.json) 보기

#### Code Example
다양한 위치와 요구사항에서 특정 채용 기회를 찾도록 이러한 검색 기준을 사용자 지정하십시오.
```python
search_criteria = [
    {
        "location": "New York",
        "keyword": "data analyst",
        "country": "US",
        "time_range": "Any time",
        "job_type": "Part-time",
        "experience_level": "Entry level",
        "remote": "Remote",
        "company": "",
    },
    {
        "location": "paris",
        "keyword": "product manager",
        "country": "FR",
        "time_range": "Past month",
        "job_type": "Full-time",
        "experience_level": "Internship",
        "remote": "On-site",
        "company": "",
    },
    {
        "location": "New York",
        "keyword": '"python developer"',
        "country": "",
        "time_range": "",
        "job_type": "",
        "experience_level": "",
        "remote": "",
        "company": "",
    },
]
```

👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_jobs_by_keyword.py) 보기

### 10. Job Listings Discovery by URL
직접 LinkedIn 검색 URL을 사용하여 채용 공고를 추출합니다

<img width="700" alt="linkedin-scraper-bright-data-screenshot-linkedin_jobs_by_search_url" src="https://github.com/bright-kr/LinkedIn-Scraper/blob/main/LinkedIn%20Images/linkedin-scraper-bright-data-screenshot-linkedin_jobs_by_search_url.png" />

#### Input Parameters
| Parameter          | Type    | Required | Description                                                                                       |
|--------------------|---------|----------|---------------------------------------------------------------------------------------------------|
| `url`              | string  | Yes      | 직접 LinkedIn 검색 URL(예: 회사 검색 또는 키워드 기반 검색)                        |
| `selective_search` | boolean | No       | `true`로 설정하면 지정한 키워드를 포함하지 않는 제목을 제외합니다                 |

> **Note:** 시간 범위 필터를 구현하려면 원하는 범위를 초 단위로 계산(`hours * 3600`)한 후 LinkedIn 검색 URL의 `&f_TPR` 매개변수를 업데이트하십시오.
>
> - 지난 1시간: `f_TPR=r3600` 사용  
> - 지난 24시간: `f_TPR=r86400` 사용  
> - 지난 1주: `f_TPR=r604800` 사용

#### Sample Response
```json
{
    "job_info": {
        "id": "4107998267",
        "title": "Software Engineer, Professional Services",
        "location": "Tel Aviv District, Israel",
        "posted": {"date": "2024-12-22T08:39:21.666Z", "time_ago": "1 hour ago"},
        "type": {
            "employment": "Full-time",
            "level": "Entry level",
            "function": "Information Technology",
            "industry": "Software Development",
        },
        "applicants": 25,
        "apply_link": "https://www.linkedin.com/jobs/view/externalApply/4107998267?url=https%3A%2F%2Fwww%2Efireblocks%2Ecom%2Fcareers%2Fcurrent-openings%2F4426623006%3Fgh_jid%3D4426623006",
    },
    "company": {
        "name": "Fireblocks",
        "id": "14824547",
        "logo": "https://media.licdn.com/dms/image/v2/C4D0BAQEyT6gpuwTpPg/company-logo_100_100/company-logo_100_100/0/1630561416766/fireblocks_logo?e=2147483647&v=beta&t=MNcf2cPIzbPMdPDbsidFZBlEVWQHcHK-QimzqSaimww",
        "url": "https://www.linkedin.com/company/fireblocks",
    },
    "requirements": {
        "core": [
            "2+ years of software development experience",
            "Proficiency in JavaScript, TypeScript, and Python",
            "Strong understanding of frontend and backend technologies",
            "Experience with SQL and NoSQL databases",
            "Familiarity with Docker and Kubernetes",
            "Knowledge of blockchain and crypto development",
            "Understanding of security protocols",
        ],
        "nice_to_have": [
            "Experience with Fireblocks or similar crypto platforms",
            "Knowledge of cloud platforms (AWS, GCP, Azure)",
        ],
    },
    "responsibilities": [
        "Collaborate with clients on technical requirements",
        "Build custom tools and integrations",
        "Work on frontend and backend components",
        "Assist with API integration",
        "Provide technical training",
        "Stay updated on blockchain trends",
    ],
}
```

👉 [Full JSON Response Sample](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_data/linkedin_jobs_search_url.json) 보기

#### Code Example
특정 회사 또는 검색 결과에서 채용 공고를 수집하려면 이러한 검색 URL을 수정하십시오.
```python
search_urls[
    {
        "url": "https://www.linkedin.com/jobs/search?keywords=Software&location=Tel%20Aviv-Yafo&geoId=101570771&trk=public_jobs_jobs-search-bar_search-submit&position=1&pageNum=0&f_TPR=r3600"
    },
    {"url": "https://www.linkedin.com/jobs/semrush-jobs?f_C=2821922"},
    {"url": "https://www.linkedin.com/jobs/reddit-inc.-jobs-worldwide?f_C=150573"},
]
```

👉 [Full Python Code](https://github.com/bright-kr/LinkedIn-Scraper/blob/main/linkedin_scraper_api_codes/linkedin_jobs_by_search_url.py) 보기


## Data Collection Approaches
다음 매개변수를 사용하여 결과를 세밀하게 조정할 수 있습니다:
| **Parameter**       | **Type**   | **Description**                                            | **Example**                  |
|---------------------|------------|------------------------------------------------------------|------------------------------|
| `limit`             | `integer`  | 입력당 최대 결과 수                                   | `limit=10`                   |
| `include_errors`    | `boolean`  | 문제 해결을 위한 오류 리포트 가져오기                     | `include_errors=true`        |
| `notify`            | `url`      | 완료 시 알림을 받을 Webhook 알림 URL  | `notify=https://notify-me.com/` |
| `format`            | `enum`     | 출력 형식(예: JSON, NDJSON, JSONL, CSV)         | `format=json`                |

💡 **Pro Tip:** 또한 데이터를 [external storage](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-deliver-to-external-storage)로 전달할지, 또는 [webhook](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview#via-webhook)으로 전달할지 선택할 수도 있습니다.

----

더 자세한 내용이 필요하신가요? [official API docs](https://docs.brightdata.com/scraping-automation/web-data-apis/web-scraper-api/overview)를 확인하십시오.