# Documentação da FastAPI

## Descrição Geral
Esta é uma API simples construída com FastAPI. Ela contém dois endpoints, um para criar um item (`POST /items/`) e outro para recuperar um item pelo seu ID (`GET /items/{item_id}`).

## Endpoints

### `POST /items/`

#### Descrição
Este endpoint aceita um objeto JSON representando um item e retorna o item recebido. Em uma aplicação real, você provavelmente irá querer inserir os dados do item em um banco de dados aqui.

#### Parâmetros
- `item: Item` (corpo da requisição) - Um objeto JSON representando um item. Deve conter os seguintes atributos:
  - `name: str` - O nome do item.
  - `description: str` - Uma descrição do item.
  - `price: float` - O preço do item.

#### Exemplo de Uso
```
POST /items/
Content-Type: application/json

{
  "name": "Item 1",
  "description": "This is item 1",
  "price": 49.99
}
```

### `GET /items/{item_id}`

#### Descrição
Este endpoint recupera um item pelo seu ID. Se o item não for encontrado, ele retornará um erro HTTP 404.

#### Parâmetros
- `item_id: int` (na URL) - O ID do item a ser recuperado.

#### Exemplo de Uso
```
GET /items/1
```

## Notas Importantes
- A API retorna um erro HTTP 404 se você tentar recuperar um item que não existe.
- Os dados dos itens não estão sendo persistidos em um banco de dados. Portanto, os itens criados com `POST /items/` não estarão disponíveis em `GET /items/{item_id}`.

## Dependências Necessárias
- FastAPI
- Pydantic
- Uvicorn (necessário para rodar a aplicação localmente)

Para instalar todas as dependências, você pode usar o seguinte comando `pip`:

```bash
pip install fastapi pydantic uvicorn
```

Para rodar a aplicação localmente, use o seguinte comando:

```bash
uvicorn main:app --reload
```