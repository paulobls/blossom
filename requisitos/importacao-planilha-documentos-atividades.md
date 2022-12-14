# Importação do Excel de Documentos e Atividades

## 1. Descrição

Cadastro de novos documentos ou atividades na Lista de Documentos e Atividades (LD/LA) no ELFA.

### 1.1. Problema

Atualmente, não é possível fazer a operação de Create de Documentos/Atividades (DA) em lote. Assim, o cadastro de novos DA é feito um por vez e é muito moroso, consequentemente.

- É possível cadastrar mais de um documento por vez, mas a funcionalidade não atende muito bem a demanda pois:
  - São criados Documentos ou Atividades do mesmo tipo (e não possível alterar o tipo depois da criação)
  - Os demais campos (ex: títulos) devem ser preenchidos um por um

### 1.2. Objetivo

Aumentar a produtividade através do cadastro em lote de novos DA de um Projeto a partir de um arquivo Excel.

### 1.3. Escopo

Deve se aplicar a todo o sistema, no entanto, atualmente o processo de cadastro de DA é feito no módulo Orçamentação

### 1.4. Modelagem de Processos

#### 1.4.1. Processo Geral de Orçamentação

```mermaid
graph TB
    A("Solicitação de OSE") ---> B
    B{"Precisa de FCE?"} --->|Sim| C
    C[["Fase de Conhecimento de Escopo"]]---> D
    B --->|Não| D
    D["Cadastrar OS [1]"] ---> E
    E["Cadastrar Escopo [2]"] ---> F
    F["Cadastrar Entregáveis [3]"] ---> G
    G["Revisar Orçamento"] ---> H
    H["Elaborar Cronograma Macro"] ---> I
    I["Enviar Orçamento para o Cliente"] ---> J
    J{"Aprovado pelo Cliente"?} --->|Sim| K
    J --->|Não| D
    K["Confirmar Orçamento no ELFA"]
```

> ELFA/Orçamentação/...
>
> [1] OS - Dados de entrada
>
> [2] ORM/ORM - Escopo
>
> [3] ORM/ORM - Lista Docs / Atividades

## 2. Requisitos

### 2.1. Histórias de Usuários

| Persona _(Eu como...)_ | Ação _(quero/preciso...)_ | Benefício _(para...)_ |
| ---------------------- | ------------------------- | --------------------- |

### 2.2. Lista de Requisitos

- [ ] Cadastrar novos Documentos/Atividades a partir de uma planilha
- [ ] lorem ipsum
- [ ] lorem ipsum . . .

## 3. Dados

### 3.1. ER

```mermaid
erDiagram
    CUSTOMER }|..|{ DELIVERY-ADDRESS : "has"
    CUSTOMER ||--o{ ORDER : "places"
    CUSTOMER ||--o{ INVOICE : "liable for"
    DELIVERY-ADDRESS ||--o{ ORDER : "receives"
    INVOICE ||--|{ ORDER : "covers"
    ORDER ||--|{ ORDER-ITEM : "includes"
    PRODUCT-CATEGORY ||--|{ PRODUCT : "contains"
    PRODUCT ||--o{ ORDER-ITEM : "ordered in"
```

### 3.2. Campos

#### 3.2.1. Tabela Entidade A

| Campo         | Tipo                                                                     | Restrições                                   | Valor default | Not Null |
| ------------- | ------------------------------------------------------------------------ | -------------------------------------------- | ------------- | -------- |
| nome_do_campo | Texto, Número, Data, Arquivo, Seleção única, Seleção Múltipla, Tabela... | Formato de Email, Exatamente 6 caracteres... |               |

## 4. 5 Referências

[BL0000-GP-PRC-0004 - Orçamentação](https://blossomconsultoria.sharepoint.com/:w:/r/sites/SGQ2/Documentos%20Compartilhados/01_Procedimentos/08_Gerenciamento%20de%20Projeto/BL0000-GP-PRC-0004%20-%20Or%C3%A7amenta%C3%A7%C3%A3o%20Rev.00.docx?d=w664883832c8e487881bd014687382702&csf=1&web=1&e=CYyQhH)
