# Prova Técnica QA Pleno - API Biblioteca Digital

Este repositório contém os artefatos da prova técnica para Analista de Qualidade Pleno, com foco na API Biblioteca Digital e na Controller Books.

## 1. Objetivo

Este projeto contém a estratégia, planejamento, execução e automação dos testes da API Biblioteca Digital, com foco na Controller Books.

A automação foi implementada utilizando Postman, com scripts JavaScript em cada request para validar status code, contrato de resposta, campos obrigatórios, cenários negativos, integração entre endpoints e comportamento de performance básica.

## 2. Estrutura do Projeto

* `01-estrategia-testes`: documentos de análise, estratégia e planejamento
* `02-plano-testes`: planilha com casos de teste estruturados
* `03-postman`: Collection Postman e Environment
* `04-automacao`: README com instruções de execução via Postman/Newman
* `05-evidencias`: evidências em PNG dos testes executados
* `06-relatorio-bugs`: relatório de bugs e ressalvas
* `07-respostas-situacionais`: respostas técnicas e situacionais

## 3. Ferramentas utilizadas

* Postman
* JavaScript nos scripts de Post-response
* Newman para execução via linha de comando

## 4. Arquivos necessários

Os arquivos exportados do Postman estão na pasta `03-postman`:

* `Biblioteca Digital - Books API.postman_collection.json`
* `BibliotecaDigital_ENV.postman_environment.json`

## 5. Como executar pelo Postman

1. Abrir o Postman.
2. Importar a collection:

   * `Biblioteca Digital - Books API.postman_collection.json`
3. Importar o environment:

   * `BibliotecaDigital_ENV.postman_environment.json`
4. Selecionar o environment `BibliotecaDigital_ENV`.
5. Abrir a collection `Biblioteca Digital - Books API`.
6. Executar as requests individualmente ou utilizar a opção `Run Collection`.

## 6. Como executar via Newman

Para executar via terminal, é necessário ter Node.js e Newman instalados.

Instalação do Newman:

```bash
npm install -g newman
```

Execução da collection:

```bash
newman run "03-postman/Biblioteca Digital - Books API.postman_collection.json" -e "03-postman/BibliotecaDigital_ENV.postman_environment.json"
```

## 7. Escopo automatizado

Foram automatizados 19 casos de teste:

* CT-001 a CT-003: consultas de livros
* CT-004 a CT-009: criação, atualização, exclusão e persistência
* CT-010: validação de schema/contrato do objeto Book
* CT-011: consulta com ID negativo
* CT-012 a CT-015: payload incompleto, pageCount negativo, script e SQL Injection no campo title
* CT-016: publishDate inválido
* CT-017: tempo de resposta da listagem
* CT-018: integração Books x Authors
* CT-019: integração Books x CoverPhotos

## 8. Observações importantes

Durante a execução dos testes, foi observado que a FakeRESTApi retorna sucesso para operações POST, PUT e DELETE, porém não persiste as alterações em consultas posteriores via GET.

Também foram identificadas aceitações de entradas de borda, como payload incompleto, pageCount negativo, script e tentativa de SQL Injection em campos textuais.

Esses comportamentos foram registrados como ressalvas no plano de testes e no relatório de bugs/ressalvas.

## 9. Resultado geral

Foram planejados e executados 19 casos de teste para a Controller Books.

Os testes foram executados com sucesso no Postman.

Não foram encontrados bugs críticos impeditivos. Foram registradas ressalvas relacionadas à persistência da FakeRESTApi e à ausência de validações mais rígidas para alguns campos.
