# Resumo - Apostila

## Capítulo 4 - Modelagem de dados usando o Modelo-Entidade Relacionamento (MER)

MER - modelo de dados conceitual de alto-nível

* Entidades:
  * `Entidade`: unidade básica que o MER representa
  * `Atributo`: propriedades de uma entidade
    * **simples**/atômico ou **composto**
    * **univalorado** ou **multivalorado**
    * **derivado** (*ex*: dt_nasc e idade)
    * **nullable**
  * `Tipo de identidade`: conjunto de entidades com os mesmos atributos;
  * `Atributo-chave`;

* `Relacionamento`:
  * Relacionamento recursivo;
  * `Grau de um tipo de relacionamento`:
    * 2 - **binário**;
    * 3 - **ternário**;
    * **1 ternário x 3 binários**.
  * `Razão de cardinalidade`:
    * **1:1**
    * **1:N**
    * **M:N**
  * Restrições:
    * `Restrição de participação`: total ou parcial (dependência existencial);
    * `Restrição estrutural`: min e max
      * Se `min >= 0`, parcial
      * Senão, se `min > 0`, total
  * Atributos em tipos de relacionamento:
    * Em 1:1, pode ser colocado em qualquer lado;
    * Em 1:N, pode ser colocado do lano **N**.
  * `Entidade fraca`:
    * **Não** possui atributo-chave;
    * `Relacionamento de identificação`: entre a *entidade fraca* e o     **proprietário da identificação**
    * **Sempre** possui restrição de *participação total*
    * Possui uma **chave parcial**.

* Diagrama Entidade-Relacionamento (DER)

## Capítulo 5 - O Modelo de Dados Relacional

### 5.1 Conceitos do Modelo Relacional

Modelo de dados relacional - dados são uma coleção de relações

Uma relação pode ser vista como uma tabela de valores

* Colunas - atributos
* Linha - valores

Terminologia:

* Tabela => relação
* Linha => tupla
* Coluna => atributo
* Tipo de dado => domínio

`Grau de uma relação` = número de atributos da relação

`Intenção da relação` = esquema `R`

`Extensão da relação` = instância `r` do esquema `R`

#### 5.1.2 Atributos-chaves de uma relação

Por definição de conjunto, todos os elementos são distintos. Sendo assim, todas as tuplas de uma relação também são distintas.

* `Super-chave` = subconjunto de atributos de uma relação esquema R com a propriedade de que nenhuma outra tupla de uma relação r de R tenha a mesma combinação
* `Chave` = super-chave mínima
* `Chave-candidatas` = conjunto de chaves
* `Chave-primária` = chave-candidata designada com melhor atributo(s) que identifica unicamente cada tupla

#### 5.1.3 Esquema de Bases de Dados Relacionais e Restrições de Integridade

* `Esquema` da base dados relacional `S` = conjunto de relações esquemas `(R_1, R_2, ..., R_m)`
* `RI` = Conjunto de restrições de integridade
* `Instância` da base de dados relacional `DB` de `S` = conjunto de instâncias das relações do esquema `S` que satisfazem `RI`

`Base de dados relacional` = refere-se implicitamente ao esquema + instâncias

`Restrições de Chave (individual)` = os valores das chaves-candidatas devem ser únicos para todas as tuplas de quaisquer instâncias da relação esquema

`Restrição de integridade de entidade (individual)` = valor da chave primária NÃO pode ser nulo.

`Restrição de integridade referencial (entre duas relações)` = uma tupla de uma relação deve se referir à outra tupla existente de outra relação
Chave-estrangeira (CE) = formalização de referência para a restrição de integridade referencial

Restrições de integridade semânticas

#### 5.1.4 Operações de Atualizações sobre Relações

* Inserção = inserir novas tuplas à relação
* Remoção = remove tuplas da relação
* Modificação = modifica valores de alguns atributos.

Quando aplicadas, devem ser verificadas as `RIs`.

## Capítulo 6 - Mapeamento do MER para o Modelo de Dados Relacional + Slides sobre MER-X

`MER` = Modelo Entidade-Relacionamento

`MER-X` = Modelo Entidade-Relacionamento Extendido, que adiciona as abstrações de `agregação` e `generalização` / `especialização`

`DER` = Diagrama Entidade-Relacionamento

Passo a passo:

1. Mapeamento de entidade regular
   * Para cada entidade, crie uma relação (tabela);
   * Adicione *atributos simples*;
   * Adicione as partes simples dos *compostos*;
   * Adicione *atributo-chave* como *chave-primária*.
2. Mapeamento de entidade fraca
   * Para cada entidade fraca, cria uma relação (tabela);
   * Adicione *atributos simples*;
   * Adicione as partes simples dos *compostos*;
   * Adicione a chave-primária do *proprietário de identificação* como *chave-estrangeira*;
   * A *chave-primária da relação* é a combinação da *chave-estrangeira* com a *chave-parcial*.
3. Mapeamento de relacionamentos binários 1:1
   * Para cada relacionamento binário 1:1, identifique entidades S e T que participam do relacionamento;
   * Escolha uma delas (S no exemplo) e adicione como *chave-estrangeira* a chave-primária da outra (é melhor escolher o tipo de entidade com participação total);
   * Adicione os *atributos simples* do tipo de relacionamento à S.
4. Mapeamento de relacionamentos binários 1:N
   * Para cada relacionamento binário 1:N, identificar a *relação S que participa do lado N* do relacionamento;
   * Adicione como *chave-estrangeira de S* a *chave-primária* do outro tipo de entidade;
   * Adicione os *atributos simples* do tipo de relacionamento à S.
