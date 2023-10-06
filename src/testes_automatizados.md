# Testes Automatizados

Testes automatizados fazem parte dos principais conceitos quando falamos de qualidade de software, porém muitas
vezes (como desenvolvedores) não sabemos como trabalhar com os mesmos

### Porque Testar?

Alguns motivos do porque testes são importantes:

- Com os testes podemos identificar falhas antes do software ir para produção
- Podemos evidenciar regras/especificações do domínio
- Garantir que um mesmo erro não tenha um 'reset' após ser eliminado
- Garantir integridade das regras de negócio

### Pirâmide De Testes

Quando nos tratamos sobre testes de software temos um conceito amplamente utilizado conhecido como 'pirâmide de
testes', que nos define níveis de testes e a quantidade em que temos que produzir testes em cada nível. Temos:

- Testes Unitários

**Objetivo:** Tem como objetivo testar a menor unidade possivel dentro do software
**Motivo de falha:** Testes unitários - quase sempre - falham quando a implementação sofre alteração
**Custo (recurso):** Baixo
**Fakers:** Amplamente utilizado

- Testes De Integração

**Objetivo:** Tem como objetivo testar a integração entre os componentes do software
**Motivo de falha:** Testes de integração falham sempre que a forma como os componentes são integrados se alteram
**Custo (recurso):** Mediano
**Fakers:** Amplamente utilizado

- Testes Ponta A Ponta (e2e)

**Objetivo:** Tem como objetivo simular todo o percurso de um cliente (sendo o mesmo uma API, uma pessoa, entre outros
clientes)
**Motivo de falha:** Testes e2e - quase sempre - falham quando a implementação de entrada/saída sofrem alteração
**Custo (recurso):** Alto
**Fakers:** Utilizado somente em serviços terceiros

### Padrões De Descrição De Testes

- Should, When, At

Descreve o comportamento de um teste com uma sintaxe simples e enxuta

exemplo:

```
should return 201 status code when an user introduce a valid payload
```

- Gherkin Syntax

Este é um padrão amplamente utilizado em Desenvolvimento Orientado A Comportamento, é robusto e tem uma ampla conexão
com o domínio do software

exemplo:

```
feature: todo feature
scenario: the user want to register a new todo
given:
   - a valid payload
when:
   - the POST /todo endpoint is called
then:
   - return 201 status code
```

### Exemplos

> Todos os exemplos feitos com NodeJS

- Modelo De Componentes

Para os exemplos vamos utilizar modelos de componentes com as 4 (quatro) operações matemáticas básicas:

```
+-----------+    +-------------+    +----------+    +---------+
| ADICIONAR | => | MULTIPLICAR | => | SUBTRAIR | => | DIVIDIR |
+-----------+    +-------------+    +----------+    +---------+
```

- Teste Unitário

```
```

- Teste De Integração

```
```

- Teste Ponta A Ponta

```
```

### Referências

- [A Piramide De Testes](https://medium.com/creditas-tech/a-pir%C3%A2mide-de-testes-a0faec465cc2)
- [Teste De Software](https://blog.tecnospeed.com.br/teste-de-software/)
- [Piramide De Testes](https://natahouse.com/pt/piramide-de-testes)
- [Practical Test Pyramid](https://martinfowler.com/articles/practical-test-pyramid.html)

