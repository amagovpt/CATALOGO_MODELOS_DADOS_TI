# Descrição

Os modelos de dados para representar **Monitorização da rede de saneamento** é o `WastewaterQualityObserved` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home), nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)) e segue as especificações da diretiva [EN 805](https://standards.iteh.ai/catalog/standards/cen/86c0b326-bc0f-42f5-82fb-3d3daa42cffc/en-805-2025?srsltid=AfmBOopqsDG1K91hPudoxPQ4QypDUR-suauhqRhhkM3f2sWjvqGUdjX0) para sistemas de tratamento de água.
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `WastewaterQualityObserved`|
| address | Object | Morada associada ao local | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String | O país | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry) |
| address.addressLocality| String | A localidade tem de ser coincidente com o município | Este campo é obrigatório quando o campo 'address' é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality) |
| address.addressRegion | String | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o campo 'address' é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district | String | Um distrito é um tipo de divisão administrativa | Este campo é obrigatório quando o campo 'address' é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode | String | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode) |
| address.streetAddress | String | Endereço da rua | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)  |
| address.streetNr | String | Número de polícia | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | Área geográfica servida pela estação de monitorização | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| biochemicalOxygenDemand | Number | Carência bioquímica de oxigénio (CBO) medida na água residual | Indicador de poluição orgânica. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| chemicalOxygenDemand | Number | Carência química de oxigénio (CQO) da água residual | Mede a carga orgânica e inorgânica. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| complianceStatus | String | Estado de conformidade com normas ambientais | Enumerado:<br>- Compliant,<br>- Non-Compliant. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObserved | DateTime | Data e hora de observação | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dischargePoint | String | Ponto de descarga da água tratada | Pode ser um rio, lago, oceano, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| heavyMetals | Object | Presença de metais pesados na água residual | Estrutura com concentrações de Lead, Mercury, Cadmium, etc. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Localização geográfica da estação de monitorização | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| micropollutants | Object | Presença de micropoluentes na água residual, nomeadamente resíduos farmacêuticos, cosméticos e outras substâncias resultantes da atividade humana | 
Estrutura com propriedades para diversas substâncias (e.g. diclofenac, carbamazepina, estradiol, entre outras), cada uma com a sua concentração e, quando aplicável, taxa de remoção. Normalmente expressa em µg/l ou ng/l. Modelo: https://schema.org/Number |
| name | String | Nome da observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nitrates | Object | Concentração de nitratos na água residual | Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| nitrogen | Object | Azoto total presente na água residual, resultante da soma das diferentes formas de azoto | Estrutura agregando os componentes que constituem o azoto total: azoto Kjeldahl (orgânico + amoniacal), nitratos (NO3) e nitritos (NO2). Relevante para verificação do cumprimento dos limiares de tratamento terciário. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pH | Object | Indica a acidez ou basicidade de soluções aquosas | Valor que varia entre 0 e 14. Inclui qualityAssessment com accuracy, precision e lastCalibration. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| phosphates | Object | Concentração de fosfatos na água residual | Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| phosphorus | Object | Fósforo total presente na água residual, resultante da soma das diferentes formas de fósforo | Estrutura agregando os componentes que constituem o fósforo total, incluindo ortofosfatos, polifosfatos e fósforo orgânico. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| reportingAuthority | URI | Autoridade responsável pela monitorização e reporte da qualidade da água | Pode incluir URL da entidade responsável. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| temperature | Object | Temperatura da água | Normalmente expressa em graus Celsius (CEL). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalSuspendedSolids | Object | Sólidos suspensos totais (TSS) na amostra de água | Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| treatmentLevel | String | Nível de tratamento aplicado à água residual | Enumerado: <br>- Primary,<br>- Secondary,<br>- Tertiary,<br>- Quaternary.  Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `dateObserved`
- `location`

Têm de ser incluídas os valores de *todos* os parâmetros de decorrem de imposições legais ([e.g Directiva (EU) 2024/3019](https://eur-lex.europa.eu/legal-content/PT/TXT/?uri=CELEX:32024L3019) do Parlamento Europeu e do Conselho de 27 de novembro de 2024), podendo estes variar dependendo do tipo do usufruto que a água terá.

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.