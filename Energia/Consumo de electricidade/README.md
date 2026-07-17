# Descrição

O modelo de dados a seguir para representar **Consumo de eletricidade**
é o [ACMeasurement](https://github.com/smart-data-models/dataModel.Energy/blob/master/ACMeasurement/README.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models/). Este modelo utiliza uma corrente alternada (AC) para um sistema trifásico (L1, L2, L3) ou monofásico (L) e neutro (N). Inclui atributos para várias medições eléctricas, como potência, frequência, corrente e tensão. Este modelo tem a particularidade de ter como um dos valores da lista do atributo `type` o valor `ACMeasurement`.
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `ACMeasurement`|
| activePower    | Object    | Potência ativa consumida por fase  | Valores de L1, L2 e L3 que representam valores para a fase 1, 2 e 3, respetivamente. Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) | 
| address    | Object          | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| alternateName       | String          | Nome alternativo para a área de medida  |  Ex: nome comum ou local da localização  |
| apparentEnergyExport  | Object    | 
| apparentPower    | Object    | Potência aparente consumida por fase  | Valores de L1, L2 e L3 que representam valores para a fase 1, 2 e 3, respetivamente. Normalmente expressa em volt-ampere (VA). Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) | 
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| current    | Object    | Corrente eléctrica por fase  | Valores de L1, L2, L3 e N que representam valores para a fase 1, 2, 3 e neutra, respetivamente. Normalmente expressa em ampere (AMP). Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue) | 
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateEnergyMeteringStarted        | DateTime | Data de início da contagem da energia  |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObserved        | DateTime | Data e hora da observação  |  Pode ser representado por um instante de tempo específico ou por um intervalo [ISO 8601-1:2019](https://www.iso.org/standard/70907.html) para separar os atributos `dateObservedFrom`,`dateObservedTo`. Obrigatório `dateObservedFrom`,`dateObservedTo` não estiverem definidos. se  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObservedFrom        | DateTime | Data e hora do início da observação  | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Obrigatório se `dateObserved` não estiver definido.  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateObservedTo        | DateTime | Data e hora do fim da observação  | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html).  Obrigatório se `dateObserved` não estiver definido.  Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| displacementPowerFactor   | Object    | Fator de potência de deslocamento para cada fase | A quantidade é baseada na frequência fundamental do sistema.  Modelo: [https://schema.org/Number](https://schema.org/Number) |
| frequency | Number    | Frequência do circuito    | Normalmente expressa em hertz (HTZ) Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Referência Geojson para a entidade |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'. O mesmo que [Geometry](https://inspire.ec.europa.eu/codelist/GeometrySpecificationValue) |
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| phaseToPhaseVoltage   | Object    | Valor da voltagem entre fases | Valores medidos: L12, L23 e L31, i.e. valor da tensão da fase 1 para a fase 2, da fase 2 para a fase 3 e daa fase 3 para a fase 1, respetivamente. Normalmente expressa em volts (VLT). odelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue)   |
| phaseType | String    | Tipo de fase, único   | Enumerado: <br>- 'singlePhase', <br>- 'threePhase. Modelo: [https://schema.org/Text](https://schema.org/Text)|
| phaseVoltage  | Object    | Tensão entre cada condutor de fase e neutro   | Valores medidos: L1, L2 e L3.  Normalmente expressa em volts (VLT). Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue)   |
| powerFactor   | Object    | Fator de potência para cada fase   | Valores medidos: L1, L2 e L3.  Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue)   |
| reactivePower | Object    | Potência reactiva de frequência   | Valores medidos: L1, L2 e L3. Normalmente expressa em volt-ampere reactiva (VAR).  Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue)   | 
| thdCurrent    | Object    | Distorção harmónica total da corrente para cada fase | Valores medidos: L1, L2 e L3.  Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue)   | 
| thdVoltage    | Object    | Distorção harmónica total da tensão para cada fase | Valores medidos: L1, L2 e L3.  Modelo: [https://schema.org/StructuredValue](https://schema.org/StructuredValue)   | 
| totalActiveEnergyExport    | Number    | Energia total exportada |  Modelo: [https://schema.org/Number](https://schema.org/Number)   | 
| totalActiveEnergyImport    | Number    | Energia total consumida |  Modelo: [https://schema.org/Number](https://schema.org/Number)   | 
| totalActivePower    | Number    | Potência ativa total consumida |  Normalmente expressa em watts (WTT). Modelo: [https://schema.org/Number](https://schema.org/Number)   | 
| totalApparentPower    | Number    | Potência aparente total consumida |  Normalmente expressa em volt-ampere (VA). PowerModelo: [https://schema.org/Number](https://schema.org/Number)   | 
| totalReactiveEnergyExport    | Number    | Total da energia reactiva de frequência  exportada |  Normalmente expressa em kilovolt-ampere-hora reactiva (KVARH). Modelo: [https://schema.org/Number](https://schema.org/Number)   | 
| totalReactiveEnergyImport    | Number    | Total da energia reactiva consumida |  Normalmente expressa em kilovolt-ampere-hora reactiva (KVARH). Modelo: [https://schema.org/Number](https://schema.org/Number)   | 

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `generatorType`
- `location`
- `installedCapacity`
- `connectionType`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).
Para determinados atributos, como a corrente e a tensão, o valor assume uma estrutura com propriedades específicas para uma única fase (L) ou para três fases distintas (L1, L2 e L3). Em algumas medições, como nos diferentes tipos de potência (ativa, reativa e aparente), existe um atributo que representa o valor total agregado de todas as fases. As regras são definidas da seguinte forma:

- Trifásico - Total = L1 + L2 + L3
- Monofásico - Total = L.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
