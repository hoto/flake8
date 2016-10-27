# Flake8 docker image

Docker image with [flake8](http://flake8.pycqa.org/en/latest/) python linter.


### Usage

* Docker

```
docker run -v $(pwd)/scripts:/scripts hoto/flake8:3.0.4 /scripts
```

* Docker Compose

```yaml
#docker-compose.yml
version: '2'

services:

  lint:
    image: hoto/flake8:3.0.4
    command: flake8 /scripts /tests
    volumes:
      - ./scripts:/scripts
      - ./tests:/tests
      - ./.flake8:/.flake8
```

* Gitlab CI Runner

```yaml
#.gitlab-ci.yml
lint:
  image: hoto/flake8:3.0.4
  stage: lint
  tags:
    - dind
  script:
    - flake8 scripts/ tests/
```
