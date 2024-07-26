

Buil : ok


stages:

  - build

  - test

  - deploy

  

variables:

  MAVEN_CLI_OPTS: "-s .m2/settings.xml --batch-mode --errors --fail-at-end --show-version"

  MAVEN_OPTS: "-Dmaven.repo.local=.m2/repository"

  

# Cache Maven dependencies

cache:

  paths:

    - .m2/repository

  

before_script:

  - 'which ssh-agent || ( apt-get update -y && apt-get install openssh-client -y )'

  - eval $(ssh-agent -s)

  - echo "$SSH_PRIVATE_KEY" | tr -d '\r' | ssh-add -

  

build:

  stage: build

  image: docker:stable-dind

  services:

    - docker:stable-dind

  script:

    - docker info

    - docker build -t qcmapp .

  artifacts:

    paths:

      - target/*.jar

  

test:

  stage: test

  image: maven:3.8.3-openjdk-17

  script:

    - mvn $MAVEN_CLI_OPTS test

  

deploy:

  stage: deploy

  image: alpine:latest

  before_script:

    - apk add --no-cache openssh

  script:

    - scp -o StrictHostKeyChecking=no target/*.jar $SSH_USER@$VM_IPADDRESS:/qcm_app

    - ssh $SSH_USER@$VM_IPADDRESS 'docker-compose down && docker-compose up -d'

  only:

    - cyr_dev