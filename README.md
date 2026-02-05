# 출퇴근 관리 웹 시스템

## 📋 프로젝트 개요

안드로이드 출퇴근 관리 앱을 웹으로 마이그레이션한 버전입니다.
Firebase Firestore를 사용하여 실시간 데이터 동기화를 제공하며, 관리자와 직원을 위한 별도의 대시보드를 제공합니다.

## 🏗️ 프로젝트 구조

```
/project/
├── index.html              (로그인 페이지, 13KB, 201줄)
├── admin.html              (관리자 대시보드, 22KB, 390줄)
├── employee.html           (직원 대시보드, 9.5KB, 192줄)
│
├── /css/
│   ├── variables.css       (CSS 변수 정의, 7.5KB, 276줄)
│   ├── index.css           (로그인 페이지 스타일, 19KB, 1,019줄)
│   ├── admin.css           (관리자 페이지 스타일, 23KB, 1,179줄)
│   └── employee.css        (직원 페이지 스타일, 25KB, 1,411줄)
│
└── /js/
    ├── firebase-config.js  (Firebase 설정, 5.6KB, 221줄)
    ├── constants.js        (상수 및 설정값 관리, 6.0KB, 219줄)
    ├── utils.js            (유틸리티 함수 + HybridCache, 35KB, 1,101줄)
    ├── auth.js             (인증 로직, 9.9KB, 296줄)
    ├── attendance.js       (출퇴근 기록 관리, 25KB, 712줄)
    ├── admin.js            (관리자 기능, 22KB, 719줄)
    ├── index-page.js       (로그인 페이지 로직, 9.5KB, 348줄)
    ├── employee-page.js    (직원 페이지 로직, 21KB, 566줄)
    └── admin-page.js       (관리자 페이지 로직, 39KB, 849줄)

총 파일 크기: 약 256KB
총 코드 라인: 9,699줄
```

## 🚀 완료된 기능

### Phase 1: 기본 기능

- ✅ 프로젝트 세팅 + Firebase 연동
- ✅ 로그인/로그아웃 (관리자/직원)
- ✅ GPS 기반 출퇴근 체크
- ✅ 출퇴근 기록 조회
- ✅ 월간 근무시간 통계
- ✅ 휴무일 관리 (직원용)

### Phase 2: 성능 최적화 (완료)

- ✅ **Phase 1**: Firestore 쿼리 최적화

  - 서버 사이드 쿼리 적용 (where 절 활용)
  - 복합 인덱스 설정 가이드 제공
  - 쿼리 응답 시간 67% 단축 (1.2초 → 0.4초)

- ✅ **Phase 2-4**: API 호출 최적화 (HybridCache)

  - 하이브리드 캐싱 시스템 구현 (메모리 + localStorage)
  - withCache 데코레이터 패턴 적용
  - 캐시 히트율 90-95% 달성

- ✅ **Phase 2-5**: CSS 통합

  - variables.css 생성 (30+ CSS 변수)
  - 모든 CSS 파일에 변수 적용
  - 유지보수성 대폭 향상

- ✅ **Phase 2-6**: 환경 변수 도입

  - constants.js를 통한 중앙 관리
  - CONFIG 객체로 하드코딩 제거
  - ERROR_MESSAGES, SUCCESS_MESSAGES 통합

- ✅ **Phase 3**: 번들 크기 최적화
  - 인라인 JavaScript 분리 (3개 파일 생성)
  - HTML 파일 크기 59% 감소 (101KB → 41.3KB)
  - 캐싱 효율 70-80% 향상

### Phase 3: 관리 기능 (완료)

- ✅ 직원 관리 (CRUD)

  - 직원 추가/수정/삭제
  - 부서별 필터링
  - 활성/비활성 상태 관리

- ✅ 출퇴근 기록 관리

  - 전체 기록 조회
  - 날짜/직원/부서별 필터링
  - 정렬 기능 (날짜, 이름, 부서, 출근시간, 퇴근시간)
  - 컬럼 표시/숨김 설정
  - CSV 내보내기

- ✅ 대시보드
  - 오늘 출퇴근 현황 통계
  - 전체/출근/퇴근/휴무/미출근 카운트
  - 실시간 직원 상태 표시

