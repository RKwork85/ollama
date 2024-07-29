# Ollama仓库 记录

## 部署：
ubuntu下：

>curl -fsSL https://ollama.com/install.sh | sh

即可

然后启动一个模型进行命令行对话：

>ollama run llama3

对 ollama 服务控制
```
systemctl start ollama 
systemctl stop ollama 
systemctl status ollama 

```
启动服务：

    export OLLAMA_HOST=0.0.0.0:11434
    ollama serve 


ollma + open-webui


docker run -d -p 3000:8080 --add-host=host.docker.internal:host-gateway -v open-webui:/app/backend/data --name open-webui --restart always ghcr.io/open-webui/open-webui:main


open-webui serve