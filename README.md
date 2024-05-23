# 모바일 청첩장

## 사용법
1. root에 .env 파일 생성
2. .env 파일에 아래 정보를 입력 - 각 정보는 해당 서비스에 직접 가입하여 얻어내야 합니다.
```
#Firebase
VITE_APP_FIREBASE_API_KEY=<Filebase key>
VITE_APP_FIREBASE_AUTH_DOMAIN=<Filebase domain>
VITE_APP_FIREBASE_DATABASE_URL=<Filebase url>
VITE_APP_FIREBASE_PROJECT_ID=<Filebase project id>
VITE_APP_FIREBASE_STORAGE_BUCKET=<Filebase storage bucket>
VITE_APP_FIREBASE_MESSAGING_SENDER_ID=<Filebase sender id>
VITE_APP_FIREBASE_APP_ID=<Filebase app id>
VITE_APP_FIREBASE_MEASUREMENT_ID=<Filebase measurement id>

#Kakao
VITE_APP_KAKAO_JAVASCRIPT_KEY=<Kakao javascript key>
VITE_APP_KAKAO_TEMPLATE_ID=<Kakao template id>

#Naver
VITE_APP_NAVER_CLIENT_ID=<Naver client id>

#TMap
VITE_APP_TMAP_API_KEY=<Tmap api key>

#Google
VITE_APP_GOOGLE_FORM_ADDRESS=<Goole form address>
```
3. ```npm install``` 또는 ```yarn install```
4. ```npm run dev``` 또는 ```yarn dev```


## 구성

- welcome
- 인사말
- 갤러리
- Youtube 생중계
- 달력
- 지도
- 마음전하기
- 참석여부
- 축하메시지
- 공유링크

## 참고링크

- https://github.com/young-do/seohye-s2-youngdo
  - 많은 도움이 되었습니다. 감사합니다.
