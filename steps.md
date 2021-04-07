General 
```
gcloud services enable containerregistry.googleapis.com

gcloud config set run/region us-central1
gcloud config set run/platform managed


```

Auth
```
 gcloud auth application-default login
 #Or manually set the GOOGLE_APPLICATION_CREDENTIALS environment variable to point to a service account key JSON file path.

```

Proj id
```
gcloud projects list
#PROJECT_ID               NAME       PROJECT_NUMBER
#cogeco-44-410-dev-00016  elite-dev  888170786432
```
Build
```
mvn compile jib:dockerBuild

```

Run local 

```

set PROJECT_ID=cogeco-44-410-dev-00016
set CR_APP_NAME=tmf652-resource-order-v4
set PORT=8080
docker run --rm -p 9090:%PORT% -e PORT=%PORT% gcr.io/%PROJECT_ID%/%CR_APP_NAME%
#docker run --rm -p 9090:${PORT} -e PORT=${PORT} gcr.io/${PROJECT_ID}/${CR_APP_NAME}
```

In Crun

```androiddatabinding
# push image
set PROJECT_ID=cogeco-44-410-dev-00016
set CR_APP_NAME=tmf652-resource-order-v4

gcloud auth configure-docker
docker tag gcr.io/cogeco-44-410-dev-00016/tmf652-resource-order-v4 gcr.io/cogeco-44-410-dev-00016/tmf652-resource-order-v4:0.0.1
docker -- push gcr.io/cogeco-44-410-dev-00016/tmf652-resource-order-v4:0.0.1
```

```

gcloud run deploy --image gcr.io/${PROJECT_ID}/${CR_APP_NAME}
gcloud run deploy --image gcr.io/cogeco-44-410-dev-00016/tmf652-resource-order-v4:0.0.1
```