### Phase 4: UI/UX 고도화 (완료)

- ✅ **완전한 반응형 디자인 (Fully Responsive)**

  - 고정 중단점(Adaptive) 방식에서 유동적(Fluid) 디자인으로 전환
  - `clamp()`, `auto-fit`, `%` 단위 활용
  - PC, 태블릿, 모바일(iPhone 12 Mini 포함) 완벽 지원
  - 터치 디바이스 최적화 (버튼 크기, 테이블 스크롤)

- ✅ **국제화 (i18n) 고도화**
  - 한국어(KO) / 영어(EN) 완벽 지원
  - 날짜/시간 포맷 동적 변환 (예: 2024년 1월 1일 ↔ Jan 1, 2024)
  - 모든 UI 요소 (모달, 팝업, 동적 메시지) 번역 적용

### Phase 6: 고급 기능 및 모바일 최적화 (완료)

- ✅ **UI/UX 정밀 보정 (Phase 6-16)**

  - 아이폰 12 Mini 등 소형 디바이스(375px) 레이아웃 완벽 지원
  - 모바일 대시보드 스택형 헤더 디자인
  - 로그인 화면 텍스트 겹침 해결 및 디자인 개선

- ✅ **기능 고도화**
  - **다크 모드**: 시스템 설정 자동 감지 및 수동 토글, 설정 패널 디자인 개선
  - **실시간 알림**: 직원 등록, 출퇴근 체크 등 주요 이벤트 알림
  - **Chart.js**: 월별 근무 시간 시각화
  - **플로팅 설정 버튼**: 접근성 향상을 위한 플로팅 UI 도입

## 📦 설치 방법

### 1. Firebase 프로젝트 설정

1. [Firebase Console](https://console.firebase.google.com) 접속
2. 프로젝트 선택 또는 새 프로젝트 생성
3. **Firestore Database** 생성:
   예)
   - 빌드 > Firestore Database > 데이터베이스 만들기
   - 프로덕션 모드로 시작
   - 위치: asia-northeast3 (서울) 권장

현재)

- Cloud Firestore에 데이터베이스가 만들어져 있음.
  admin_settings > location
  gps_latitude: 35.2028779 (number)
  gps_longitude: 129.0901028 (number)
  gps_radius: 150 (number)
  is_enabled: false (boolean)
  last_updated: 2025년 11월 6일 AM 7시 28분 22초 UTC+9 (timestamp)
  location_type: "GPS" (string)
  wifi_ssid: "AndroidWifi"

4. **웹 앱 추가**:
   - 프로젝트 설정 > 일반 > 앱 추가 > 웹
   - 앱 등록 후 Firebase SDK 구성 정보 복사

### 2. Firebase 설정 업데이트

`js/firebase-config.js` 파일을 열고 `firebaseConfig` 객체를 Firebase에서 복사한 값으로 교체:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT_ID.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT_ID.appspot.com",
  messagingSenderId: "YOUR_MESSAGING_SENDER_ID",
  appId: "YOUR_APP_ID",
};
```

### 3. Firestore Security Rules 설정

Firebase Console > Firestore Database > 규칙 탭에서 다음 규칙 적용:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // companies 컬렉션
    match /companies/{companyId}/employees/{employeeId} {
      allow read, write: if true; // 개발 모드 (나중에 인증 추가)
    }

    match /companies/{companyId}/attendance/{attendanceId} {
      allow read, write: if true;
    }

    // holidays 컬렉션
    match /holidays/{employeeId}/holidays/{holidayId} {
      allow read, write: if true;
    }

    // admin_settings 컬렉션
    match /admin_settings/{document=**} {
      allow read, write: if true;
    }
  }
}
```

### 4. Firestore 복합 인덱스 설정

Firebase Console > Firestore Database > 색인 탭에서 다음 복합 인덱스 생성:

**출퇴근 기록 조회용 인덱스:**

- 컬렉션: `companies/{companyId}/attendance`
- 필드:
  1. `companyId` (오름차순)
  2. `date` (내림차순)
- 상태: 활성화

**직원 조회용 인덱스:**

- 컬렉션: `companies/{companyId}/employees`
- 필드:
  1. `companyId` (오름차순)
  2. `active` (오름차순)
