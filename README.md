# Onlyfeet

Web hacking challenge developed for my yearly workshop on offensive security for web.

## Setup

1. Create and prepare `src/users.json`
2. Set `FLAG` in `.env`
2. Create Azure container registry `cronlyfeet`
3. Build and deploy image

	```bash
	sudo service docker start
	docker login cronlyfeet.azurecr.io
	docker build . -t onlyfeet
	docker tag onlyfeet:latest cronlyfeet.azurecr.io/onlyfeet:latest
	docker push cronlyfeet.azurecr.io/onlyfeet:latest
	```

4. Create Azure web app for containers `app-onlyfeet`

	```bash
	az deployment group create --name onlyfeet --resource-group rg-onlyfeet --template-file deploy/template.json --parameters deploy/parameters.json
	```