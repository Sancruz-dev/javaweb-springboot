# ![DevSuperior logo](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/devsuperior-logo-small.png) Seu primeiro projeto Java Web no Spring Boot 2022
>  Veja como é simples construir uma API REST com banco de dados usando Java e Spring Boot 

## Realização
[DevSuperior - Escola de programação](https://devsuperior.com.br)

[![DevSuperior no Instagram](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/ig-icon.png)](https://instagram.com/devsuperior.ig)
[![DevSuperior no Youtube](https://raw.githubusercontent.com/devsuperior/bds-assets/main/ds/yt-icon.png)](https://youtube.com/devsuperior)

### Pré-requisitos

- Lógica de programação (qualquer linguagem)
- Programação orientada a objetos (qualquer linguagem)
- Ferramentas
  - Spring Tool Suite (STS)
  - Postman

### Objetivos da aula

- Resgatar fundamentos de programação
- Colocar em prática esses fundamentos
- Criar um pequeno sistema com ferramentas e práticas de mercado
- Dar mais um passo em direção à preparação para o mercado

### Visão geral do sistema

Vamos construir um pequeno sistema (API REST) de usuários e departamentos, com os seguintes casos de uso:

- Buscar todos usuários
- Buscar um usuário pelo seu id
- Inserir um novo usuário

![Image](https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/dominio.png "Modelo conceitual")

### Desenvolvimento moderno: relacional -> objeto -> json

![Image](https://raw.githubusercontent.com/devsuperior/java-web-spring-2022/main/img/objetos.png "Objetos")

### Passos da aula

- Criar o projeto
- Implementar o modelo de domínio
- Mapeamento objeto-relacional com JPA
- Configurar o banco de dados H2
- Criar os endpoints da API REST

### Configuração Inicial com [Spring Initializr](https://start.spring.io/)

![Print - Sprint Initilizr](https://user-images.githubusercontent.com/83969467/149042792-9f302278-5c66-496b-9c7f-587a8da54f16.png)


### Trechos de código para copiar

#### Configuração do Maven Resources Plugin
###### Correção de versionamento do Maven: no arquivo pom.xml, inserir entre `<plugins>` o código abaixo.

```xml
<plugin>
	<groupId>org.apache.maven.plugins</groupId>
	<artifactId>maven-resources-plugin</artifactId>
	<version>3.1.0</version>
</plugin>
```

###### OBS: Após isso, clicar com o botão direito na pasta principal contendo o [boot] > Maven > Udate Projects... > marcar caixa "force Update of Snapshots" > OK.

#### Configurações do banco de dados

```
# Dados de conexão com o banco H2
spring.datasource.url=jdbc:h2:mem:testdb
spring.datasource.username=sa
spring.datasource.password=

# Configuração do cliente web do banco H2
spring.h2.console.enabled=true
spring.h2.console.path=/h2-console

# Configuração para mostrar o SQL no console
spring.jpa.show-sql=true
spring.jpa.properties.hibernate.format_sql=true
```

#### Script SQL

```sql
INSERT INTO tb_department(name) VALUES ('Gestão');
INSERT INTO tb_department(name) VALUES ('Informática');

INSERT INTO tb_user(department_id, name, email) VALUES (1, 'Maria', 'maria@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (1, 'Bob', 'bob@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (2, 'Alex', 'alex@gmail.com');
INSERT INTO tb_user(department_id, name, email) VALUES (2, 'Ana', 'ana@gmail.com');
```

## Anotações Pessoais da Aula

[•](https://#) É possível criar o projeto através do navegador entrando no link: https://start.spring.io/
E depois de gerar o zip, é preciso importar para dentro no STS: abrir a aba 'Maven' e selecionar 'Existing Maven Projects', e em seguida selecionar a pasta do projeto onde tem o src, .mvn e outros... A partir disso já é pra aparecer o arquivo pom.xml (configuration file of Maven), que já é um sinal de sucesso, depois em finish.



- type Maven Project (gerenciador de dependências): app que baixa da internet todas libs dependentes que o projeto precisar.



- O nome do grupo que faz parte dos metadados do projeto, tem o nome de caminho invertido para ser um caminho único, como "com.devsuperior".



- @SpringBootApplication: é uma anotation que vai fazer um pré-processamento na classe antes cde compilar transformando-a em um projeto spring boot. (O Framework Spring faz muito use de 'anotations' pra deixar o código mais limpo).



- ctrl + shift + f = identar no STS.



- ORM (Mapeamento objeto-relacional): Processo de conversão do modelo relacional num modelo de objetos. Portanto, JPA é uma ferramenta ORM que agiliza todo esse processo, para que ele não seja "feito na mão".



- As configurações do BD vão dentro de application.properties na pasta resoucers.



- UserRepository tem como função no projeto, de buscar, salvar, deletar atualizar os dados do usuario com o endpoints.



- Controlador REST: Objeto responsável por receber as requisições do usuários, e repondê-las.



- Mecanismo de injeção de independência: agiliza o uso de isntanciação de composição de componentes.



- findById: retorna um 'optional' (objeto especial do java), e dentro do objeto é que está o que está sendo buscado. 



- Na requisição POST coloca-se o corpo na URL com o objeto que será salvado/inserido.



- Para consultar o BD do projeto: http://localhost:8080/h2-console



- Para consultar os dados da tabela de usuarios: http://localhost:8080/users