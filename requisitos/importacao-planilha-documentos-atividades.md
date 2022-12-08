# Importação do Excel de Documentos e Atividades

## 1. Descrição

Cadastro de novos documentos ou atividades na Lista de Documentos e Atividades (LD/LA) no ELFA.

### 1.1. Problema

Atualmente, não é possível fazer a operação de Create de Documentos/Atividades (DA) em lote. Assim, o cadastro de novos DA é feito um por vez e é muito moroso, consequentemente.

> Alguns projetos podem chegar a centenas de documentos e atividades

> Imagem aqui

### 1.2. Objetivo

Aumentar a produtividade através do cadastro em lote de novos DA de um Projeto a partir de um arquivo Excel.

### 1.3. Escopo

Deve se aplicar a todo o sistema, no entanto, atualmente o processo de cadastro de DA é feito no módulo Orçamentação

### 1.4. Modelagem de Processos

#### 1.4.1. Processo 1

```mermaid
flowchart LR
    A[Hard edge] -->|Link text| B(Round edge)
    B --> C{Decision}
    C -->|One| D[Result one]
    C -->|Two| E[Result two]
```

## 2. Requisitos

### 2.1. Histórias de Usuários

| Persona _(Eu como...)_ | Ação _(quero/Preciso...)_         | Benefício _(para...)_             |
| ---------------------- | --------------------------------- | --------------------------------- |
| Gerente de Projetos    | Visualizar o avanço do Cronograma | Acompanhar o andamento do Projeto |

### 2.2. Lista de Requisitos

- [ ] lorem ipsum
- [ ] lorem ipsum
- [ ] lorem ipsum . . .

### 2.3. Fluxo do Usuário/Casos de Uso do Usuário

```mermaid
stateDiagram
    direction LR
    [*] --> A
    A --> B
    B --> C
    state B {
      direction LR
      a --> b
    }
    B --> D
```

## 3. Interface

![image](https://user-images.githubusercontent.com/114407461/206535989-8360f611-a22d-45bc-8d1d-08b31ad44005.png)

## 4. Dados

### 4.2. ER

```mermaid
erDiagram
    CUSTOMER }|..|{ DELIVERY-ADDRESS : has
    CUSTOMER ||--o{ ORDER : places
    CUSTOMER ||--o{ INVOICE : "liable for"
    DELIVERY-ADDRESS ||--o{ ORDER : receives
    INVOICE ||--|{ ORDER : covers
    ORDER ||--|{ ORDER-ITEM : includes
    PRODUCT-CATEGORY ||--|{ PRODUCT : contains
    PRODUCT ||--o{ ORDER-ITEM : "ordered in"
```

### 4.1. Campos

#### Tabela Entidade A

| Campo         | Tipo                                                                     | Restrições                                   | Valor default | Not Null |
| ------------- | ------------------------------------------------------------------------ | -------------------------------------------- | ------------- | -------- |
| nome_do_campo | Texto, Número, Data, Arquivo, Seleção única, Seleção Múltipla, Tabela... | Formato de Email, Exatamente 6 caracteres... |               |
