# Aptamil Staff Perks - 접수 시스템

## 비밀번호 관리 방법

### 1. GitHub Secrets 사용 (권장)

#### 설정 방법:

1. GitHub 저장소로 이동: https://github.com/Agency8Group/Aptamil-Staff-Perks
2. **Settings** 탭 클릭
3. 왼쪽 사이드바에서 **Secrets and variables** → **Actions** 클릭
4. **New repository secret** 버튼 클릭
5. 다음 시크릿들을 추가:

```
Name: AGENCY8_PASSWORD
Value: aptamil2024

Name: TEST_COMPANY_PASSWORD
Value: test123456

Name: MARKETING_CORP_PASSWORD
Value: marketing2024
```

#### 현재 등록된 계정:

-   **회사명**: Agency8Group
-   **비밀번호**: aptamil2024

-   **회사명**: TestCompany
-   **비밀번호**: test123456

-   **회사명**: MarketingCorp
-   **비밀번호**: marketing2024

### 2. 새로운 회사 추가 방법

1. GitHub Secrets에 새 비밀번호 추가:

    ```
    Name: [회사명]_PASSWORD
    Value: [비밀번호]
    ```

2. `auth.js` 파일에서 `BROWSER_CREDENTIALS` 객체에 추가:
    ```javascript
    const BROWSER_CREDENTIALS = {
        Agency8Group: "aptamil2024",
        TestCompany: "test123456",
        MarketingCorp: "marketing2024",
        새회사명: "새비밀번호",
    };
    ```

### 3. 보안 고려사항

⚠️ **주의**: 현재 구현은 클라이언트 사이드에서만 동작하므로 완전한 보안을 제공하지 않습니다.

#### 더 안전한 방법들:

1. **서버 사이드 인증**: Node.js 서버 구축
2. **Firebase Authentication**: Google Firebase 사용
3. **Netlify Functions**: 서버리스 함수 사용
4. **Vercel Functions**: Vercel 서버리스 함수 사용

### 4. 현재 사용 가능한 계정

| 회사명        | 비밀번호      | 상태    |
| ------------- | ------------- | ------- |
| Agency8Group  | aptamil2024   | ✅ 활성 |
| TestCompany   | test123456    | ✅ 활성 |
| MarketingCorp | marketing2024 | ✅ 활성 |

### 5. 문제 해결

#### 로그인이 안 될 때:

1. 회사명과 비밀번호가 정확한지 확인
2. 브라우저 개발자 도구(F12)에서 콘솔 확인
3. 세션스토리지 초기화: 브라우저 탭 닫기

#### 새로운 회사 추가 후 문제:

1. GitHub Secrets 설정 확인
2. `auth.js` 파일 수정 확인
3. 브라우저 캐시 삭제 후 재시도
