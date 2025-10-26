# Plataforma de Ensino para Pessoas Privadas de Liberdade

## 1. Introdução

O sistema tem como finalidade ofertar cursos de formação técnica e profissionalizante a fim de promover capacitação profissional e contribuir para ressocialização de pessoas privadas de liberdade.

## 2. Requisitos Funcionais (RF)
Este documento tem como objetivo descrever de forma detalhada os requisitos funcionais e não funcionais do sistema, bem como suas restrições, regras de negócio e matriz de rastreabilidade.

### RF01 - Cadastro de Curso
O sistema deve permitir CRUD de cursos (criar, visualizar, editar e excluir).

#### Campos
- Título: String;
- Descrição: String;
- Categoria: Enum; (1)
- Duração: Numérico; 2
- Ativo: Booleano; 3
- Data de inclusão: Data (XX/XX/XXXX) 4
- Palavras-chaves: String 5
- Docente: String 6 
- Módulo: 7


#### Regra e observações do preenchimento dos campos:

1. Categoria será um campo de seleção com todas as categorias previamente criadas no sistema. 
2. Duração deve representar a soma da duração de tempo das vídeo-aulas de cada módulo. Não pode ser valor negativo.
3. Quando o campo Ativo estiver em Falso, não deve ser possível acessar os módulos do curso nem alterar o campo Concluído dos módulos para Verdadeiro. Ademais, o campo Ativo só poderá ser verdadeiro se houver pelo menos 1 módulo cadastrado.
4. A data de inclusão deve ser salva automaticamente obtendo a data e hora no fuso BRT no momento do cadastro de um novo curso e não poderá ser alterada.
5. O campo Palavras-Chave deve permitir incluir palavras e termos para facilitar a busca.
6. O campo Docente será um seletor com a lista de todos os docentes cadastrados em cadastro dedicado. A exibição do selector conterá Nome, E-mail e Foto de Docentes previamente cadastrados ordenados alfabeticamente pelo nome. O cadastro de Docente está descrito no RF02.
7. O campo Módulo será manipulado por um cadastro dedicado descrito no RF03.

#### Alteração:
Será realizado somente por um funcionário com o nível de acesso que permita essa modificação. Vale salientar que em todos os casos deve ser mantido os históricos dos registros, contendo quem realizou a operação juntamente com o que foi realizado, com data e hora. O campo Data de Inclusão não poderá ser modificado.

#### Exclusão:
Não será realizado a exclusão teremos um campo com o nome Ativo onde o mesmo poderá ser verdadeiro ou falso. Vale salientar que em todos os casos deve ser mantido os históricos dos registros.

#### Pesquisa
Será permitido buscar o curso por Título, Descrição, Docente, Categoria e Ativo.

#### Protótipo

<img width="1918" height="1005" alt="curso" src="https://github.com/user-attachments/assets/29093624-73b6-4def-b69e-3314c86c4564" />

### RF02 - Cadastro de Docente
O sistema deve permitir CRUD de docentes (criar, visualizar, editar e excluir).

#### Campos
- Nome: String; (1)
- Descrição: String; (1)
- Foto: String; (2)
- E-mail: String (xxxxxx@xxx.xx); (1, 3)
- Ativo: Booleano

#### Regra e observações do preenchimento dos campos:

1. Os campos Nome, Descrição e e-mail são campos obrigatórios
2. As imagens inseridas no campo Foto deverão ser hospedadas no serviço de armazenamento em nuvem Cloudinary. O sistema armazenará apenas a URL pública retornada pela API do Cloudinary.
3. O campo E-mail deve ter verificação para preenchimento no formato adequado de e-mail (ex.: xxxxxx@xxx.xx).

#### Alteração:
Será realizado somente por um funcionário com o nível de acesso que permita essa modificação. Vale salientar que em todos os casos deve ser mantido os históricos dos registros, contendo quem realizou a operação juntamente com o que foi realizado, com data e hora.

#### Exclusão:
Não será realizada a exclusão teremos um campo com o nome Ativo onde o valor pode ser verdadeiro ou falso, vale salientar que em todos os casos deve ser mantido os históricos dos registros.

#### Pesquisa: 
Será permitido buscar o Docente por Nome, Descrição, e-mail e cursos relacionados.

#### Protótipo

<img width="1901" height="718" alt="docente" src="https://github.com/user-attachments/assets/0e416b99-8626-422c-a642-4cd9d0ab3b61" />


### RF03 - Cadastro de Módulo
O sistema deve permitir CRUD de Módulos (criar, visualizar, editar e excluir).

#### Campos
- Título: String;
- Vídeo-aula: String; (1, 2)
- Texto: String; (1)
- Ordem: Int; (3)
- Pergunta: String; (1, 4)
- Resposta: String; (1, 4)
- Ativo: Booleano;

#### Regra e observações do preenchimento dos campos:

1. Os campos Vídeo-aula, Texto, Pergunta e Resposta são opcionais, mas pelo menos 1 deles deve ser preenchido. Os campos Título e Ordem são campos obrigatórios
2. O vídeo inserido no campo Vídeo-aula deverá ser hospedado no serviço de armazenamento em nuvem Cloudinary. O sistema armazenará apenas a URL pública retornada pela API do Cloudinary.
3. O campo Ordem deve ser um valor único, preenchido automaticamente em sequência pelo sistema, mas pode ser alterado pelo usuário. Deve ter verificação impedindo que módulos compartilhem o mesmo valor nesse campo.
4. Os campos Pergunta e Resposta são dependentes e deve haver uma validação para que sejam quando um deles for preenchido, o outro precisa também ser.

#### Alteração:
Será realizado somente por um funcionário com o nível de acesso que permita essa modificação. Vale salientar que em todos os casos deve ser mantido os históricos dos registros, contendo quem realizou a operação juntamente com o que foi realizado, com data e hora.
#### Exclusão:
Não será realizada a exclusão teremos um campo com o nome Ativo onde o valor pode ser verdadeiro ou falso, vale salientar que em todos os casos deve ser mantido os históricos dos registros.
#### Pesquisa: 
Será permitido buscar pelo Título.

#### Visualização: 
Será possível visualizar os módulos nos cursos relacionados.

#### Protótipo

<img width="1899" height="1080" alt="modulo" src="https://github.com/user-attachments/assets/40813d7f-f451-4283-9e53-483784bfe0f7" />


### 2.2 Requisitos Não Funcionais (RNF)
| ID | Tipo | Descrição |
|------|----|-----------------|
| RNF01 | Requisito Legal - Segurança | Os computadores utilizados não deverão possuir acesso a internet. |
| RNF02 | Requisito de Produto – Confiabilidade | Deve existir um mecanismo de backup diário automático de todos os dados da plataforma. |
| RNF03 | Requisito de Facilidade de Uso - Acessibilidade | Deve seguir as diretrizes WCAG 2.1 para garantir acessibilidade. |

---
