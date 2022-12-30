---
layout: post
title: Terraform을 사용한 인프라 관리
description: >
  #IaC #Infrastructure as Code #Terraform
categories: [study]
tags: [bigdata]
sitemap: false
hide_last_modified: true
comments: true
---

## Terraform이란?
IaC(Infrastructure as Code)로서 코드로 인프라를 관리하는 것

## Terraform 작동 원리
**Terraform init**
- 지정한 backend에 상태 저장을 위한 .tfstate 파일을 생성 (여기에는 가장 마지막에 적용한 테라폼 내역이 저장됨)
- init 작업을 완료하면, local에는 .tfstate에 정의된 내용을 담은 .terraform 파일이 생성
- 기존에 다른 개발자가 이미 .tfstate에 인프라를 정의해 놓은 것이 있다면, 다른 개발자는 init 작업을 통해서 local에 sync를 맞출수 있음

**Terraform plan**
- 정의한 코드가 어떤 인프라를 만들게 되는지 미리 예측 결과를 보여줌 (plan을 한 내용에서 에러가 없더라도 실제 apply 했을 때는 에러가 발생할 수 있음)
- plan 명령어는 어떠한 현상에도 변화를 주지 않음

**Terraform apply**
- 실제로 배포하기 위한 명령어
- apply를 완료하게되면, 실제 cloud 상에 인프라가 생성되고 작업 결과가 backend의 .tfstate 파일에 저장
- 해당 결과는 local의 .terraform 파일에도 저장

**Terraform import**
- 클라우드 인프라에 배포된 리소스를 terraform state로 옮겨주는 작업
- 상태(state)만 가져올 수 있으며, 설정(configuration)은 만들어 주지 않는다.
- local의 .terraform에 해당 리소스의 상태 정보를 저장해주는 역할을 함 (절대 코드를 생성해주지 않음)        
- 한 번에 하나의 리소스만 가져올 수 있으며, 많은 리소스로 구성된 인프라를 가져오지는 못함. 하지만, terraformer를 사용하면 기존에 구성했던 클라우드 인프라를 한 번의 명령으로 전부 가져올 수 있음

## Terraform의 설정과 상태
- Teraform은 자원을 관리할 때 크게 설정(configuration)과 상태(state)가 존재
- 설정은 .tf 파일, 상태는 .tfstate 파일을 의미

## Terraform Project
> 1. GCP에 이미 만들어진 스냅샷을 사용
> 2. 원하는 갯수만큼 인스턴스 생성
> 3. 내부 IP 범위로 지정
> 4. 방화벽 설정

### 1단계 : GCP에 이미 만들어진 스냅샷 사용
GCP에 이미 만들어진 프로젝트들에 대해서 테라폼으로 가져와야 한다. 이때, Terraform의 import 명령어를 리눅스를 사용하여 실행한다. 

```bash
# 사전작업
  1. tf를 만들 폴더 만들기 
  2. 해당 폴더에 들어간뒤 tf파일을 만든다.
  3. 아래 내용을 추가 한다.
  # .tf file
  provider "google" {
  credentials = "${file("gcp의 json형식의 key파일")}"
  project     = "프로젝트 명"
  }

  resource "google_compute_snapshot" "메소드의 이름"{

  }

  4. terraform init #명령어 실행
```
![import 사용을 위한 tf 파일 작성](./img/import1.png)


```bash
# 명령어 실행
  # 여기서, {project}는 gcp의 프로젝트명
  # {name}은 가져올 snapshot의 이름
  # google_compute_snapshot.snapshot_test은 사용할 메소드와 이름
  terraform import google_compute_snapshot.snapshot_test projects/{project}/global/snapshots/{name}
```
  ![import 적용](