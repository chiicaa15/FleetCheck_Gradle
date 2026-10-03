# FleetCheck – Build Systems Lab

This project is intentionally incomplete. Follow the worksheet in the order given.

Expected final application output:

```
FleetCheck 1.0
Vehicles loaded: 4
Vehicles requiring service: 2
Average mileage: 37000 km
```

Do not copy the solution POM. The objective is to observe how each build change alters the result.


[ERROR] /C:/Users/Francisca Silva/Desktop/Universidade/2º Ano/3º Ano/1º Semestre/QS/Worksheet 4/FleetCheck_Starter/src/main/java/pt/upt/fleetcheck/App.java:[3,39] package com.fasterxml.jackson.core.type does not exist

1- É uma falha melhor porque o código já compila com sucesso, mas um teste deteta que o programa não está a ter o comportamento esperado. Isto mostra um erro na lógica ou no comportamento da aplicação, sendo mais útil do que uma simples falha de compilação.

4-O Shade plugin alterou o JAR padrão ao incluir as dependências da aplicação dentro do próprio JAR. Desta forma, o ficheiro contém não só as classes do projeto, mas também as bibliotecas necessárias para a sua execução, podendo ser executado sem precisar das dependências separadamente.
5-O wrapper removeu a dependência da data e hora atual do ambiente de build. Sem um timestamp fixo, a hora do sistema podia alterar os ficheiros gerados e tornar builds iguais diferentes. Ao definir um output timestamp fixo, a build torna-se reprodutível independentemente de quando ou onde é executada.
7-O SBOM contém componentes que não foram adicionados explicitamente porque são dependências transitivas. Por exemplo, o projeto declara diretamente o `jackson-databind`, mas esta biblioteca depende do `jackson-core` e do `jackson-annotations`. O Maven resolve essas dependências automaticamente e o CycloneDX inclui-as no SBOM porque fazem parte dos componentes necessários para a aplicação.
8.1-App.java:3: error: package com.fasterxml.jackson.core.type does not exist
import com.fasterxml.jackson.core.type.TypeReference;
App.java:4: error: package com.fasterxml.jackson.databind does not exist
import com.fasterxml.jackson.databind.ObjectMapper