# Descrição

Os modelos de dados a seguir para representar **Bilhética**
são os `PassengerCountAggregation`e `Organization` inspirados no [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
| ------------- | ------ | ----------- | ------------------------- |
| `id` | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| `type` | String | Tipo de entidade | Valor constante igual a `PassengerCountAggregation` |
| `name` | String | Designação legível da entidade, adequada para apresentação a utilizadores. | Modelo: [https://schema.org/Text](https://schema.org/Text). |
| `description` | String | Descrição textual da agregação representada pela entidade. | Deve explicar, de forma clara, o que está a ser contado, qual o operador e o período temporal.  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| `dataProvider` | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| `dateCreated` | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| `dateModified` | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| `operator` | URI | Referência para a entidade `Organization` que representa o operador de transporte público ao qual a agregação diz respeito. | -- |
| `measurementValue` | Integer | Valor numérico agregado da contagem observada no período considerado. | Modelo: [https://schema.org/Integer](https://schema.org/Integer). |
| `countType` | String | Tipo de contagem de passageiros representada pelo valor agregado em `measurementValue`. | Valores possíveis para as contagens: <br>- boarding, <br>- alighting, <br>- tripValidation. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| `aggregationPeriod` | String | Granularidade temporal da agregação. | Enumerado: <br>- `hour`,<br> - `day`,<br> - `week`, <br> - `month`,<br> - `year`.<br> Modelo: [https://schema.org/Text](https://schema.org/Text). |
| `startDate` | DateTime | Data e hora de início do intervalo temporal coberto pela agregação. | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime). |
| `endDate` | DateTime | Data e hora de fim do intervalo temporal coberto pela agregação. | De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime). |
| `generatedAt` |DateTime | Data e hora em que a agregação foi gerada no sistema de origem. | Corresponde ao instante de produção do registo agregado, não ao período observado. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime). |
| `source` | String | Sequência de caracteres que fornece a fonte original dos dados da entidade como um URL. | Nome de domínio totalmente qualificado do fornecedor de origem, ou o URL para o objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL) |
| `seeAlso` | Array | Lista de URI que apontam para recursos adicionais sobre o item | Pode apontar para projetos públicos ou documentos. Modelo: [https://schema.org/URL](https://schema.org/URL). |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `startDate`
- `endDate`
- `operator`
- `measurementValue`
- `countType`
- `aggregationPeriod`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
