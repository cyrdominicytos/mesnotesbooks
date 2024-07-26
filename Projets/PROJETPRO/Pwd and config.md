
VM Istic

pwd : Qcmapp!2024! (Z)
user : zprojet
vm name : qcmapp
ip : 

https://youtu.be/mFHnaTZUQgA

https://www.fosstechnix.com/gitlab-ci-deploy-to-ec2-using-ssh/#comment-14092



ssh-rsa AAAAB3NzaC1yc2EAAAADAQABAAACAQDQfABLWjxqudvaC9ujHZ6U09421H7MOZYrISUFL5rAUtBQc2qoi1uchVhGRFER9kCneaHlp68sD2wIhux4n0sU3a8VqzmE5P5S71A+U3D60rBVOp3xJnFMsL8SG7MFGNzAjJy4/DsBQ+nqvUw2MUCP8MI+cpJLV2DaXpAYH0UicGlnntTjNRmcWIU0qphoJYgNx+xClGH3/Ts+BgmOi1iEwtgnBRbHZPLfkQ6VEYms0SEll7gsWnoWQ4gMUvSuwjuv4izEhS/TTZ4y8N7+jiOPjn0eCzUvRDDl+agS/wZIDS6o48pAJQcgna+KVcNXifI9rxI34gPSyrzTUEmKjR0xSGCJ8+FjrtJFYA31Eba333JOqs2jp/ZsMh2isl5bGJgS7OSj6NR6YiK7oMmt6PByrKPB3FvSgzKqOsMVfQyN7O/bQQhSDS/v+8PH7H8zrKCPAUsGvn53373jSYM88Ni/Njdb3TOFuIi+vLeEYF6rd6vKC8R91kLqqp8lGKxYTLdhKL6OE0YNWBQCWIoa2HWjGjQUd6IXtd9HwjikFy+NnZP6NDlxtHF10XG3Bp0gA9nyT4MSlifnKdfAstZanSr58my9xAB/virqJBLyG8y6baD+HxdzcPHuiAjjX7Us62zqYU46DpM5zkiQymogEsyAN7X84ghHvNNonaHP+JwEsQ== cyriaque.tossou@etduiant.univ-rennes.fr


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
  - export PATH="$PATH:/root/.m2"

build:
  stage: build
  image: maven:3.8.3-openjdk-17
  script:
    - mvn $MAVEN_CLI_OPTS clean package -DskipTests
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
  script:
    - apk add --no-cache openssh
    - scp -o StrictHostKeyChecking=no target/*.jar $SSH_USER@$VM_NAME:/path/to/deploy/
    - ssh your_user@your_vm_ip 'docker-compose down && docker-compose up -d'
  only:
    - master




gitlab-runner register \ --non-interactive \ --url "https://gitlab.istic.univ-rennes1.fr" \ --registration-token "glrt-zqZqykQNjnLR7TjKfjP-" \ --description "docker-runner" \ --executor "docker" \ --docker-image debian:latest


gitlab-runner register  --url https://gitlab.istic.univ-rennes1.fr  --token glrt-zqZqykQNjnLR7TjKfjP-