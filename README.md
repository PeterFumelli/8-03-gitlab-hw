# Домашнее задание к занятию "8-03. GitLab" - Петр Фумелли

### Задание 1

Runner config ![alt text](https://github.com/PeterFumelli/8-03-gitlab-hw/blob/main/img/runner_conf.png)


### Задание 2

Jobs ststus ![alt text](https://github.com/PeterFumelli/8-03-gitlab-hw/blob/main/img/jobs.png)

```yaml

stages:
  - test
  - build

test_1:
  stage: test
  image: golang:1.17
  script:
   - go test .
  tags:
     - yandex

build_2:
  stage: build
  image: docker:latest
  script:
   - docker build .
  tags:
     - cloud

```

### Задание 3

```yaml

stages:
  - test
  - build

test_1:
  stage: test
  image: golang:1.17
  script:
    - go test .
  rules:
    - changes:
        - '**/*.go'
  tags:
    - yandex

build_2:
  stage: build
  image: docker:latest
  script:
    - docker build .
  needs: []
  tags:
    - cloud
  ```
