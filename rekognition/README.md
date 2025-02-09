# Amazon Rekognition

Amazon Rekognition é um serviço da AWS que permite análise de imagens e vídeos utilizando inteligência artificial. Com ele, é possível identificar objetos, cenas, rostos, textos, e até mesmo detectar sentimentos e atividades em imagens e vídeos.

## Principais Funcionalidades

### Pelo Portal da AWS
- **Detecção de Objetos e Cenas**: Identifica elementos como carros, pessoas, animais, etc.
- **Reconhecimento Facial**: Identifica e analisa rostos, determinando emoções e características.
- **Detecção de Texto (OCR)**: Extrai textos de imagens.
- **Moderação de Conteúdo**: Identifica conteúdos impróprios.
- **Análise de Vídeos**: Permite a identificação de objetos e faces em vídeos.

### Via API com Python
Com a SDK da AWS para Python (boto3), é possível integrar o Amazon Rekognition em aplicações para:
- Analisar imagens enviadas diretamente.
- Comparar rostos em diferentes imagens.
- Identificar celebridades.
- Monitorar eventos em tempo real.

## Configuração do Ambiente

### Windows

1. **Instalar o Python**
   - Baixe e instale a versão mais recente do [Python](https://www.python.org/).
   - Certifique-se de adicionar o Python ao PATH durante a instalação.

2. **Instalar o AWS CLI**
   - Baixe e instale o [AWS CLI](https://aws.amazon.com/cli/).
   - Configure com o comando:
     ```sh
     aws configure
     ```
     Insira suas credenciais de acesso da AWS.

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

def detect_labels(image_path):
    client = boto3.client('rekognition')
    
    with open(image_path, 'rb') as image_file:
        image_bytes = image_file.read()
    
    response = client.detect_labels(Image={'Bytes': image_bytes}, MaxLabels=10)
    
    for label in response['Labels']:
        print(f"{label['Name']} - Confiança: {label['Confidence']:.2f}%")

# Testando com uma imagem detect_labels('imagem.jpg')
```
