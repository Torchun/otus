@host: </br>
<code>docker build -t ai/first -f ./Dockerfile .</code></br>
<code>docker run -ti -v /data:/data -p 8888:8888 --rm ai/first /bin/bash</code></br>
</br>
@container: </br>
<code>jupyter-lab --allow-root --no-browser --port 8888 --ip '0.0.0.0'</code></br>
-or-</br>
@host:</br>
<code>docker run -ti -v /data:/data -p 8888:8888 --rm ai/first /opt/miniconda/bin/jupyter-lab --allow-root --no-browser --port 8888 --ip '0.0.0.0'</code></br>
