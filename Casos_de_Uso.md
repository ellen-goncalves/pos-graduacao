# CS01 Iniciar curso
## Sumário: 
O usuário estudante deseja iniciar um curso disponível na plataforma.
## Ator primário: 
Estudante
## Ator secundário:

## Pré condições:
- Autenticar estudante
- Cadastrar curso
- Cadastrar módulo
- Buscar curso

## Fluxo principal:
1. Estudante deseja iniciar um curso
2. Estudante busca um curso na lista
3. Estudante seleciona curso
4. Sistema verifica se curso está disponível para início
5. Sistema permite clicar para iniciar curso
6. Estudante clica para iniciar curso
7. Finalizar fluxo

## Fluxo alternativo: (Item 2)
Caso estudante não encontre o curso que está buscando:
- O sistema deve exibir cursos da mesma categoria
- Retornar ao fluxo em item 3

## Fluxo alternativo: (Item 2)
Caso estudante não encontre o curso que está buscando e não aceite outra opção:
- Sistema deve exibir um formulário de sugestões
- Estudante preenche formulário com a sugestao do curso desejado
- Retornar ao fluxo em item 7

## Fluxo alternativo: (Item 4)
Caso curso não esteja disponível:
- O sistema não deve permitir clicar em iniciar curso
- Estudante volta para busca
- Retornar ao fluxo em item 2

## Pós condição:
O status do curso deve ser alterado para "Em Andamento".

## Fluxo de exceção:
“O curso selecionado não está disponível para início atualmente.”

## Regra de Negócio:
RN01: O curso só pode estar disponível caso possua pelo menos 1 módulo cadastrado.
