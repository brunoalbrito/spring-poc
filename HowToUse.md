1. Após a instalação de ambos os programas vamos iniciar a configuração do Eclipse para permitir que as bibliotecas Spring sejam baixadas no projeto. Primeiro é necessário baixar um arquivo de configuração que define alguns parâmetros de download dos pacotes utilizando o Artifactory do banco. Abra o seu Git Bash siga até a pasta de documentos e execute os seguintes comandos:

```bash
mkdir kit-dev

cd kit-dev

git clone -b settings-eclipse 

``` 
 
2. Agora abra o Eclise Jee e siga navegando até o seguinte local:

> Windows > Preferences > Maven > User Settings > Browse... > Vá até a pasta kit-dev e escolha o arquivo settings.xml

3. O próximo passo é a criação de um projeto Maven, para isso siga as instruções:

> File > Others > Maven > Maven Project 

Check a opção **Create a simple project(skip archetype selection)** > Next 

Preencha os seguintes campos:

**Artifact**
```
Group Id: com.itau
Artifact Id: webapirestful
Name: webapirestful
```
**Parent Project**
```
Group Id: org.springframework.boot
Artifact Id: spring-boot-starter-parent
Version: 2.0.5.RELEASE
```

Agora selecione **Finish**
Pronto, nosso projeto está criado, agora vamos adicionar todas as depêndencias ao pom.xml. Para isso, clique sob ele com o botão direito, selecione Open With > Generic Text Editor. Abaixo da tag <name> cpie e cole o trecho a baixo: 

```xml
<dependencies>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-web</artifactId>
	</dependency>
	<dependency>
		<groupId>org.springframework.boot</groupId>
		<artifactId>spring-boot-starter-test</artifactId>
		<scope>test</scope>
	</dependency>
	<dependency>
		<groupId>com.jayway.jsonpath</groupId>
		<artifactId>json-path</artifactId>
		<scope>test</scope>
	</dependency>
</dependencies>

<properties>
	<java.version>1.8</java.version>
</properties>


<build>
	<plugins>
		<plugin>
			<groupId>org.springframework.boot</groupId>
			<artifactId>spring-boot-maven-plugin</artifactId>
		</plugin>
	</plugins>
</build>
```
Ctrl + S para Salvar

Agora vamos criar nossos pacotes básicos:
Clique com o botão direito sob *src/main/java* e crie 3 novos pacotes:
```
models
controllers
application
```
Novamento com o botão direito, porém sob application, selectione a opção > New > Class
```
Name: Application > Finish
```

Copie e cole o código a baixo:

```java
package application;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class Application {

    public static void main(String[] args) {
        SpringApplication.run(Application.class, args);
    }
}
```

Sob o pacote model crie uma nova classe:
```
Name: User > Finish
```

Copie e cole o código a baixo:

```java
package model;

public class User {

    private final long id;
    private final String firstName;
    private final String lastName;

    public User(long id, String firstName, String lastName) {
        this.id = id;
        this.firstName = firstName;
        this.lastName = lastName;
    }

    public long getId() {
        return id;
    }

	public String getFirstName() {
		return firstName;
	}

	public String getLastName() {
		return lastName;
	}
}
```


Sob o pacote controller crie também uma nova classe:
```
Name: UserController > Finish
```

Copie e cole o código a baixo:

```java
package controller;

import java.util.concurrent.atomic.AtomicLong;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

import model.User;

@RestController
public class UserController {

    private static final String _firstName = "Nome%s!";
    private static final String _lastName = "Sobrenome%s";
    private final AtomicLong counter = new AtomicLong();

    @RequestMapping("/users")
    public User getUser(@RequestParam(value="name", defaultValue="user") String firstName, String lastName) {
        return new User(counter.incrementAndGet(),
                            String.format(_firstName, counter), String.format(_lastName, counter));
    }
}

``` 
Não se proocupe com os erros de importação por enquanto, agora vamos resolver isso


Clique com o botão direito sob o projeto e selecione a opção **Run As** **>** **Maven Install**, espere receber a seguinte mensagem no console:

```bash
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time: 0.000 s
[INFO] Finished at: 2018-12-06T01:12:46-02:00
[INFO] ------------------------------------------------------------------------
```
Agora é a hora de executarmos nosso projeto, Clique com o botão direito sob o projeto e selecione a opção **Run As** **>** **Java Application**, selectione *Application* e espere a mensagem no console:
```

  .   ____          _            __ _ _
 /\\ / ___'_ __ _ _(_)_ __  __ _ \ \ \ \
( ( )\___ | '_ | '_| | '_ \/ _` | \ \ \ \
 \\/  ___)| |_)| | | | | || (_| |  ) ) ) )
  '  |____| .__|_| |_|_| |_\__, | / / / /
 =========|_|==============|___/=/_/_/_/
 :: Spring Boot ::        (v2.0.5.RELEASE)
 .
 .
 .
 Varias Coisas
 .
 .
 .
2018-12-06 01:15:03.961  INFO 22112 --- [           main] o.s.b.w.embedded.tomcat.TomcatWebServer  : Tomcat started on port(s): 8080 (http) with context path ''
2018-12-06 01:15:03.967  INFO 22112 --- [           main] application.Application                       : Started Application in 2.898 seconds (JVM running for 3.292)
```

Abra o navegador e chame o seguinte caminho:

[](http://localhost:8080/users)

Espere receber o retorno:

```json
{"id":1,"firstName":"Nome1!","lastName":"Sobrenome1"}
```


Sucesso!!! Você acaba de criar sua primeira API RestFul no Sprint Boot.