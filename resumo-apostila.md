# Resumo - Apostila

## Capítulo 4 - Modelagem de dados usando o Modelo-Entidade Relacionamento (MER)

MER - modelo de dados conceitual de alto-nível

* `Entidade`: unidade básica que o MER representa
* `Atributo`: propriedades de uma entidade
  * Simples/atômico ou composto
  * Univalorado ou multivalorado
  * Derivado (ex: dt_nasc e idade)
  * nullable
* `Tipo de identidade`: conjunto de entidades com os mesmos atributos;
* `Atributo-chave`;

* `Relacionamento`:
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

* Atributos em tipos de relacionamento;
* `Entidade fraca`:
  * **Não** possui atributo-chave;
  * `Relacionamento de identificação`: entre a *entidade fraca* e o **proprietário da identificação**
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

## 6 Mapeamento do MER para o Modelo de Dados Relacional

`MER` = Modelo Entidade-Relacionamento

`DER` = Diagrama Entidade-Relacionamento

Passo a passo:

1. Mapeamento de entidade regular
2. Mapeamento de entidade fraca
3. Mapeamento de relacionamentos binários 1:1
4. Mapeamento de relacionamentos binários 1:N
5. Mapeamento de relacionamentos binários M:N
6. Mapeamento de atributo multivalorado
7. Mapeamento de relacionamentos N-ário
8. Mapeamento de generalização/especialização
9. Categoria (union type)
10. Agregações