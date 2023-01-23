# FinAPI

FinAPI é uma aplicação web que simula uma conta bancária, onde é possível realizar operações bancárias básicas, como criar uma conta, depositar ou retirar dinheiro, ver o extrato, ver o saldo, atualizar o nome do cliente e excluir a conta. Todas essas operações são feitas através de requisições HTTP para rotas específicas. Essa aplicação foi construída durante o Ignite da Rocketseat como exemplo de aplicação bancária. Ela fornece uma estrutura básica para simular operações bancárias, mas não deve ser usada em ambientes de produção sem implementação de segurança e validações adicionais.

## Rotas

### Criar conta

-   Rota: /account
-   Método: POST
-   Corpo da requisição:
	 - `{
  "cpf": "123.456.789-00",
  "name": "John Doe"
}` 
-   Retorno:
    -   201: conta criada com sucesso
    -   400: cliente já existe

### Ver extrato

-   Rota: /statement
-   Método: GET
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Retorno:
    -   200: extrato do cliente
    -   400: cliente não encontrado

### Depositar

-   Rota: /deposit
-   Método: POST
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Corpo da requisição:
	- `{
  "description": "Salary",
  "amount": 1000
}` 
-   Retorno:
    -   201: depósito realizado com sucesso
    -   400: cliente não encontrado

### Retirar

-   Rota: /withdraw
-   Método: POST
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Corpo da requisição:
	- `{
  "amount": 500
}` 
-   Retorno:
    -   201: retirada realizada com sucesso
    -   400: cliente não encontrado, saldo insuficiente

### Ver extrato por data

-   Rota: /statement/date
-   Método: GET
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Query:
    -   `date: 2021-01-01`
-   Retorno:
    -   200: extrato do cliente filtrado por data
    -   400: cliente não encontrado

### Atualizar nome do cliente

-   Rota: /account
-   Método: PUT
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Corpo da requisição:
	- `{
  "name": "Jane Doe"
}` 
-   Retorno:
    -   201: nome do cliente atualizado com sucesso

### Ver informações da conta

-   Rota: /account
-   Método: GET
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Retorno:
    -   200: informações da conta do cliente
    -   400: cliente não encontrado

### Excluir conta

-   Rota: /account
-   Método: DELETE
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Retorno:
    -   200: conta excluida com sucesso
    -   400: cliente não encontrado

### Ver saldo

-   Rota: /balance
-   Método: GET
-   Cabeçalho da requisição:
    -   `cpf: 123.456.789-00`
-   Retorno:
    -   200: saldo da conta do cliente
    -   400: cliente não encontrado
  
## Como executar

Para executar a aplicação, você precisará ter o Node.js instalado em sua máquina.

1.  Faça o clone deste repositório
2.  Acesse o diretório da aplicação via terminal
3.  Execute o comando `yarn add` para instalar as dependências
4.  Execute o comando `yarn start` para iniciar a aplicação
5.  Utilize algum software para fazer as chamadas HTTP para as rotas listadas acima

Observação: Para testar as rotas, pode ser usado o software "Postman" ou "Insomnia"

## Observações finais

Este é apenas um exemplo de aplicação e não deve ser usado em ambientes de produção sem implementação de segurança e validações adicionais. Também é importante observar que nenhum tipo de persistência de dados esta implementado na aplicação.
