# Descrição

O modelo de dados a seguir para representar **Gestão de Urbanismo**
são os `UnitRegistration`, `BuildingRegistration` e `UrbanProcess` inspirados no [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Estes modelos utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `UnitRegistration`.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Valor único atribuído automaticamente |
| type | String | Tipo de entidade | Valor constante igual a `UnitRegistration`    |
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'|
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| cadastreNumber       | String    | O número de artigo de matriz predial | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description   | String   | Descrição textual | Descrição adicional da fração. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dwellingType       | String    | Tipologia da fração | Apenas deve ser preenchido quando o uso da fração é residencial. Enumerado:<br>- T0, <br>- T1, <br>- T2, <br>- T3, <br>- T4+. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| landRegistryNumber   | String   | nº do registo predial | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| fractionId | String | O identificador da fração.| Idenficador único dentro do sistema fonte, e.g. CODSIG existentes em vários sistemas cartográficos de municípios.  Modelo: [https://schema.org/Text](https://schema.org/Text).|
| fractionNumber | String | O identificador da fração no registo predial.| Modelo: [https://schema.org/Text](https://schema.org/Text).|
| occupation   | String   | Situação da fração | Enumerado: <br>- ocupado,<br>- partialmente_ocupado, <br>- livre. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ownershipType   | String   | Tipo de propriedade | Enumerado:<br>- municipal, <br>- privado, <br>- estado, <br>- outro. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| refBuilding  | String     | Referência para entidade `BuildingRegistration` que agrega as frações | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| use       | String    | O tipo de uso da fração | Enumerado:<br>- residencial, <br>- comercial, <br>- uso_misto, <br>- industrial, <br>- terciário, <br>- equipamentos,<br>- logística, <br>- turismo, <br>- produção_agrícola, <br>- outros. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| stateOfPreservation       | String    | Estado de conservação do edifício | Enumerado:<br>- excelente, <br>- bom, <br>- suficiente, <br>- mau, <br>- medíocre. Modelo: [https://schema.org/Text](https://schema.org/Text)    |

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `BuildingRegistration`.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Valor único atribuído automaticamente |
| type | String | Tipo de entidade | Valor constante igual a `BuildingRegistration`    |
| buildingId | String | O identificador do edifício| Idenficador único dentro do sistema fonte, e.g. CODSIG existentes em vários sistemas cartográficos de municípios. Modelo: [https://schema.org/Text](https://schema.org/Text).|
| buildingNumber | String | O identificador do edifico no registo predial.| Modelo: [https://schema.org/Text](https://schema.org/Text).|
| address | Object | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira' |
| address.addressSubRegion | String | Uma sub região onde se situa a localidade | Este campo é obrigatório quando o campo 'address' é obrigatório. As sub-regiões correspondem às NUTS 3 conforme nomenclatura do INE. Valores possíveis: 'Alto Minho', 'Cávado', 'Ave', 'Área Metropolitana do Porto', 'Alto Tâmega e Barroso', 'Tâmega e Sousa', 'Douro', 'Terras de Trás-os-Montes', 'Região de Aveiro', 'Região de Coimbra', 'Região de Leiria', 'Viseu Dão Lafões', 'Beira Baixa', 'Beiras e Serra da Estrela', 'Oeste', 'Médio Tejo', 'Lezíria do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo Litoral', 'Baixo Alentejo', 'Alto Alentejo', 'Alentejo Central', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira' |
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| cadastreNumber       | String    | O número de artigo de matriz predial   | Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| description   | String   | Descrição textual | Descrição adicional da fração. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON |Localização a que reportam os valores |  Valores possíveis: 'Point',  'Polygon'.  |
| landRegistryNumber   | String   | nº do registo predial | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| workNumber   | String   | Identificador do volume de obra do edifício | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| occupation   | String   | Situação da fração | Enumerado: <br>- ocupado,<br>- parcialmente_ocupado, <br>- livre. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ownershipType   | String   | Tipo de propriedade | Enumerado:<br> - municipal,<br> - privado,<br> - estatal,<br> - principalmente_municipal,<br> - principalmente_privado,<br> - outro. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| propertyNature       | String    | Natureza do edifício | Enumerado:<br>- rustico, <br>- urbano, <br>- misto. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| stateOfPreservation       | String    | Estado de conservação do edifício | Enumerado:<br>- excelente, <br>- bom, <br>- suficiente, <br>- mau, <br>- medíocre. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| totalFractions       | Integer    | Total de frações do edifício | Valor positivo, incluindo 0.  Modelo: [https://schema.org/Integer](https://schema.org/Integer)    |
| use       | String    | O tipo de uso da fração | Enumerado:<br>- residencial, <br>- comercial, <br>- uso_misto, <br>- industrial, <br>- terciário, <br>- equipamentos,<br>- logística, <br>- turismo, <br>- produção_agrícola, <br>- outros. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| yearOfConstruction       | Integer    | Ano de construção do edifício | Valor positivo.  Modelo: [https://schema.org/Integer](https://schema.org/Integer)    |

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados `UrbanPlanningProcess`.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `UrbanPlanningProcess`    |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| interventionType       | String    | O tipo de intervenção que se quer licenciar | Enumerado: <br>- construção;<br>- reconstrução;<br>- ampliação;<br>- alteração_exterior;<br>- alteração_interior;<br>- conservação;<br>- construção_piscina.  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| lastDecisionAt        | DateTime | Registo de data e hora da última decisão sobre o processo |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| licenseNumber | String | Alvará de obra|  Modelo: [https://schema.org/Text](https://schema.org/Text).|
| phase       | String    | Fase do processo | Enumerado: <br>- submissão;<br>- saneamento_liminar;<br>- decisão;<br>- decisão_arquitetura;<br>- decisão_especialidades;<br>- decisão_controlo_sucessivo;<br>- pagamento_de_taxas_e_encargos;<br>- obra_diligências_seguintes;<br>- conclusão. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| proceedingDecision       | String    | Decisão atual | Enumerado: <br>- aprovação; <br>- aprovação_tácita;<br>- deferimento;<br>- deferimento_tácito;<br>- informação_favorável;<br>- informação_desfavorável;<br>- indeferimento;<br>- rejeição;<br>- ineptidão;<br>- rejeição_liminar;<br>- extinção;<br>- caducidade;<br>- determinação_vistoria;<br>- aperfeiçoamento. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| processNumber | String | O número do processo|  Modelo: [https://schema.org/Text](https://schema.org/Text).|
| procedureType       | String    | Tipo de procedimento | Enumerado:<br>- licenciamento;<br>- comunicação_prévia;<br>- comunicação_prévia_utilização;<br>- comunicação_prévia_com_prazo;<br>- pedido_de_informação_prévia;<br>- comunicação_de_início_de_trabalhos;<br>- outros_procedimentos. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| serviceCode       | String    | Código do serviço no CUSP | O código do serviço no CUSP, quando existente. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| status       | String    | O estado do processo | Enumerado:<br>- aguarda_pagamento;<br>- em_análise;<br>- aguarda_elementos;<br>- decidido_favorável;<br>- decidido_desfavorável;<br>- consultas_externas;<br>- aguarda_audiência_dos_interessados;<br>- aguarda_pedido_seguinte;<br>- arquivado;<br>- suspenso;<br>- aguarda_vistoria;<br>- aguarda_início_dos_trabalhos. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| responsibleEntityCode       | String    | Código da entidade no CUSP | O código da entidade no CUSP quando existente. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| refBuilding  | String     | Referência para uma entidade `BuildingRegistration` a que diz respeito o processo de licenciamento | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| refFraction  | String     | Referência para uma entidade `UnitRegistration` a que diz respeito o processo de licenciamento | Se o licenciamento for para o edificio todo, esta propriedade deve ser omitida. Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| submittedAt        | DateTime | Registo de data e hora da submissão do processo |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| urbanOperationType       | String    | Operação urbanística | Enumerado:<br>-construção;<br>- reconstrução;<br>- ampliação;<br>- alteração_exterior;<br>- alteração_interior;<br>- conservação;<br>- construção_piscina. Modelo: [https://schema.org/Text](https://schema.org/Text)    |

É de realçar que nem todas as combinações de valores dos atributos `procedureType` (colunas, itálico )e `proceedingDecision` (linhas) são possíveis, devendo ser seguindas as indicadas na tabela abaixo.
| proceedingDecision | licenciamento | comunicação_prévia | comunicação_prévia_utilização | comunicação_prévia_com_prazo | pedido_de_informação_prévia | comunicação_de_início_de_trabalhos | outros_procedimentos |
|---|---|---|---|---|---|---|---|
| aprovação | X | | | | | | |
| aprovação_tácita | X | | | | | | |
| deferimento | X | | | | | | X |
| deferimento_tácito | X | | | | X | | X |
| informação_favorável | | | | | X | | |
| informação_desfavorável | | | | | X | | |
| indeferimento | X | | | | | | X |
| rejeição | | | | X | | | |
| ineptidão | | X | X | X | | | |
| rejeição_liminar | X | | | | X | | |
| extinção | X | X | X | X | X | X | X |
| caducidade | X | X | | | X | X | |
| determinação_vistoria | | | | X | | | X |
| aperfeiçoamento | X | | | | X | | |

## Propriedades obrigatórias

Os atributos obrigatórios para o modelo `UnitRegistration` são:

- `id`
- `type`
- `address`
- `refBuilding`

Os atributos obrigatórios para o modelo `BuildingRegistration` são:

- `id`
- `type`
- `location`
- `address`

Os atributos obrigatórios para o modelo `UrbanPlanningProcess` são:

- `id`
- `type`
- `interventionType`
- `processNumber`
- `procedureType`
- `urbanOperationType`
- `status`
- `address`
- `location`
- `address`
- `dateCreated`
- `dateModified`

## Notas

Este modelo de dados reflete os requisitos e procedimentos previstos no RJUE (Decreto-Lei n.º 555/99), na sua redação atual, incluindo as alterações introduzidas pelo Decreto-Lei n.º 108/2026, bem como os modelos de requerimento, elementos instrutórios e regras de tramitação definidos pela Portaria n.º 320/2026.

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
