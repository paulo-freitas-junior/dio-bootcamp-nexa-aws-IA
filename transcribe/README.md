# Amazon Transcribe

Amazon Transcribe é um serviço da AWS que converte automaticamente áudio em texto utilizando tecnologia de reconhecimento automático de fala (ASR). Ele é ideal para transcrição de chamadas telefônicas, conferências, legendagem de vídeos e outros casos de uso que exigem extração de texto a partir de áudio.

## Principais Funcionalidades

### Pelo Portal da AWS
- **Transcrição Automática**: Converte arquivos de áudio em texto de forma precisa.
- **Identificação de Locutores**: Diferencia múltiplos falantes no áudio.
- **Pontuação e Formatação**: Adiciona automaticamente pontuação ao texto transcrito.
- **Suporte a Vários Idiomas**: Transcreve áudio em diversos idiomas.
- **Filtragem de Palavras**: Permite remover ou substituir palavras sensíveis.

### Via API com Python
Com a SDK da AWS para Python (boto3), é possível:
- Iniciar transcrição de arquivos armazenados no Amazon S3.
- Monitorar o status da transcrição.
- Recuperar e processar o texto gerado.

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

def transcribe_audio(job_name, audio_file_uri):
    client = boto3.client('transcribe')
    
    response = client.start_transcription_job(
        TranscriptionJobName=job_name,
        Media={'MediaFileUri': audio_file_uri},
        MediaFormat='mp3',
        LanguageCode='en-US'
    )
    
    print(f"Transcrição iniciada: {response['TranscriptionJob']['TranscriptionJobName']}")

# Testando com um arquivo no S3
transcribe_audio('meu_job', 's3://meu-bucket/meuarquivo.mp3')
```
