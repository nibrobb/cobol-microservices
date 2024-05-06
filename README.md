# COBOL + CI/CD = ❤️

## Quick start

Get the latest exchange rates from the [EBC](https://www.ecb.europa.eu/stats/policy_and_exchange_rates/euro_reference_exchange_rates/html/index.en.html) and put them in resources

```bash
mkdir -p resources/ && wget -O - https://www.ecb.europa.eu/stats/eurofxref/eurofxref.zip?... | unzip -d resources/ -
```


## Install the neccecary modules
```bash
mkdir -p modules

npm install -g cobolget

cobolget init

cobolget add core-network

cobolget add core-string

cobolget add --debug gcblunit

cobolget update

cobolget -t bca12d6c4efed0627c87f2e576b72bdb5ab88e34 install
```

## Docker - build the image
```bash
docker build --tag microservice .
```

## Run the container
```bash
docker run -d -i --name microservice -p 8000:8000 microservice
docker exec -i microservice cobc -j -x src/microservice.cbl
```

## Stop the container
```bash
docker rm --force microservice
```


Source: https://medium.com/swlh/modern-cobol-microservice-tutorial-7d7d738f0b00