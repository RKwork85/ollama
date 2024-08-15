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




curl http://localhost:11434/api/chat -d '{
  "model": "llama3.1",
  "messages": [
    {
      "role": "user",
      "content": "What is the weather today in Paris?"
    }
  ],
  "stream": false,
  "tools": [
    {
      "type": "function",
      "function": {
        "name": "get_current_weather",
        "description": "Get the current weather for a location",
        "parameters": {
          "type": "object",
          "properties": {
            "location": {
              "type": "string",
              "description": "The location to get the weather for, e.g. San Francisco, CA"
            },
            "format": {
              "type": "string",
              "description": "The format to return the weather in, e.g. 'celsius' or 'fahrenheit'",
              "enum": ["celsius", "fahrenheit"]
            }
          },
          "required": ["location", "format"]
        }
      }
    }
  ]
}'