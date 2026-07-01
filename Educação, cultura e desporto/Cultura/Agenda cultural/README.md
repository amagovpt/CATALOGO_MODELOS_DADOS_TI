# Descrição

O modelo de dados a seguir para representar **Agenda Cultural**
é o `Event` inspirado do [FIWARE Smart Data Models](https://github.com/smart-data-models/). 
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).


## Propriedades
Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `Event`    |
| address                  | Object          | Endereço físico do evento | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| accessibility        | Array       | Recursos de acessibilidade disponíveis        |  Valores possíveis: 'wheelchairAccessible' ,'audioDescription' signLanguageInterpreter'. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| ageRating       | String       | Classificação etária do evento |  Modelo: [https://schema.org/Text](https://schema.org/Text)      |
| category | Array | Uma sequência de termos que pretendem classificar o  evento |   Lista de possíveis valores, individuais ou combinados: 'Literário', 'Cinema', 'Música', 'Tradicional', 'Religioso', 'Culinária', 'Educação', 'Comunitária', 'Desporto', 'Espetáculo', 'Artes Visuais', 'Festivais', 'Outros'.   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateFinished        | DateTime | Registo de data e hora da conclusão do evento |   É omitido quando a intervenção está a decorrer. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateStarted        | DateTime | Registo de data e hora de início do evento |   De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| image     | URI       | Imagem associada ao evento   |   Modelo: [https://schema.org/URL](https://schema.org/URL)    | 
| eventSchedule        | Object       | Horário do evento    | Inclui data, hora, recorrência e exceções. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o objecto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| license         | URI     | Licença dos dados | URL da licença. Ex: [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/). Modelo: [https://schema.org/URL](https://schema.org/URL) |
| maximumCapacity      | Number       | Capacidade máxima permitida de participantes   |    Modelo: [https://schema.org/Number](https://schema.org/Number)  |
| priceSpecification   | Array       | Informação sobre os preços do evento   | Inclui tipo de audiência, valor e tipo de moeda. Normalmente expressa em euros (EUR). 'Valor' pode tomar os seguintes valores: 'adult', 'student', e outros. Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| refEvent      | Array       | Referência para o evento agregador |   Relevantes para modelar sub-eventos co-localizados temporalmente, ou não, mas que fazem parte de um evento mais alargado. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| seeAlso    | Array         | Lista de URI que apontam para recursos adicionais sobre o item   | Pode apontar para outras informações sobre o evento. Modelo: [https://schema.org/URL](https://schema.org/URL)     |
| subject   | String       | Tema ou área artística do evento    | Modelo: [https://schema.org/Text](https://schema.org/Text)   | 
| subTitle  | String     | Subtítulo do evento      | Modelo: [https://schema.org/Text](https://schema.org/Text)      |
| tags      | Array       | Palavras-chave associadas ao evento | Valores possíveis: 'erudito, 'rock', 'pop'. Modelo: [https://schema.org/Text](https://schema.org/Text)     |
| targetAudience       | Array       | Público-alvo do evento | Valores possíveis: 'general', 'families', 'adults'. Modelo: [https://schema.org/Text](https://schema.org/Text)        |
| title   | String       | Título do evento         | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| venues    | Array   | Referência a entidades que representam os locais do evento.         | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)        |


## Propriedades obrigatórias

Os atributos obrigatórios são:
- `id`
- `title`
- `type`
- `category`
- `location`
- `dateStarted`
- `dateFinished`
- `ageRating`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.