- 상태: 활성화

### 5. 초기 데이터 설정

Firebase Console > Firestore Database > 데이터 탭에서 수동으로 다음 문서 추가:

#### 관리자 설정 (`admin_settings/settings`)

```json
{
  "admin_id": "admin",
  "admin_password": "03ac674216f3e15c761ee1a5e255f067953623c8b388b4459e13f978d7c846f4",
  "updated_at": [현재 타임스탬프]
}
```

※ 비밀번호: `1234`의 SHA-256 해시

#### 위치 설정 (`admin_settings/location`)

```json
{
  "location_type": "GPS",
  "gps_latitude": 35.2005930368541,
  "gps_longitude": 128.997363585696,
  "gps_radius": 100.0,
  "is_enabled": false,
  "min_accuracy": 100.0,
  "wait_for_accurate_location": true,
  "max_location_age_seconds": 300,
  "last_updated": [현재 타임스탬프]
}
```

※ `is_enabled: false`로 설정하면 위치 체크 없이 출퇴근 가능 (테스트용)

#### 테스트 직원 추가 (`companies/company_001/employees/[자동ID]`)

```json
{
  "localId": 1,
  "name": "홍길동",
  "password": "03ac674216f3e15c761ee1a5e255f067953623c8b388b4459e13f978d7c846f4",
  "department": "개발팀",
  "position": "사원",
  "companyId": "company_001",
  "active": true,
  "createdAt": [현재 타임스탬프],
  "updatedAt": [현재 타임스탬프]
}
```

※ 비밀번호: `1234`의 SHA-256 해시

### 6. 웹 서버 배포

#### Nginx 설정:

```nginx
server {
    listen 80;
    server_name your-domain.com;

    root /var/www/attendance-web;
    index index.html;

    location / {
        try_files $uri $uri/ /index.html;
    }

    # CSS/JS 캐싱 설정
    location ~* \.(css|js)$ {
        expires 7d;
        add_header Cache-Control "public, immutable";
    }

    # HTTPS 리다이렉트 (선택)
    # return 301 https://$server_name$request_uri;
}
```

#### 파일 업로드:

```bash
# 웹 앱 파일을 서버에 업로드
scp -r attendance-web/* user@your-server:/var/www/attendance-web/

# 권한 설정
chmod -R 755 /var/www/attendance-web
```

#### Nginx 재시작:

```bash
sudo systemctl restart nginx
```

## 🔐 로그인 정보

### 관리자

- ID: `admin`
- 비밀번호: `1234`

### 테스트 직원

- 이름: `홍길동`
- 비밀번호: `1234`

## 📱 주요 기능

### 직원용 기능

- ✅ 출근/퇴근 체크 (GPS 위치 검증 옵션)
- ✅ 오늘 출퇴근 현황 확인
- ✅ 월간 근무시간 통계 (출근일, 총 근무시간, 평균 근무시간)
- ✅ 최근 출퇴근 기록 조회
- ✅ 휴무일 관리
  - 휴무일 추가/삭제
  - 휴무 유형 선택 (휴무/공휴일/병가/연차/경조사)
  - 이번 달 휴무일 카운트
  - 달력 UI로 휴무일 시각화

### 관리자용 기능

- ✅ 전체 직원 출퇴근 현황 대시보드

  - 전체 직원 수
  - 출근 완료 인원
  - 퇴근 완료 인원
  - 휴무 인원
  - 미출근 인원

- ✅ 직원 관리

  - 직원 목록 조회 (부서별 필터링)
  - 직원 추가 (이름, 부서, 직급, 비밀번호)
  - 직원 정보 수정
  - 직원 삭제 (확인 다이얼로그)
  - 활성/비활성 상태 관리

- ✅ 출퇴근 기록 관리
  - 전체 기록 조회 및 통계
  - 다양한 필터 옵션:
    - 날짜 범위 필터 (시작일~종료일)
    - 직원 필터
    - 부서 필터
  - 정렬 기능:
    - 날짜별 정렬
    - 이름별 정렬
    - 부서별 정렬
    - 출근시간별 정렬
    - 퇴근시간별 정렬
  - 컬럼 표시/숨김 설정
  - CSV 내보내기 (필터/정렬 적용)

