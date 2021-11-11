# Validação de entrada de dados no NODEjs
### Processo que verifica a concordância dos dados em relação às requisições da API, lidando com a entrada de dados para que a API consuma apenas os dados necessários para seu funcionamento.

### Porque Validar os Dados?
> A validação de entrada de dados em uma api é um processo importante para uma aplicação estável, este processo pode ser definido como a verificação dos dados das requisições do servidor HTTP, verificando se o usuário, por exemplo, tenha não entregado um dado importante ou até mesmo tenha enviado um dado não requerido pela API, que se não tiver um sistema de validação de dados, pode causar sérios riscos à sua disponibilidade.

## Como garantir que apenas dados válidos sejam repassados para o banco de dados?
> #### Para que apenas dados úteis sejam repassados ao banco de dados é necessário que seja feita uma validação, um processo onde apenas os dados úteis sejam pegos da requisição e o restante seja ignorado. E para que isso seja realizado, deve-se seguir uma das formas a seguir.

## Como realizar uma validação de dados
- Manualmente
- Block try/catch
- Status HTTP
- Bibliotecas
### Manualmente
Na verificação manual o desenvolvedor deve fazer uso de estruturas de decisão para validar o tipo de dado, como o if/else.
```javascript 
if (...) {
...
} else { 
...
}
```

### Try/Catch
O Try/Catch é uma estrutura que pode ser usada para lidar com erros, funcionando como um if/else, porém mais voltado para a verificação de erros.
```javascript
try {
 // código a ser feito
} catch(erro){
// código para caso dê erro
}
```

### Status HTTP
É um código que serve para indicar ao cliente sobre o status do servidor após o envio dos dados, no contexto de validação de dados. Existem tipos de códigos de três algarismos para status HTTP, cada um tem sua particularidade. Os códigos que começam com "2", como 200, indicam que uma resposta "ok" do servidor, não houve erros observados, os códigos que se iniciam com o algarismo "4", como 400, demonstram que houve algum erro por parte do cliente, já os códigos que se começam por "5", como 500, indicam que houve alguma falha interna no servidor.
### Bibliotecas
É uma das maneiras mais práticas de tratar validações de dados, geralmente proporcionando ao desenvolvedor diversas funções já prontas para que o seu workflow seja mais dinâmico e produtivo. Bibliotecas populares a seguir.
- yup
- joi
- express-validator

## Como responder ao usuário em caso de uma entrada incorreta?
Existem diversas maneiras de dizer isso ao usuário, pode-se até juntá-las na solução final, porém a forma que mais recomendo é o uso de uma biblioteca de validação, por exemplo a biblioteca "express-validator".
- Manualmente
```javascript
if (!req.body.email) {
  return res.status(400).json({erro: 'Campo email é obrigatório'})
}
```
- Bibliotecas (usando express-validator)
```javascript
routes.post('/email-express-validator', [
// verifica se é email, se tem mais de 5 caracteres e configura a mensagem caso dê erro
body('email').isEmail().isLength({min: 5}).withMessage('Email deve ser válido')
], (req, res) => {
const errors = validationResult(req)
if (!errors.isEmpty()) {
  return res.status(400).json({erros: errors.array()})
}
res.json({mensagem: 'sucesso'})
}

```

# Autores
Higor Ricardo e Gervásio Gonçalves
Turma: 3° ano Informática

## Referências
- https://www.youtube.com/watch?v=08rRhRL23u4&ab_channel=ProgramandoSolu%C3%A7%C3%B5es
- https://drive.google.com/file/d/1O6uVOwNZDLhektdoOkfYraGCZqrln_TC/view
- https://programandosolucoes.dev.br/2020/11/10/valida-api-express-validator/
