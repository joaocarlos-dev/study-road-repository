O dockerfile é um arquivo de texto utilizado para a construção das [[Containers]] [[Images]] da aplicação dentro do docker. Para essa construção é utilizado uma série de comandos respeitando a ordem das layers da image.

Para essa construção temos os seguintes comandos:

 - `FROM <image>`: especifica a imagem que aquela build vai utilizar. 
 - `WORKDIR <path>`: Especifica o 'Working Directory' ou o caminho na imagem para onde os arquivos serão copiados e onde os comandos serão executados
 - `COPY <host-path> <image-path>`: Especifica para o builder para copiar os arquivos do caminho do host para o caminho da imagem. 
 - `RUN <command>`: Informa o builwer para rodar um determinado comando
 - `ENV <name> <value>`: Define as variáveis de ambiente que o container irá utilizar.
 - `EXPOSE <port-number>`: Define a porta que será exposta da Imagem.
 - `USER <user-or-uid>`: Define um usuário padrão para todas as ações a partir dessa.
 - `CMD ["<command>", "<arg1>"]` Define o comando padrão que o container usando aquela imagem irá rodar.

A referência completa dos comando está disponível em: https://docs.docker.com/reference/dockerfile

Exemplo de Dockerfile pronto para rodar:

```dockerfile
FROM python:3.13
WORKDIR /usr/local/app

# Install the application dependencies
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

# Copy in the source code
COPY src ./src
EXPOSE 8080

# Setup an app user so the container doesn't run as the root user
RUN useradd app
USER app

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8080"]
```

No exemplo acima estamos dizendo ao Dockerfile o seguinte, crie um container com uma Imagem python na versão 3.13 dentro do caminho `/usr/local/app`, logo em seguida copie o arquivo `requirements.txt` para a raiz dessa Imagem e rode o pip install para instalar os pacotes de reuirements.txt dentro do container. 

Com isso feito, copie a pasta src do host para a pasta src da Imagem, exponha a porta 8080, rode o comando `useradd` para adicionar o usuário `app` e por fim, utilize esse usuário e rode o comando do uvicorn no CMD para rodar a main na porta 8080 que foi exposta.

Existem muitas outras configurações que podem ser feitas em uma Imagem como healthchecks, definir autores e várias outras coisas.
