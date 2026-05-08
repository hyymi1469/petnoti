## 해당 프로젝트는 상용으로 사용 중인 소프트웨어라 코드를 공개할 수 없습니다.
# petnoti
애견미용샵 매니징 어플
https://petnoti.com

애견미용샵에서 사장이 가게 매니징을 편하게 하기 위한 목적으로 개발된 어플. 고객 예약, 스케줄 관리, 알림장, 히스토리 관리, 알림톡, 매출 관리 등 가게 운영에 필수적인 소프트웨어.

# 개발 인원
* 혼자

# 사용 기술
* 백엔드 - Go

* 프론트엔드 - ReactNative, Expo, AndroidStudio

* DB - Mysql

* Storage - BlackBlaze B2

* CDN - CloudFlare CDN

* 도메인 구매 - CloudFlare

* CloudCompute - Mac mini m4

* AI - ClaudeCode, Codex

# Overview
- 시중에 나와 있는 애견미용샵 어플들은 비싸고 불편한 점이 많아 애견미용샵을 운영 중인 지인에게 직접 피드백을 받으며 상용화 목적으로 개발.

- 개인적으로 익숙한 언어기도 하고 고루틴이라는 경량화 스레드가 있고 어느 os든 포팅이 간편하다는 점에서 go언어를 선택함.
  
- 프론트엔드는 웹, 앱이 모두 작동해야 한다고 하여 ReactNative로 선택.
  
- 해당 어플은 미용사들이 강아지들의 사진, 동영상을 저장하고 고객에게 보여줘야 하기 때문에 저장소가 무조건 필요.
  저장소는 원래 CloudFlare R2를 사용하려 했으나 생각보다 비싼 보관 비용 때문에 찾아보다가 BlackBlaze B2라는 보관비용이 싼 곳을 발견.
  하지만 B2는 트래픽(다운로드, 업로드)가 유료여서 고민하던 찰나 "Backblaze B2 → Cloudflare 구간의 트래픽 비용(egress)”을 면제해주는 제휴가 되어 있다는 걸
  보고 마침 이미지, 동영상을 빠르게 내려줘야 했기 때문에 CDN이 필요했고 CloudeFlare CDN은 무료였기 때문에 데이터 보관비만 내면 됨.
  <img width="808" height="347" alt="스크린샷 2026-05-08 14 21 32" src="https://github.com/user-attachments/assets/d62d1e30-1b43-461c-97c5-c1f2548cfbcb" />


- 웹쪽 작업을 많이 해보면 알지만 백앤드나 프론트엔드, DB를 올릴 장비가 필요한데 AWS, GCP, Azure는 굉장히 비싸다.
<img width="839" height="349" alt="스크린샷 2026-05-08 14 48 40" src="https://github.com/user-attachments/assets/89c69fe0-d37c-4492-93d4-c176a926683b" />
  성능대비 가격이 굉장히 비싼데 소규모 프로젝트에 달마다 이 금액을 낼 수는 없어서 고민을 하다가 그냥 집에 직접 장비를 구해서 서비스 하기로 결심하고 이것저것 찾아보았다.
  
  미니컴퓨터나 자그마한 컴퓨터를 찾는데 반도체 이슈로 인해 성능대비 굉장히 고가가 되어 있었음.
<img width="669" height="306" alt="스크린샷 2026-05-08 14 52 44" src="https://github.com/user-attachments/assets/da5d9e8c-9e80-4ce1-9c29-98d205890f6c" />
  이런 저런 정보를 찾고 주위 사람들과 대화한 결과, 요즘 가성비의 애플, 감성의 삼성이란 말을 듣고 생각해보니 맥미니가 성능대비 굉장히 쌌고 심지어 unix기반이라 사실상 linux와 큰 차이가 없어서 맥미니 m4 구매.

- 일반 가정집에서 라이브서버를 올리는 것이기 때문에 백업은 필수라 외장하드를 Mac에 연결하고 매일 03시마다 DB백업하도록 cron(mac에서는 launchd)을 사용하고 오래된 백업파일은 지우도록 함. 다음과 같은 프로세스 구축.
  
 cron/systemd timer  ->  backup shell script  ->  mysqldump  ->  압축  ->  외장하드로 이동  ->  오래된 백업 삭제

- 
