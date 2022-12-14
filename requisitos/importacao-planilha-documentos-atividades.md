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

#### 1.4.1. Processo Geral

```mermaid
graph TB
    A(Solicitação de OSE) ---> B
    B{Precisa de FCE?} --"Sim"--> C
    C[[Fase de Conhecimento de Escopo]]---> D
    B --"Não"--> D
    D[Cadastrar OS] ---> E
    E[Cadastrar Escopo] ---> F
    F[Cadastrar Entregáveis] ---> G
    G[Revisar Orçamento] ---> H
    H[Elaborar Cronograma Macro] ---> I
    I[Enviar Orçamento para o Cliente] ---> J
    J{Aprovado pelo Cliente?} --"Sim"--> K
    J --"Não"--> D
    K[Confirmar Orçamento no ELFA]
```

## 2. Requisitos

### 2.1. Histórias de Usuários

| Persona _(Eu como...)_ | Ação _(quero/preciso...)_ | Benefício _(para...)_ |
| ---------------------- | ------------------------- | --------------------- |

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
    CUSTOMER }|..|{ DELIVERY-ADDRESS : "has"
    CUSTOMER ||--o{ ORDER : "places"
    CUSTOMER ||--o{ INVOICE : "liable for"
    DELIVERY-ADDRESS ||--o{ ORDER : "receives"
    INVOICE ||--|{ ORDER : "covers"
    ORDER ||--|{ ORDER-ITEM : "includes"
    PRODUCT-CATEGORY ||--|{ PRODUCT : "contains"
    PRODUCT ||--o{ ORDER-ITEM : "ordered in"
```

### 4.1. Campos

#### Tabela Entidade A

| Campo         | Tipo                                                                     | Restrições                                   | Valor default | Not Null |
| ------------- | ------------------------------------------------------------------------ | -------------------------------------------- | ------------- | -------- |
| nome_do_campo | Texto, Número, Data, Arquivo, Seleção única, Seleção Múltipla, Tabela... | Formato de Email, Exatamente 6 caracteres... |               |

## 5 Referências

[BL0000-GP-PRC-0004 - Orçamentação](https://blossomconsultoria.sharepoint.com/:w:/r/sites/SGQ2/Documentos%20Compartilhados/01_Procedimentos/08_Gerenciamento%20de%20Projeto/BL0000-GP-PRC-0004%20-%20Or%C3%A7amenta%C3%A7%C3%A3o%20Rev.00.docx?d=w664883832c8e487881bd014687382702&csf=1&web=1&e=CYyQhH)
