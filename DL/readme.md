@host: 
docker build -t ai/first -f ./Dockerfile .
docker run -ti -v /data:/data -p 8888:8888 --rm ai/first /bin/bash
