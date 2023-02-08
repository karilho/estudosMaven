# MAVEN 

### 1 - O QUE É O MAVEN?

O maven é uma tentativa de aplicar padrões a infraestrutura de construção de um projeto para melhorar a compreensão
e produtividade do mesmo, fornecendo um caminho claro em busca de melhores práticas.

O maven, também é essencialmente uma ferramento de gestão e compreensão de projetos, ajudando em:

* Compilações 
* Gerenciamento de dependências
* Testes
* Documentações
* Distribuição
* Lançamentos

### 2 - INSTALAÇÃO

Para instalar o maven, basta acessar o site oficial do maven, baixar a versão recente e seguir as instruções de instalação.

### 3 - CRIANDO O PRIMEIRO PROJETO COM O MAVEN.

Para criar um projeto com o maven, temos um exemplo de comando que pode ser utilizado para criar um projeto com o maven básico.

    mvn archetype:generate -DgroupId=com.estudosMaven -DartifactId=estudosMaven -DarchetypeArtifactId=maven-archetype-quickstart -DarchetypeVersion=1.4 

Realizando o comando a seguir, teremos a seguinte estrutura: *IGNORE* o .idea (é criado pela IDE).

    mavenStudy
    ├── pom.xml
    └── src
        ├── main
        │   ├── java
        │   │   └── com
        │   │       └── estudosMaven
        │   │           └── App.java
        │   └── resources
        └── test
            ├── java
            │   └── com
            │       └── estudosMaven
            │           └── AppTest.java
            └── resources

### 4 - EXPLICAÇÃO DOS COMANDOS

* **mvn archetype:generate** - comando para gerar um projeto maven.
* **-DgroupId** - define o nome do pacote do projeto, no no casso caso foi estudosMaven.
* **-DartifactId** - define o nome do projeto, no caso estudosMaven.
* **-DarchetypeArtifactId** - define o "esqueleto" de projeto que será criado, no caso maven-archetype-quickstart foi o utilizado.
* **-DarchetypeVersion** - define a versão do "esqueleto" de projeto que será criado, no caso 1.4 foi a versão utilizada.

### 5 - EXPLICAÇÃO DA ESTRUTURA

* **pom.xml** - arquivo de configuração do maven, onde ficam as dependências, plugins, etc.
* **main** - pasta onde ficam os arquivos fontes do projeto.
* **java** - pasta onde ficam os arquivos fontes de testes do projeto.

### 6 - EXPLICAÇÃO DO ARQUIVO POM.XML
O arquivo criado pom.xml, cuja abreviação significa Project Object Model, é considerado a unidade básica e central de trabalho
em quem o maven irá se apoiar para construir o projeto, nele são colocadas informações sobre o projeto, como nome, versão,
dependências, plugins, propriedades etc.

### 7 - COMANDOS UTILIZADOS MAVEN
Ok, o projeto foi definido, com pastar, subpastas e seu executável, porém, como é seu funcionamento com o maven?
A seguir, vou listar alguns comandos que são utilizados no maven.

* **MVN COMPILE** - Compila a nossa aplicação, baixando as dependências necessárias declaradas no pom.xml, o que acabará
como resultado na criação do diretório target, responsável por armazenar os arquivos compilados.
* **MVN TEST COMPILE** - Realiza o mesmo processo que o anterior, porém, para os arquivos de testes.
* **MVN PACKAGE** - Empacota o projeto, gerando um arquivo .jar, .war, .ear, etc dependendo do que foi específicado, 
este arquivo será gerado no diretório target com nome, versão, e SNAPSHOT (o que significa que não é a versão estável ou definitiva).
* **MVN INSTALL** - Instala o projeto no repositório local, que é por padrão maven o .m2/repository, para que possa ser utilizado em outros projetos.
* **MVN DEPLOY** - Faz o deploy do projeto no repositório remoto, como o git, bitbucket, etc.

### 8 - CICLO DE VIDA DO MAVEN
O maven possui 3 ciclos de vida, que são compostos por fases que são executadas em sequência, são eles:
#### 8.1 - CICLO DE VIDA DEFAULT
O ciclo de vida default é o ciclo de vida padrão do maven, possuindo um padrão de construção e distribuição de projeto bem definido.
As fases do ciclo de vida default são, em um exemplo padrão (há outros tipos de fases para o ciclo de vida default):

* **VALIDATE** - Verifica se o projeto está correto e todas as informações necessárias estão disponíveis.
* **COMPILE** - Compila o código fonte do projeto.
* **TEST** - Testa o código compilado, usando um framework de teste como JUnit.
* **PACKAGE** - Pega o código compilado e o empacota em um formato como JAR, WAR ou EAR.
* **VERIFY** - Executa qualquer verificação necessária no pacote para garantia com seus testes de integração e que ele é válido para ser publicado.
* **INSTALL** - Instala o pacote no repositório local, para que possa ser usado como uma dependência em outros projetos localmente.
* **DEPLOY** - Faz o deploy do pacote no repositório remoto, para que possa ser usado como uma dependência em outros projetos remotamente.

***IMPORTANTE*** - Caso seja utilizado por exemplo, o comando mvn install, o maven irá executar todas as fases do ciclo 
de vida default até o install, o mesmo vale para todos os outros comandos, por isso este é o motivo dele ser o mais utilizado.
Todas essas fases podem ser utilizadas separadamente no terminal do maven, por exemplo, mvn validate, irá executar apenas 
a fase validate do ciclo de vida default, porém se usarmos o comando mvn compile, ele irá executar o validate e o compile.

### 8.2 - CICLO DE VIDA CLEAN
O ciclo de vida clean é o ciclo de vida responsável por limpar os arquivos gerados pelo maven, como por exemplo, os 
arquivos compilados, os arquivos empacotados entre outros.

Cabe destacar que o ciclo de vida tem como objetivo principal a limpeza dos arquivos gerados pelo maven, porém, ele não 
limpa os arquivos gerados pelo projeto.

Possui somente 3 fases: pre-clean, clean e post-clean. Que basicamente estão relacionados diretamente com limpeza e não 
há necessidade de menção.

### 8.3 - CICLO DE VIDA SITE
O ciclo de vida site é o ciclo de vida responsável por gerar o site do projeto, que é gerado no diretório target/site, em 
que podemos ver informações do projeto, como por exemplo, informações sobre as dependências, plugins, relatórios de testes, etc.

Essa informações são geradas em um arquivo chamado index.html, que é o arquivo principal do site do projeto.

Possui 4 fases que são: pre-site, site, post-site e site-deploy, que, pelo mesmo motivo anterior, não há necessidade de menção.


## 8.4 EXTRA

***IMPORTANTE*** - O maven possui também a possibilidade de combinações de diversos tipos de ciclos de vida, como, por exemplo,
o comando mvn clean install site, que irá realizar o ciclo de vida clean, depois o ciclo de vida default até a fase install,
e por fim, o ciclo de vida site.

## 9 - CONSIDERAÇÕES FINAIS

Como podemos ver, o maven é uma ferramenta muito poderosa e que pode nos ajudar muito no desenvolvimento de projetos. 
Por enquanto, não serão abordados temas como archetypes (outros esqueletos padrão), plugins e detalhadamente o POM.xml,
porém, futuramente serão abordados.

Todas as informações aqui elencadas foram retiradas da documentação oficial do maven, que pode ser encontrada no link:

https://maven.apache.org/guides/getting-started/index.html


  