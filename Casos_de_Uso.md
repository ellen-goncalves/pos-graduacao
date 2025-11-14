# CS 01 - Cadastrar curso
## Sumário: 
O usuário administrador deseja cadastrar um curso na plataforma.
## Ator primário: 
Administrador
## Ator secundário:

## Pré condições:
- Autenticar administrador

## Fluxo principal:
1. Administrador deseja cadastrar um curso
2. Administrador clica para cadastrar curso
3. Sistema solicita Título, Descrição, Categoria e Palavras-chave
4. Administrador preenche dados
5. Sistema solicita Docente
6. Administrador busca Docente por Nome
7. Administrador seleciona Docente
8. Sistema solicita cadastro de Módulo
9. Administrador cadastra módulo com Título, Texto, Vídeo-aula e ordem
10. Administrador altera curso para disponível
11. Finalizar fluxo

## Fluxo alternativo: (Item 6)
Caso Administrador não encontre docente:
- Administrador cadastra novo docente
- Retornar ao fluxo em item 7

## Fluxo alternativo: (Item 9)
Caso Administrador não queira cadastrar módulo no momento:
- Sistema não permite alterar curso para indisponível
- Retornar ao fluxo em item 11

## Pós condição:
O curso deve passar a aparecer na busca de cursos do sistema.

## Fluxo de exceção:
“O curso selecionado não poderá ser disponibilizado enquanto não houver módulos cadastrados.”

## Regra de Negócio:
RN01: O curso só pode estar disponível caso possua pelo menos 1 módulo cadastrado.

***

# CS 02 - Iniciar curso
## Sumário: 
O usuário Discente deseja iniciar um curso disponível na plataforma.
## Ator primário: 
Discente
## Ator secundário:

## Pré condições:
- Autenticar Discente
- Cadastrar curso
- Cadastrar módulo
- Buscar curso

## Fluxo principal:
1. Discente deseja iniciar um curso
2. Discente busca um curso na lista
3. Discente seleciona curso
4. Sistema verifica se curso está disponível para início
5. Sistema permite clicar para iniciar curso
6. Discente clica para iniciar curso
7. Finalizar fluxo

## Fluxo alternativo: (Item 2)
Caso Discente não encontre o curso que está buscando:
- O sistema deve exibir cursos da mesma categoria
- Retornar ao fluxo em item 3

## Fluxo alternativo: (Item 2)
Caso Discente não encontre o curso que está buscando e não aceite outra opção:
- Sistema deve exibir um formulário de sugestões
- Discente preenche formulário com a sugestao do curso desejado
- Retornar ao fluxo em item 7

## Fluxo alternativo: (Item 4)
Caso curso não esteja disponível:
- O sistema não deve permitir clicar em iniciar curso
- Discente volta para busca
- Retornar ao fluxo em item 2

## Pós condição:
O status do curso deve ser alterado para "Em Andamento".

## Fluxo de exceção:
“O curso selecionado não está disponível para início no momento.”

## Regra de Negócio:
RN01: O curso só pode estar disponível caso possua pelo menos 1 módulo cadastrado.
