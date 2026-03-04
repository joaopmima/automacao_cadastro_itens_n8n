# automa-o_cadastro_itens_de_consumo-n8n

# Automação Inteligente de Cadastro de Itens

Sistema de automação para cadastro completo de itens a partir de e-mails com anexos em PDF, utilizando extração estruturada de dados com inteligência artificial, validação fiscal de NCM, classificação contábil automatizada e inserção direta em banco de dados.

---

## Sumário

- Sobre o Projeto
- Arquitetura do Fluxo
- Funcionamento
- Regras de Negócio
- Tecnologias Utilizadas
- Tratamento de Erros
- Benefícios
- Evoluções Futuras
- Status

---

## Sobre o Projeto

Este projeto foi desenvolvido para automatizar o processo de cadastro de itens recebidos por e-mail, eliminando atividades manuais, reduzindo falhas operacionais e garantindo padronização das informações cadastradas.

O sistema realiza:

- Leitura automática de e-mails
- Identificação e processamento de anexos em PDF
- Extração estruturada de dados via IA
- Validação de NCM
- Classificação contábil inteligente
- Inserção automática no banco de dados
- Registro em planilha de controle
- Envio de e-mail com resumo do processamento

---

## Arquitetura do Fluxo


Email Trigger
    ↓
Verificação de Anexo
    ↓
Extração de Texto do PDF
    ↓
IA 1 - Extração Estruturada
    ↓
Validação de NCM
    ↓
Consulta Código Padrão (Planilha)
    ↓
IA 2 - Classificação Contábil
    ↓
Inserção no Banco de Dados
    ↓
Registro em Planilha
    ↓
Envio de E-mail com Resumo

---

## Funcionamento

### 1. Monitoramento de E-mail

O sistema monitora automaticamente uma caixa de entrada específica. Ao receber um novo e-mail, o fluxo é iniciado.

### 2. Verificação de Anexo

- Caso não haja anexo, o sistema envia automaticamente um e-mail solicitando o envio do arquivo.
- Caso exista anexo em PDF, o processamento é iniciado.

### 3. Extração de Dados

O texto do PDF é extraído e enviado para a primeira IA, responsável por estruturar os campos necessários ao cadastro, como:

- Descrição do item
- NCM
- Unidade de medida
- Marca
- Código do fornecedor
- Demais campos configurados

### 4. Validação de NCM

O NCM é validado conforme regras fiscais vigentes.

- Se inválido, o fluxo é interrompido e um e-mail de recusa é enviado.
- Se válido, o processamento continua.

### 5. Consulta de Código Padrão

O sistema consulta uma planilha interna para identificar o código padrão da empresa correspondente ao item.

### 6. Classificação Contábil

A segunda IA recebe:

- Dados estruturados do item
- Lista de contas contábeis disponíveis no workflow

Com base nessas informações, retorna a conta contábil mais adequada.

### 7. Persistência de Dados

Após validações e classificações:

- O item é inserido no banco de dados.
- O registro é armazenado em planilha para controle e auditoria.

### 8. Finalização

Após processar todos os itens do anexo, o sistema envia um e-mail com o resumo do cadastro realizado.

---

## Regras de Negócio

- Nenhum item é cadastrado sem NCM válido.
- A classificação contábil é obrigatória.
- Todo item processado é registrado para auditoria.
- O fluxo só é finalizado após o processamento completo dos itens do anexo.
- Em caso de erro crítico, o processo é interrompido e notificado.

---

## Tecnologias Utilizadas

- Ferramenta de automação de workflow
- API de inteligência artificial para extração e classificação
- Processamento de PDF
- Banco de dados relacional
- Planilhas como base auxiliar
- Integração via SMTP e IMAP

---

## Tratamento de Erros

- NCM inválido gera interrupção do fluxo e envio automático de notificação.
- Falhas na extração geram registro em log e alerta.
- Falhas na inserção no banco geram rollback e notificação.
- Ausência de anexo gera solicitação automática ao remetente.
- Erros não tratados são registrados para análise posterior.

---

## Benefícios

- Redução de erros humanos
- Padronização de cadastro
- Validação fiscal automatizada
- Ganho de produtividade
- Escalabilidade do processo
- Rastreabilidade completa do cadastro

---

## Evoluções Futuras

- Integração com validação automática da tabela TIPI atualizada
- Cache de classificações contábeis recorrentes
- Dashboard de monitoramento
- Sistema de logs centralizado
- Versionamento de regras de cadastro
- Transformação em solução interna escalável

---

## Status

Projeto em operação com evolução contínua e melhorias planejadas para aumento de robustez, precisão e desempenho.