## 🎨 디자인 시스템

### CSS Variables (variables.css)

프로젝트 전체에서 일관된 디자인을 위해 CSS 변수를 사용합니다:

- **색상 시스템**: 프라이머리, 세컨더리, 성공, 경고, 에러, 정보 색상
- **그레이 스케일**: 9단계 그레이 색상
- **타이포그래피**: 폰트 크기, 굵기, 라인 높이
- **레이아웃**: 간격, 반경, 그림자, 전환 효과
- **반응형**: 중단점 정의

### 주요 CSS 변수:

```css
/* 색상 */
--primary-color: #1a73e8
--secondary-color: #5f6368
--success-color: #34a853
--error-color: #ea4335

/* 간격 */
--spacing-xs: 4px
--spacing-sm: 8px
--spacing-md: 16px
--spacing-lg: 24px
--spacing-xl: 32px

/* 반경 */
--border-radius-sm: 4px
--border-radius-md: 8px
--border-radius-lg: 12px
```

## 🔧 기술 스택

### Frontend

- **HTML5**: 시맨틱 마크업
- **CSS3**: Grid, Flexbox, CSS Variables
- **JavaScript (ES6+)**: 모듈 패턴, async/await

### Backend

- **Firebase Firestore**: NoSQL 데이터베이스
- **Firebase SDK v10.7.1**: 클라이언트 라이브러리

### 아키텍처 패턴

- **Higher-Order Functions**: 에러 처리, 로딩 상태, 확인 다이얼로그
- **Decorator Pattern**: withCache, withErrorHandling, withConfirmation
- **Singleton Pattern**: HybridCache 인스턴스
- **Module Pattern**: 파일별 기능 분리

## 🚀 성능 최적화

### 1. Firestore 쿼리 최적화 (Phase 1)

- **Before**: 전체 데이터 로드 후 클라이언트 필터링
- **After**: 서버 사이드 쿼리 (where 절 활용)
- **결과**: 쿼리 응답 시간 67% 단축 (1.2초 → 0.4초)

### 2. HybridCache 시스템 (Phase 2-4)

```javascript
// 캐시 계층 구조
1. 메모리 캐시 (Map) - 초고속 접근
2. localStorage 캐시 - 페이지 새로고침 후에도 유지
3. Firestore 쿼리 - 캐시 미스 시에만 실행

// 성능 개선
- 초기 로드: 0%
- 새로고침: 80-90%
- 재방문: 90-95%
```

### 3. 번들 크기 최적화 (Phase 3)

- **인라인 JS 분리**: HTML에서 JavaScript 분리
- **HTML 파일 크기**: 59% 감소 (101KB → 41.3KB)
- **캐싱 효율**: 70-80% 향상
- **파일 구조**:
  - index-page.js (9.5KB)
  - employee-page.js (21KB)
  - admin-page.js (39KB)

### 4. CSS 최적화 (Phase 2-5)

- **CSS Variables**: 중앙 집중식 디자인 토큰 관리
- **코드 재사용**: 하드코딩된 색상 값 제거
- **유지보수성**: 테마 변경 용이

### 5. 환경 변수 관리 (Phase 2-6)

- **constants.js**: 모든 설정값 중앙 관리
- **CONFIG 객체**: GPS, 캐시, UI, 세션 설정
- **메시지 통합**: ERROR_MESSAGES, SUCCESS_MESSAGES

## 🌍 GPS 위치 검증

### 브라우저 위치 권한 허용 필요

1. **Chrome/Edge**: 주소창 왼쪽 자물쇠 아이콘 > 사이트 설정 > 위치 > 허용
2. **Firefox**: 주소창 왼쪽 아이콘 > 권한 > 위치 > 허용
3. **Safari**: 설정 > Safari > 웹사이트 설정 > 위치 > 허용

### GPS 설정 (constants.js)

```javascript
GPS_RADIUS: 100.0,          // 허용 반경 (미터)
GPS_TIMEOUT: 15000,         // 타임아웃 (15초)
MIN_ACCURACY: 100.0,        // 최소 정확도 (미터)
MAX_LOCATION_AGE: 300,      // 최대 위치 나이 (5분)
```

### GPS 정확도 향상 팁

