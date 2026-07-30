As imagens de container são as responsáveis por fazer com que o ambiente isolado dos containers funcionem, elas são um pacote padronizado que inclui todos os arquivos, libs, binários, configurações etc para rodar aquele container. No dockerHub você pode encontrar tanto imagens oficiais quanto as feitas por outros desenvolvedores para apenas instalar elas no seu container e começar a rodar o que você precisa.

Existem dos princípios das imagens:
 - Elas são imutáveis, ou seja, quando uma imagem é criada ela não pode ser modificada, você precisa fazer uma nova imagem ou adicionar coisas nela.
 - As imagens são feitas de camadas, cada camada representa um conjunto de arquivos do sistema que adicionam, removem ou modificam os arquivos.

As imagens são divididas em 5 camadas para sua construção, sendo elas:

1. A primeira camada é a responsável por adicionar comandos e gerenciadores de pacotes como APT ou PACMAN
2. A segunda camada é a responsável por instalar as dependências do seu APP, como em um exemplo instalar uma Runtime de Python (responsável por rodar o Python) e o gerenciador de dependências como o PIP.
3. A terceira camada é responsável por copiar todos os requisitos da aplicação como por exemplo os pacotes que estão dentro de requirements.txt em um projeto Python.
4. A quarta camada é a de instalação, ela é a responsável por instalar os pacotes copiados na camada anterior
5. Por fim, a quinta camada é a que copia o código fonte da aplicação para dentro da imagem.

![[Pasted image 20260730110016.png]]

Um dos beneficios desse sistema de camadas é que elas podem ser reutilizadas entre as imagens. Por exemplo, digamos que você esteja construindo duas aplicações, cada uma com suas dependências, pacotes mas que compartilham da mesma base, você pode reutilizar as camadas para acelerar o processo de criação da imagem como na foto abaixo:

![[Pasted image 20260730110227.png]]

