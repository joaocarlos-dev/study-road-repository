As imagens de container são as responsáveis por fazer com que o ambiente isolado dos containers funcionem, elas são um pacote padronizado que inclui todos os arquivos, libs, binários, configurações etc para rodar aquele container. No dockerHub você pode encontrar tanto imagens oficiais quanto as feitas por outros desenvolvedores para apenas instalar elas no seu container e começar a rodar o que você precisa.

Existem dos princípios das imagens:
 - Elas são imutáveis, ou seja, quando uma imagem é criada ela não pode ser modificada, você precisa fazer uma nova imagem ou adicionar coisas nela.
 - As imagens são feitas de camadas, cada camada representa um conjunto de arquivos do sistema que adicionam, removem ou modificam os arquivos.