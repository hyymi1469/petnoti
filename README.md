# petnoti
애견미용샵 매니징 어플
https://petnoti.com

# 사용 기술
* 백엔드 - Go

* 프론트엔드 - ReactNative, Expo, AndroidStudio

* DB - Mysql

* Storage - BlackBlaze B2

* CDN - CloudFlare CDN

* 도메인 구매 - CloudFlare

* OS - Unix Mac

* AI - ClaudeCode, Codex

# Overview
- 고루틴이라는 경량화 스레드가 있고 어느 os든 포팅이 굉장히 간편하다는 점에서 go언어를 선택함.
- 프론트엔드는 웹, 앱이 모두 작동해야 한다고 하여 리액트네이티브로 선택.
- 해당 어플은 미용사들이 강아지들의 사진, 동영상을 저장하고 고객에게 보여줘야 하기 때문에 저장소가 무조건 필요함.
  저장소는 원래 CloudFlare R2를 사용하려 했으나 생각보다 비싼 보관 비용때문에 찾아보다가 BlackBlaze B2라는 보관비용이 싼 곳을 발견.
  하지만 다운로드, 업로드가 유료여서 고민하던 찰나 CloudFlare를 CDN으로 이용하면 
