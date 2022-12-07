# Introdução

Esse documento especifica em detalhes como o Sistema ELFA deve tratar os permissionamentos de seus usuários nos diversos módulos e funções do sistema.

Escopo: Aplicável em todos os módulos do sistema já construídos e também nos módulos a serem desenvolvidos.

# Descrição Geral

Na versão atual do sistema, temos um cadastro de perfis de usuários. Através do código fonte, os módulos e as funcionalidades de cada módulo são habilitados para o usuário considerando o perfil que foi atribuído a ele (cadastro de usuário). Assim, sempre que é necessário um novo perfil de acesso, o analista ELFA deve ser contactado para alterar o programa e considerar esse novo perfil.

A especificação descrita nesse documento indica o caminho correto para mantermos uma rotina simples e rápida para as atribuições ou restrições de permissões de acesso.

## Perspectiva

Liberação no menu de cada módulo apenas das funcionalidades autorizadas para o funcionário sem a intervenção do Analista de Sistemas.

# Requisitos Funcionais

## Diagrama de Caso de Uso

### Primeira Etapa

O Suporte do ELFA, faz o cadastro os módulos do sistema e suas funcionalidades, criando uma estrutura de dados similar a ilustrada abaixo:

A mesma funcionalidade pode constar em módulos diferentes dando mais flexibilidade ao sistema e facilitando a navegação. Assim, uma consulta de “comentários de cliente” pode constar no menu do GED e no menu da Qualidade, mas quem faz essa configuração é o administrador do sistema e não o analista ELFA.

Caso não haja

Há também a possibilidade de incluir várias funcionalidades em um agrupamento do menu, para termos submenus como o exemplo abaixo retirado do módulo GED do ELFA:

A função de cadastro de módulo do sistema, deve prever uma descrição completa do módulo, seus objetivos, escopo, etc. Uma descrição resumida também é necessária pensando em sua exibição em tela e no espaço que ocupará e a ordem em que deve aparecer no Menu

O cadastro deve conter uma indicação da situação do módulo como:
- Ativo
- Em Manutenção
- Em Desenvolvimento

Cada módulo cadastrado terá todas as funcionalidades que o compõe, assim, poderemos ter funcionalidade diversas e se for o caso, repetida nos diversos módulos com a finalidade de facilitar a navegação do sistema das pessoas autorizadas.

Para cada funcionalidade o sistema deve prever a DLL (ou rotina, programa, etc..) que será executada ao se escolher essa opção do menu.

Deve ser previsto também que as funcionalidades do sistema podem ser agrupadas fazendo parte de um submenu do módulo.
Exemplo da organização dos dados:

### Segunda Etapa

O Elfa possui uma tabela com o perfil de acessos dos usuários como mostrado a seguir:

Porém, devemos prever um relacionamento da tabela de perfil de acesso com as funcionalidades do sistema.
Assim, a estrutura de dados ficaria dessa forma:

> Inserir ER
> 
# Requisitos de Segurança
