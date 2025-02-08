# Amazon Textract

Amazon Textract é um serviço da AWS que utiliza aprendizado de máquina para extrair automaticamente texto, manuscritos e dados de documentos digitalizados. Ele permite processar documentos de forma rápida e eficiente, reduzindo a necessidade de entrada manual de dados.

## Principais Funcionalidades

### Pelo Portal da AWS
- **Extração de Texto e Dados**: Converte imagens e PDFs digitalizados em texto editável.
- **Detecção de Campos de Formulário**: Identifica e extrai informações de formulários estruturados.
- **Reconhecimento de Tabelas**: Mantém a estrutura de tabelas ao extrair dados.
- **Processamento de Documentos em Lote**: Permite analisar vários documentos simultaneamente.
- **Integração com Outros Serviços AWS**: Pode ser usado junto com Amazon S3, Lambda, e DynamoDB.

### Via API com Python
Com a SDK da AWS para Python (boto3), é possível:
- Extrair texto de imagens e PDFs.
- Identificar e processar formulários automaticamente.
- Exportar resultados estruturados para bancos de dados e outras aplicações.

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

def extract_text_from_image(image_path):
    client = boto3.client('textract')
    
    with open(image_path, 'rb') as image_file:
        image_bytes = image_file.read()
    
    response = client.detect_document_text(Document={'Bytes': image_bytes})
    
    extracted_text = ''
    for item in response['Blocks']:
        if item['BlockType'] == 'LINE':
            extracted_text += item['Text'] + '\n'
    
    print(extracted_text)

# Testando com uma imagem
extract_text_from_image('documento.jpg')
```

Informação criada usando [ChatGPT](https://www.chatgpt.com)