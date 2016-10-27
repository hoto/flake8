# Flake8 docker image

Docker image with [flake8](http://flake8.pycqa.org/en/latest/) python linter.


### Usage

* docker cli

```
docker run --rm \
    -v /myscripts:/scripts \
    -v /.flake8/.flake8 \
    hoto/flake8:3.0.4 \
    flake8 /scripts
```

* docker-compose

`docker-compose.yml`

```yaml
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
lint:
  image: hoto/flake8:3.0.4
  stage: lint
  tags:
    - dind
  script:
    - flake8 scripts/ tests/
```