# Atividade 1

## Passos Realizados

### Passo 1: Criar pasta e mover para a pasta
- mkdir atividade-1-computacao-em-nuvem
- cd atividade-1-computacao-em-nuvem

### Passo 2: Criar Arquivo com código de uma aplicação Flask
- nano index.py
```index
from flask import Flask

app = Flask(__name__)

@app.route('/')
def home():
    return "Olá, Docker!"

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=8080)
```

### Passo 3: Criação do Dockerfile
- nano Dockerfile
```dockerfile
FROM python:3.9-slim

WORKDIR /app

COPY . /app

RUN pip install --no-cache-dir flask

EXPOSE 8080

ENV FLASK_APP=index.py

CMD ["python", "index.py"]
```

#### Explicação do Dockerfile:

- FROM python:3.9-slim: Usa uma imagem oficial do Python 3.9
- WORKDIR /app: Define o diretório de trabalho como /app.
- COPY . /app: Copia todos os arquivos do diretório atual para o contêiner.
- RUN pip install --no-cache-dir flask: Instala o Flask no contêiner.
- EXPOSE 8080: Expõe a porta 8080 para o acesso externo.
- ENV FLASK_APP=index.py: Define a variável de ambiente FLASK_APP com o arquivo index.py.
- CMD ["python", "index.py"]: Comando padrão para iniciar a aplicação Flask.

### Passo 4: Construção da Imagem Docker
- docker build -t atividade-1-computacao-em-nuvem .

### Passo 5: Execução do Contêiner
- docker run -p 8080:8080 atividade-1-computacao-em-nuvem

### Passo 7: Verificação da Aplicação
- Agora ao abrir o navegador e acessar http://localhost:8080, vai aparecer o retorno 
do index.py que foi "Olá, Docker!" neste caso.

## Imagem do Container sendo executado
![Imagem do Contêiner](/container_img.jpg)

