**📚 Imersão Alura DevOps – API Escola**

Este projeto faz parte da Imersão DevOps da Alura, onde foi construída uma API de gestão de escola com FastAPI, containerizada com Docker, e realizada a publicação no Google Cloud Run.

**🚀 Tecnologias utilizadas**

Python 3.13.5

FastAPI

Uvicorn

Docker

Google Cloud Platform (Cloud Build + Cloud Run)


**💻 Passo a passo para rodar a aplicação**


**🔹 1. Clonar o repositório**

git clone [https://github.com/Fernanda-Damasceno2024/imersao-alura-devops/tree/main]

cd SEU_REPOSITORIO

**🔹 2. Criar e ativar o ambiente virtual**

**Windows**

python -m venv venv

venv\Scripts\activate

**Linux/macOS**

python3 -m venv venv

source venv/bin/activate

**🔹 3. Instalar as dependências**

pip install -r requirements.txt

**🔹 4. Rodar o servidor localmente**

uvicorn app:app --reload

Acesse em: http://Localhost:8000/docs


**🐳 Passo a passo para usar Docker**

**🔹 5. Criar o Dockerfile**

FROM python:3.13.5-alpine3.22

WORKDIR /app

COPY requirements.txt .

RUN pip install --no-cache-dir -r requirements.txt

COPY . .

EXPOSE 8000

CMD ["sh", "-c", "uvicorn app:app --host 0.0.0.0 --port $PORT"]


**🔹 6. Build da imagem**

docker build -t imersao-alura-devops .

**🔹 7. Rodar a aplicação no container**

docker run -p 8000:8000 imersao-alura-devops


**☁️ Passo a passo para deploy no Google Cloud Run**


**🔹 8. Build e push da imagem para o Container Registry**

gcloud builds submit --tag gcr.io/SEU_PROJETO/imersao-alura-devops

**🔹 9. Deploy no Cloud Run**

gcloud run deploy imersao-alura \

  --image gcr.io/SEU_PROJETO/imersao-alura-devops \
  
  --platform managed \
  
  --region us-central1 \
  
  --allow-unauthenticated \
  
  --port 8000
  
**🔹 10. Acessar a API no navegador**

URL gerada pelo Google Cloud Run

Adicione /docs ao final para acessar a documentação interativa Swagger

**⚠️ Possíveis erros e soluções**

**✅ Erro:** PORT não configurado

**💡 Solução:** usar CMD com variável $PORT no Dockerfile

**✅ Erro:** requirements.txt não encontrado

**💡 Solução:** verificar se está na raiz do projeto antes de buildar a imagem

**✅ Erro:** 'build' não reconhecido como comando

**💡 Solução:** usar docker build e não apenas build


**📎 Licença**

Projeto de estudo sem fins comerciais.

Criado na Imersão DevOps Alura.
