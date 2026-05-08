## 해당 프로젝트는 상용으로 사용 중인 소프트웨어라 코드를 공개할 수 없습니다.
# petnoti
애견미용샵 매니징 어플
https://petnoti.com

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
- 개인적으로 인숙한 언어기도 하고 고루틴이라는 경량화 스레드가 있고 어느 os든 포팅이 간편하다는 점에서 go언어를 선택함.
  
- 프론트엔드는 웹, 앱이 모두 작동해야 한다고 하여 리액트네이티브로 선택.
  
- 해당 어플은 미용사들이 강아지들의 사진, 동영상을 저장하고 고객에게 보여줘야 하기 때문에 저장소가 무조건 필요.
  저장소는 원래 CloudFlare R2를 사용하려 했으나 생각보다 비싼 보관 비용 때문에 찾아보다가 BlackBlaze B2라는 보관비용이 싼 곳을 발견.
  하지만 B2는 트래픽(다운로드, 업로드)가 유료여서 고민하던 찰나 "Backblaze B2 → Cloudflare 구간의 트래픽 비용(egress)”을 면제해주는 제휴가 되어 있다는 걸
  보고 마침 이미지, 동영상을 빠르게 내려줘야 했기 때문에 CDN이 필요했고 CloudeFlare CDN은 무료였기 때문에 데이터 보관비만 내면 됨.
  <img width="808" height="347" alt="스크린샷 2026-05-08 14 21 32" src="https://github.com/user-attachments/assets/d62d1e30-1b43-461c-97c5-c1f2548cfbcb" />


- 웹쪽 작업을 많이 해보면 알지만 백앤드나 프론트엔드, DB 를 올릴 장비가 필요한데 AWS, GCP, Azure는 굉장히 비싸다.
<img width="839" height="349" alt="스크린샷 2026-05-08 14 48 40" src="https://github.com/user-attachments/assets/89c69fe0-d37c-4492-93d4-c176a926683b" />
  성능대비 가격이 굉장히 비싼데 소규모 프로젝트에 달마다 이 금액을 낼 수는 없어서 고민을 하다가 그냥 집에 직접 장비를 구해서 서비스 하기로 결심하고 이것저것 찾아봄.
  미니컴퓨터나 자그마한 컴퓨터를 찾는데 반도체 이슈로 인해 성능대비 굉장히 고가가 되어 있었음.
