# Descrição

Os modelos de dados para representar **Monitorização da rede de saneamento** é o `WastewaterQualityObserved` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/), são baseados nos requisitos da diretiva [INSPIRE](https://inspire-geoportal.ec.europa.eu/srv/eng/catalog.search#/home), nos conjuntos de dados de alto valor ([HVD](https://eur-lex.europa.eu/eli/reg_impl/2023/138/oj)) e segue as especificações da diretiva [EN 805](https://standards.iteh.ai/catalog/standards/cen/86c0b326-bc0f-42f5-82fb-3d3daa42cffc/en-805-2025?srsltid=AfmBOopqsDG1K91hPudoxPQ4QypDUR-suauhqRhhkM3f2sWjvqGUdjX0) para sistemas de tratamento de água.
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/) e com os requisitos de HVD da UE.
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `WastewaterQualityObserved`|
| address | Object | Endereço da localização da estação de monitorização | Inclui addressLocality, postalCode, streetAddress e type. Modelo: [https://schema.org/address](https://schema.org/address) |
| areaServed | String | Área geográfica servida pela estação de monitorização | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| biochemicalOxygenDemand | Object | Carência bioquímica de oxigénio (CBO) medida na água residual | Indicador de poluição orgânica. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| chemicalOxygenDemand | Object | Carência química de oxigénio (CQO) da água residual | Mede a carga orgânica e inorgânica. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| complianceStatus | String | Estado de conformidade com normas ambientais | Enumerado:<br>- Compliant,<br>- Non-Compliant. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateObserved | DateTime | Data e hora de observação | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dischargePoint | String | Ponto de descarga da água tratada | Pode ser um rio, lago, oceano, etc. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| heavyMetals | Object | Presença de metais pesados na água residual | Estrutura com concentrações de Lead, Mercury, Cadmium, etc. Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| location | GeoJSON | Localização geográfica da estação de monitorização | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome da observação | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| nitrates | Object | Concentração de nitratos na água residual | Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| pH | Object | Indica a acidez ou basicidade de soluções aquosas | Valor que varia entre 0 e 14. Inclui qualityAssessment com accuracy, precision e lastCalibration. Modelo: [https://schema.org/Number](https://schema.org/Number) |
| phosphates | Object | Concentração de fosfatos na água residual | Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| reportingAuthority | URI | Autoridade responsável pela monitorização e reporte da qualidade da água | Pode incluir URL da entidade responsável. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| temperature | Object | Temperatura da água | Normalmente expressa em graus Celsius (CEL). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| totalSuspendedSolids | Object | Sólidos suspensos totais (TSS) na amostra de água | Normalmente expressa em mg/l (M1). Modelo: [https://schema.org/Number](https://schema.org/Number) |
| treatmentLevel | String | Nível de tratamento aplicado à água residual | Enumerado: <br>- Primary,<br>- Secondary,<br>- Tertiary,<br>- Quaternary.  Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `dateObserved`
- `location`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.