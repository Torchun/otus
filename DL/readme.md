@host: </br>
<code>docker build -t ai/first -f ./Dockerfile .</code></br>
<code>docker run -ti -v /data:/data -p 8888:8888 --rm ai/first /bin/bash</code>
