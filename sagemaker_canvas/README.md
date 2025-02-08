# Amazon SageMaker Canvas

Amazon SageMaker Canvas é um serviço da AWS que permite criar modelos de machine learning sem necessidade de codificação. Ele fornece uma interface visual intuitiva para construir, treinar e implantar modelos de aprendizado de máquina, facilitando a adoção de IA por usuários com pouca ou nenhuma experiência técnica.

## Principais Funcionalidades

### Pelo Portal da AWS
- **Importação de Dados**: Suporte a diversas fontes de dados, incluindo Amazon S3, bancos de dados e arquivos CSV.
- **Criação Automática de Modelos**: Análise de dados e sugestão de algoritmos adequados automaticamente.
- **Treinamento e Avaliação**: Gera previsões e permite comparação de modelos.
- **Geração de Previsões**: Possibilidade de realizar previsões em tempo real ou batch.
- **Integração com SageMaker Studio**: Permite exportar modelos para maior customização com código Python.

### Via API com Python
Com a SDK da AWS para Python (boto3), é possível:
- Criar e gerenciar modelos do SageMaker Canvas.
- Exportar e implantar modelos em ambientes SageMaker.
- Automatizar fluxos de trabalho de machine learning.

## Configuração do Ambiente

### Windows

1. **Instalar o Python**
   - Baixe e instale a versão mais recente do [Python](https://www.python.org/).
   - Durante a instalação, selecione a opção para adicionar Python ao PATH.

2. **Instalar o AWS CLI**
   - Baixe e instale o [AWS CLI](https://aws.amazon.com/cli/).
   - Configure suas credenciais:
     ```sh
     aws configure
     ```

3. **Instalar o boto3**
   ```sh
   pip install boto3
   ```

### Linux (Debian-Based)

1. **Instalar Dependências**
   ```sh
   sudo apt update && sudo apt install -y python3 python3-pip
   ```

2. **Instalar o AWS CLI**
   ```sh
   curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
   unzip awscliv2.zip
   sudo ./aws/install
   ```
   - Verifique a instalação:
     ```sh
     aws --version
     ```

3. **Configurar Credenciais**
   ```sh
   aws configure
   ```

4. **Instalar o boto3**
   ```sh
   pip3 install boto3
   ```

## Exemplo de Uso com Python

```python
import boto3

def list_sagemaker_models():
    client = boto3.client('sagemaker')
    response = client.list_models()
    
    for model in response['Models']:
        print(f"Modelo: {model['ModelName']}")

# Executando a função
list_sagemaker_models()
```

Informação criada usando [ChatGPT](https://www.chatgpt.com)