5. Mapeamento de relacionamentos binários M:N
   * Para cada relacionamento binário M:N, adicione uma nova relação S;
   * Adicione como *chaves-estrangeiras* as *chaves-primárias dos dois tipos de entidades*. A *chave-primária de S* é a combinação dessas chaves-estrangeiras;
   * Adicione os *atributos simples* do tipo de relacionamento à S.
6. Mapeamento de atributo multivalorado
   * Para cada atributo multivalorado A, crie uma nova relação R.
   * Adicione o atributo A;
   * Adicione como *chave-estrangeira* a chave-primária da relação que possui A como atributo;
   * Caso A seja *multivalorado e composto*, inclua os *atributos simples* que o compõe.
7. Mapeamento de relacionamentos N-ário
   * Para cada relacionamento N-ário, adicione uma nova relação S;
   * Adicione como *chaves-estrangeiras* as *chaves-primárias de todos os tipos de entidades* participantes. A *chave-primária de S* é a combinação dessas chaves-estrangeiras;
   * Adicione os *atributos simples* do tipo de relacionamento à S.
   * Adicione as partes simples dos *compostos*;
8. Mapeamento de generalização/especialização
   1. Relações múltiplas para classes e subclasses
      * Crie uma relação para a *superclasse*.
      * Para cada *subclasse*, crie uma relação usando a *chave-primária* da superclasse como chave-primária.
      * **Funciona para qualquer especialização** (total ou parcial, disjuntas ou sobrepostas).
   2. Relações múltiplas para subclasses
      * Para cada *subclasse*, crie uma relação **com todos os atributos da superclasse**, usando a *chave-primária* da superclasse como chave-primária.
      * **Funciona somente para especializações com subclasses totais** (total ou parcial, disjuntas ou sobrepostas).
   3. Relação única com um atributo tipo
      * Crie uma relação única L;
      * Adicione todos os atributos da superclasse e de todas as subclasses;
      * Adicione um atributo tipo, que indica à qual subclasse cada tupla pertence;
      * **Funciona especializações disjuntas** (mas pode ter muitos valores null).
   4. Relação única com múltiplos atributo tipo
      * Crie uma relação única L;
      * Adicione todos os atributos da superclasse e de todas as subclasses;
      * Adicione um atributo booleano para cada subclasse, cuja função é indicar se a tupla pertence ou não a cada subclasse.
      * **Funciona especializações sobreponíveis** (também funciona para disjuntas).
9. Categoria (union type)
10. Agregações

### Agregação

Uma abstração que permite construir objetos compostos a partir de outros objetos.

No MER-X, a agregação ocorre de duas maneiras:

* Agregando atributos à tipos de entidades e tipos de relacionamentos;
* Combinar tipos de entidades relacionados por tipos de relacionamentos e compor um **tipo de entidade agregada**.

#### 1ª forma de agregação

Os tipos de entidades e relacionamentos são agregações de atributos.

#### 2ª forma de agregação

Há casos em que adicionar tipos de entidades ou tipos de relacionamentos é incorreto, pois não atende aos requisitos. Por exemplo: não é possível relacionar dois tipos de relacionamentos.

Neste caso, podemos criar uma agregação de tipos de entidades e relacionamentos, criando uma abstração de alto nível (ou criar uma entidade fraca).

### Generalização / Especialização

Os tipos de entidades representam `classes`. Podemos pensar numa **hierarquia de classes**.

Nesta *hierarquia de classes* há:

* `Superclasses`: classe base ou classe pai;
* `Subclasses`: classes derivadas ou filhas.

`Sobreponível` ou `disjunto`.

A restrição de participação de uma superclasse em relação às suas subclasses pode ser `parcial` ou `total`.

Pode ocorrer `herança múltipla`.

## Capítulo 7 - Linguagens Formais de Consulta

A **álgebra relacional** contempla um conjunto de operações que permitem especificar consultas sob relações.

As operações são divididas em dois grupos:

* Operações da Teoria de Conjuntos;
* Operações desenvolvidas especificamente para Bancos de Dados Relacionais.

### Operador SELECT - σ

Seleciona **tuplas**, segundo as condições dadas.

As condições podem utilizar valor constante, nome do atributo, operadores relacionais (=, <, ≤, ≥, ≠), operadores lógicos (AND, OR, NOT).

Propriedades:

* Operador unário (seleciona tuplas de apenas uma relação);
* Grau da relação resultante é igual ao da original;
* Comutativa.

### Operador PROJECT - π

Seleciona **colunas**, **removendo duplicatas**.

Propriedades:

* Grau da relação resultante é menor ou igual ao da original;
* NÃO é comutativa.

### Operações UNIÃO, INTERSECÇÃO, DIFERENÇA e PRODUTO CARTESIANO

São operações da teoria de conjuntos.

### Operador JOIN - ⊳⊲

Usado para combinar informações de duas ou mais relações. Pode ser interpretado como um **PRODUTO CARTESIANO seguido de um SELECT**.

#### EQUIJOIN

JOIN com operação de igualdade. Num EQUIJOIN há pares de atributos duplicados.

#### NATURAL JOIN - *

EQUIJOIN seguido da remoção de atributos duplicados desnecessários.

### Operador DIVISION - ÷

### Sequência de operações, relações intermediárias, renomeação de atributos

### Funções de agregação - ℑ

Funções que recebem um conjunto de tuplas e retornam um único valor:

* SUM;
* AVERAGE;
* MAX;
* MIN.