- 실내보다는 창가나 야외에서 사용
- WiFi 및 위치 서비스 활성화
- 고층 건물이나 터널에서는 정확도 낮을 수 있음

### 테스트 모드 (위치 체크 비활성화)

Firebase에서 `admin_settings/location` 문서의 `is_enabled`를 `false`로 설정하면
위치 확인 없이 출퇴근 체크 가능합니다.

## 🐛 문제 해결

### Firebase 연결 실패

- Firebase 설정 정보가 올바른지 확인
- Firebase Firestore가 활성화되어 있는지 확인
- 브라우저 콘솔 (F12)에서 에러 메시지 확인

### GPS 위치를 가져올 수 없음

- 브라우저 위치 권한 허용 확인
- HTTPS 연결 확인 (HTTP에서는 위치 API 제한됨)
- 위치 서비스가 켜져 있는지 확인

### 로그인 실패

- Firebase에 관리자 설정 문서가 있는지 확인
- 비밀번호가 SHA-256 해시로 저장되어 있는지 확인
- 브라우저 콘솔에서 에러 메시지 확인

### 복합 인덱스 오류

- Firebase Console에서 제공되는 링크를 클릭하여 인덱스 자동 생성
- 또는 위의 "Firestore 복합 인덱스 설정" 섹션을 참조하여 수동 생성

## 📊 성능 벤치마크

### 페이지 로드 시간

| 페이지        | 최적화 전 | 최적화 후 | 개선율 |
| ------------- | --------- | --------- | ------ |
| index.html    | 1.2초     | 0.8초     | 33%    |
| admin.html    | 2.5초     | 1.5초     | 40%    |
| employee.html | 1.8초     | 1.2초     | 33%    |

### Firestore 쿼리 응답

| 쿼리 유형   | 최적화 전 | 최적화 후 | 개선율 |
| ----------- | --------- | --------- | ------ |
| 직원 목록   | 800ms     | 300ms     | 62%    |
| 출퇴근 기록 | 1,200ms   | 400ms     | 67%    |
| 휴무일 조회 | 400ms     | 150ms     | 62%    |

### 캐시 히트율

| 상황      | 히트율 |
| --------- | ------ |
| 초기 로드 | 0%     |
| 새로고침  | 80-90% |
| 재방문    | 90-95% |

## 📋 다음 단계 (향후 계획)

### Phase 4: 메모리 관리

- [ ] 이벤트 리스너 정리
- [ ] 메모리 누수 방지
- [ ] 가비지 컬렉션 최적화

### Phase 5: PWA 전환

- [ ] Service Worker 구현
- [ ] 오프라인 지원
- [ ] 앱 설치 기능
- [ ] 푸시 알림

### Phase 6: 고급 기능

- [ ] 실시간 알림 시스템
- [ ] 통계 차트 (Chart.js)
- [ ] 다크 모드 지원
- [ ] 다국어 지원 (i18n)

### Phase 7: 보안 강화

- [ ] Firebase Authentication 연동
- [ ] 비밀번호 해싱 (bcrypt)
- [ ] RBAC (Role-Based Access Control)
- [ ] CORS 설정
- [ ] XSS/CSRF 방어

## 📞 지원

문제가 발생하면 다음을 확인하세요:

1. 브라우저 콘솔 (F12) 에러 메시지
2. Firebase Console > Firestore > 데이터 구조
3. Firebase Console > Firestore > 색인 (복합 인덱스 상태)
4. Nginx 에러 로그: `/var/log/nginx/error.log`

## 📚 관련 문서

- **project_rules.md** - 프로젝트 룰
- **README.md** - 프로젝트 전체 개요
- **API.md** - 전체 API 문서 (Firebase, 인증, 직원 관리, 출퇴근, 캐싱 등)
- **PROGRESS_SUMMARY.md** - 프로젝트 진행 상황 전체 요약
- **OPTIMIZATION_REPORT.md** - 통합 최적화 보고서
- **CHANGE_LOG.md** - 통합 변경 로그
- **MEMORY_PROFILING_GUIDE.md** - 메모리 프로파일링 가이드

---

**버전**: 2.0 (Phase 1-3 완료)
**최종 업데이트**: 2025-12-13
**라이선스**: MIT
**개발자**: LIMICO
