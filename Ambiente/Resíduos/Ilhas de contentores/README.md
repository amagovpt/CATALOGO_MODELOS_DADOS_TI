# Descrição

O modelos de dado a seguir para representar **Ilhas de Contentores** 
é o [WasteContainerIsle](https://github.com/smart-data-models/dataModel.WasteManagement/tree/952dca8b1b9b2b5fe8e82dcba25599316ab1478e/WasteContainerIsle) do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da ilha | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `WasteContainerIsle` |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao) |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao). Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text)|
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| features      | Array     |  Lista de caraterísticas fornecidas pela ilha  | Modelo: [https://schema.org/Text](https://schema.org/Text) | 
| location | GeoJSON | Localização da entidade |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'.  |
| name | String | Nome do objeto |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| refWasteContainer | Array | Lista dos contentores presentes no ilhas | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |

## Propriedades obrigatórias

Os atributos obrigatórios são:

 - `id`
 - `location`
 - `type`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).


A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.