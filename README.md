# Ikjoo234 Photos

개인 사진 보관 사이트. 기존 ikjoo123 홈페이지와 독립적으로 운영합니다.

## 구성
- Cloudflare Worker: 웹 UI와 로그인/API
- Cloudflare R2 bucket: `ikjoo234-photos`
- 저장 용량: 앱에서 R2 객체 크기 합계 기준 1 GiB 초과 업로드 거부
- 이미지 1장당 최대 25 MiB
- 로그인 세션은 HttpOnly/Secure 쿠키, 12시간 만료
- 업로드는 JPG, PNG, GIF, WebP, AVIF만 허용

## Cloudflare 설정
Worker 이름: `ikjoo234-photos`
R2 binding: `PHOTOS` -> `ikjoo234-photos`
Secret: `PHOTO_PASSWORD` (강력한 비밀번호 설정 필수)

배포 전 `wrangler.toml`의 account_id와 binding을 확인하세요. 공개 배포 전까지 로그인 비밀번호 Secret을 반드시 등록해야 합니다.

참고: 1 GiB 한도는 애플리케이션 수준에서 검사합니다. 매우 동시적인 업로드가 발생하면 동시에 검사한 요청끼리 한도를 잠시 초과할 수 있으므로, 1GB를 절대 넘기지 않아야 하는 경우에는 단일 업로드 동시성 제어/추가 원장 저장소가 필요합니다.
