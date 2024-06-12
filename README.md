# Docker_estudos

-- Containers :
 -Isolamento entre eles
 -Controlo meus recursos (X container vai usar x% do meu hardware)
 -Mais leve que uma VM
- Container executa o que esta sendo informado na minha imagem 


-Um Dockerfile é um arquivo de texto que contém uma série de instruções que o Docker usa para criar uma imagem Docker;


Qual a diferença entre Imagem e Container?
Traçando um paralelo com o conceito de orientação a objeto, a imagem é a classe e o container o objeto. A imagem é a abstração da infraestrutura em estado somente leitura, de onde será instanciado o container.

Todo container é iniciado a partir de uma imagem, dessa forma podemos concluir que nunca teremos uma imagem em execução.

Um container só pode ser iniciado a partir de uma única imagem. Caso deseje um comportamento diferente, será necessário customizar a imagem.

Site : https://stack.desenvolvedor.expert/appendix/docker/criandoimagem.html




![image](https://github.com/KamillaLima/Docker_estudos/assets/102989894/9ca09784-5072-41ce-810d-43c3bf7a0beb)



 ----- Comandos 
 - Docker ps  > Listagens de todos os containers em execução ( retorna o id do container , mt importante para outros comandos , tipo o docker stop {container_id} 
 - Docker ps -a / docker ls -a  > Listagem de todos os containers (independente se ele está em execução no momento ou não)
 - Docker rm {id do container ou nome do container} - Exclusão de um container
 - Docker rmi {nome da imagem e a tag dela } - Exclusão de uma imagem . ATENÇÃO : só é possível realizar a exclusão da imagem se primeiro for removido o container
 - Docker run --name {nome que eu quero pro meu container}  -it ubuntu > Criando um container com o nome que eu quero . O -it é para que seja simulado um terminal ali dentro do meu container ( pra sair desse terminal CRTL+D )  -- DOCKER RUN : DOCKER CREATE + DOCKER START
 - Docker run -di ubuntu > Meu container vai ficar executando ,porém eu não vou entrar dentro do terminal dele
 - docker exec {id do container} echo "mensagem que eu quero imprimir" > Imprimindo uma mensagem dentro do meu container que está em execução
 - docker stop {id do container} > Pausando um container
 - docker start -ai {id do container}  > Dando start em um container que já existe , ai é pra eu crie ali um terminalzinho do meu container (CTRL + D pra sair dele)
 - docker create -it {nome da imagem } > Criando um container
 - docker rm -f {nome do container} > Parando e removendo um container
 - docker kill {nome do container} >  Matar o processo principal do container imediatamente .É importante ter cuidado ao utilizar esse comando, pois ele não permite que o container finalize seus processos corretamente, o que pode resultar em perda de dados ou instabilidade no ambiente.
 - docker stop {nome do container}  > Vai matar o processo também ,  a diferença é de que ele será de uma forma mais amigável , pausando/finalizando todas as coisas necessárias para ai sim pausar o container (leva uns 10 segundos,enquanto o kill leva uns 2).Mais indicado
 - docker pause {nome do container} > Pausando o container ,mas tudo ainda vai ficar la dentro certinho 
 - docker rename {nome do meu container} {nome novo pro meu container}  > Renomeando um container
 - unpause {nome do container} > Despausando o meu container
 - docker restart {nome do container} > Reiniciando o container
 - docker run dokcersamples/static-site - Iniciando um container, dockersample = usuário que criou essa imagem , static site = nome da imagem. Deve colocar o nome do usuário caso a imagem criada não seja oficial do docker 
 - docker run -P -d dockersamples/static-site - Iniciando um container , o -d é pro meu terminal não ficar travado , já ó -P é para que o docker seja o responsável por mapear as portas
 - docker run -p 5000:80 -d dockersamples/static-site - Iniciando um container , o -p é para que eu mapeie as portas manualmente , 5000:80 é 5000 a porta referente a minha máquina e a 80 é a porta referente dentro do container


   ![image](https://github.com/KamillaLima/Docker_estudos/assets/102989894/e9eabcf1-8591-49d6-b761-f5e028c0a328)
   As imagens NÃO SÃO ALTERAVEIS,desse modo,mais de um container pode consumir uma imagem e realizar alterações,pois a imagem usada não vai ser alterada
   



 --- Dockerfile
 Se trata de um arquivo de texto onde irá conter todas as instruções para a criação de uma imagem.A extensão do arquivo é .dockerfile ou posso chamar de Dockerfile diretamente.Geralmente se usa com extensão quando possui mais de um arquivo dockerfile em uma mesma pasta.
 - docker build -t {nome_imagem} . - Buildando a imagem , o nome da imagem eu posso escolher o que quiser  , o ponto é porque eu já estou dentro do diretorio aonde esta o meu arquivo dockerfile
