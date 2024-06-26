# MNIST image generation with GMMs 🔢

- This repo contains a frontend web client and a backend python service for an MNIST generator
- PCA is used to reduce the dimentionality and GMM is used for sampling
  
## Quick start
### Dependencies
- Docker Desktop 🐋 
### Step-by-step
1. Download `train.csv` and `test.csv` files from https://www.kaggle.com/code/ngbolin/mnist-dataset-digit-recognizer/input
2. Place both files in `service/data`
3. From project root run `run_linux.sh` or `run_windows.bat` depending on your OS

- Verify api is running at http://localhost:4000
- Initialize model by calling the /initialize endpoint
- Verify client is running at http://localhost:4001

### Troubleshoot
- Verrify containers are running with 'docker ps -a' (`bayes-classifier-gmm-api`, `bayes-classifier-gmm-db`, `bayes-classifier-gmm-migration` and `bayes-classifier-gmm-client`)
- Verify data has been successfully migrated (you can use a client like MongoDB Compass):
  - Connection string: `mongodb://localhost:27017/`
  - Db: `bayes_classifier_gmm`
  - Collection: `MNIST_train`

### Settings
- If you don't want to run data migration set `RUN_MIGRATION=false` in `./service/.env`
- GMM_COMPONENTS - number of mixture components (per label)
- PCA_COMPONENTS - number of components (dimentionality) of each image to keep