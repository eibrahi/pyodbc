TMP_PATH := .tmp
IMAGE_NAME := laudio/pyodbc-sqlcmd

clean:
	@rm -rf $(TMP_PATH) __pycache__ .pytest_cache
	@find . -name '*.pyc' -delete

build:
	@docker build --target=base -t $(IMAGE_NAME) .
	@docker build --target=test -t $(IMAGE_NAME):test .

test:
	@docker run --env-file=./.env.test --network=host $(IMAGE_NAME):test

check:
	@pyright --verbose

.PHONY: all test clean
