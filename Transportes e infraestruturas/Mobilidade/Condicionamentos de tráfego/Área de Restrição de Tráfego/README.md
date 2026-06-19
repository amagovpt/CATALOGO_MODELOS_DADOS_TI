# Descrição

O modelo de dados a seguir para representar **Condicionamentos de tráfego** é o [RestrictedTrafficArea](https://github.com/smart-data-models/dataModel.Transportation/blob/master/RestrictedTrafficArea/README.md) do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | -- |
| type | String | Tipo de entidade | Valor constante igual a `RestrictedTrafficArea` |
| address | Object | Morada associada à área de tráfego restrito | Inclui país, localidade, rua. Modelo: [https://schema.org/address](https://schema.org/address) |
| alternateName | String | Nome alternativo para este item | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| areaServed | String | A área geográfica onde é prestado um serviço ou oferecido um artigo | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| category | Array | Categoria(s) da área de tráfego restrito | O propósito deste campo é permitir etiquetar, de forma geral, entidades de área de tráfego restrito. Particularidades e descrições detalhadas devem ser encontradas sob os atributos específicos correspondentes. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dataProvider | String | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated | DateTime | Data e hora da criação | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| dateModified | DateTime | Registo de data e hora da última modificação da entidade | Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| description | String | Descrição textual da área de tráfego restrito | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o item | Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| name | String | Nome do objeto | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| notAllowedVehicleType | Array | Tipo(s) de veículo não permitido para atravessar a área de tráfego restrito | Lista de tipos de veículos proibidos. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| owner | Array | Lista contendo uma sequência codificada JSON de caracteres referenciando os Ids únicos do(s) proprietário(s) | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| regulation | URI | URL apontando para o regulamento para a área de tráfego restrito específica | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| restrictionExceptions | Array | Tipo de veículo individual permitido para atravessar a área de tráfego restrito numa faixa horária específica | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| restrictionValidityHours | String | Dias da semana e horas em que a restrição de tráfego está ativa | Formato ISO 8601 para períodos recorrentes (ex: "R-1/2024-12-16T08:00:00.00/P10H"). Modelo: [https://schema.org/Text](https://schema.org/Text) |
| security | Array | Aspetos de segurança fornecidos por esta área de tráfego restrito | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| seeAlso | URI | Lista de uri apontando para recursos adicionais sobre o item | Modelo: [https://schema.org/URL](https://schema.org/URL) |
| source | String | Uma sequência de caracteres dando a fonte original dos dados da entidade como URL | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| specialRestrictions | Array | Tipo de veículo individual não permitido para atravessar a área de tráfego restrito numa faixa horária específica | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| validityEndDate | DateTime | Data em que a restrição é removida | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |
| validityStartDate | DateTime | Data a partir da qual a restrição é aplicada | De acordo com a norma [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime) |

## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `type`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.