# Descrição

Os modelos desta categoria são de uso genérico de vários temas e subtemas, por exemplo Bombeiros, Casa da Música. Estes modelos utilizam o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo destes modelos, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).
De seguida são feitas algumas considerações sobre alguns dos modelos mais relevantes.

## `PointOfInterest`

O modelo [PointOfInterest](https://github.com/smart-data-models/dataModel.PointOfInterest) é retirado do [FIWARE Smart Data Models](https://github.com/smart-data-models). Este modelo tem a possibilidade de o categorizar usando a propriedade `category`, que é um array de valores. Assim, é possível categorizar o ponto de interesse seguindo uma terminologia definida para o efeito. É possível um ponto de interesse ter vários termos que o definam, ex: escola com diferentes ciclos de estudos. As propriedades possíveis são as seguintes:

### Propriedades

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type     | String    | Tipo de entidade     |  Valor constante igual a `PointOfInterest`. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao) |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do [INE](https://www.ine.pt/xportal/xmain?xpid=INE&xpgid=ine_pesquisa&frm_accao=PESQUISAR&frm_show_page_num=1&frm_modo_pesquisa=PESQUISA_SIMPLES&frm_texto=NUTS&frm_modo_texto=MODO_TEXTO_ALL&frm_data_ini=&frm_data_fim=&frm_tema=QUALQUER_TEMA&frm_area=o_ine_area_Metainformacao). Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| alternateName          | String    | Nome alternativo para este item       |   Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| areaServed             | String    | Área geográfica onde o serviço ou item é fornecido  | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| capacity | Number    | Número total de pessoas que podem ser alocadas ao mesmo tempo     |    Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| category | Array     | Categoria deste ponto de interesse    | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| contactPoint           | Object    | Detalhes de contacto do item          | Modelo: [https://schema.org/ContactPoint](https://schema.org/ContactPoint)        |
| contactPoint.areaServed| String    | Área geográfica de cobertura do contacto            |    Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.availabilityRestriction | *         | Informação sobre quando o ponto de contacto não está disponível   | Os pormenores são fornecidos utilizando a classe Especificação do Horário de Abertura. Modelo: [http://schema.org/hoursAvailable](http://schema.org/hoursAvailable)       |
| contactPoint.availableLanguage       | String         | Língua utilizável com o serviço ou local            | Modelo: [http://schema.org/availableLanguage](http://schema.org/availableLanguage)    |
| contactPoint.contactOption           | Array        | Opção disponível neste ponto de contacto     | Modelo: [http://schema.org/contactOption](http://schema.org/contactOption)        |
| contactPoint.contactType             | String    | Tipo de contacto deste item           |   Uma pessoa ou organização pode ter diferentes pontos de contacto, para diferentes fins. Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| contactPoint.email     | idn-email | Endereço de email do proprietário     |  Modelo: [https://schema.org/Text](https://schema.org/Text)     |
| contactPoint.faxNumber | String    | Número de fax do item   | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.name      | String    | Nome do ponto de contacto             |   Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| contactPoint.productSupported        | String    | Produto ou serviço suportado por este ponto de contacto           | Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.telephone | String    | Telefone de contacto    |    Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| contactPoint.url       | URI       | URL com descrição ou mais informação sobre o item   |    Modelo: [https://schema.org/URL](https://schema.org/URL)  |
| dataProvider  | String    | Uma sequência de caracteres que identifica o fornecedor da entidade de dados | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| image    | URI       | Imagem do item          | Modelo: [https://schema.org/URL](https://schema.org/URL)   |
| location | GeoJSON | Referência Geojson para a entidade |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon' |
| municipalityInfo       | Object    | Informação municipal correspondente a esta observação            | Modelo: [https://schema.org/Text](https://schema.org/Text)     |
| municipalityInfo.cityID| String    | Identificador da cidade associada a esta observação            | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.cityName            | String    | Nome da cidade associada a esta observação          | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.district            | String    | Nome do distrito associado a esta observação        | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.stateName           | String    | Nome do estado associado a esta observação          | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.ulbName             | String    | Nome da entidade urbana local associada             | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.wardID| String    | Identificador da freguesia associada             | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.wardName            | String    | Nome da freguesia associada           | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.wardNum             | Number    | Número da freguesia associada         | Modelo: [https://schema.org/Number](https://schema.org/Number) |
| municipalityInfo.zoneID| String    | Identificador da zona associada    | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| municipalityInfo.zoneName            | String    | Nome da zona associada  | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| name | String | Nome do objeto |  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| occupancy | Number    | Número de pessoas no ponto de interesse | Deve ser inferior à capacidade.  Modelo: [https://schema.org/Number](https://schema.org/Number)  |
| owner    | Array     | Lista codificada com os identificadores únicos do(s) proprietário(s) |  Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| priceRange  | String    | Descrição da gama de preços para acesso ao Ponto de Interesse     |  Modelo: [https://schema.org/Text](https://schema.org/Text)     |
| refSeeAlso  | Array     | Lista de referências para entidades relacionadas    | Referência URN a uma entidade.  Modelo: [https://schema.org/Text](https://schema.org/Text)   |
| relevance | Number    | Relevância do ponto de interesse para apresentação em diferentes níveis de zoom |   Modelo: [https://schema.org/Number](https://schema.org/Number)   |
| seeAlso      | Array         | Lista de URI que apontam para recursos adicionais sobre o item     | Pode apontar para projetos públicos ou documentos. Modelo: [https://schema.org/URL](https://schema.org/URL)     |
| source   | String    | Sequência de caracteres que fornece a fonte original dos dados da entidade como um URL  |   Recomenda-se que seja o nome de domínio totalmente qualificado do fornecedor de origem, ou o URL para o objeto de origem. Modelo: [https://schema.org/URL](https://schema.org/URL)   |
| title    | String    | Nome atribuído ao ponto de interesse além do nome específico      | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| wardId   | String    | Identificador da freguesia correspondente a esta observação    | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| zoneId   | String    | Identificador da zona correspondente a esta observação        | Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| zoneName | String    | Nome da zona correspondente a esta observação       | Modelo: [https://schema.org/Text](https://schema.org/Text)  |

[*] Se não existir um tipo num atributo é porque este pode ter vários tipos ou diferentes formatos/padrões.

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`  
- `type`
- `name`  
- `address`
- `category`
- `location`

### Categorização

Para garantir a qualidade dos dados e a sua correta categorização no contexto de utilização do `PointOfInterest`, os campos 'Temática' e 'Categoria' da tabela abaixo devem ser utilizados para organizar adequadamente os termos. Os valores a inserir no campo `category` devem corresponder a um ou mais dos disponíveis na coluna 'Subcategoria'.

| Temática      | Categoria       | Subcategoria    |
|:--------------|:----------------|:--------------------------------------------|
| Transporte e Mobilidade            | Transportes Públicos        | Paragem de autocarro          |
| Transporte e Mobilidade            | Transportes Públicos        | Estação de comboio            |
| Transporte e Mobilidade            | Transportes Públicos        | Estação de metro|
| Transporte e Mobilidade            | Transportes Públicos        | Estação fluvial |
| Transporte e Mobilidade            | Transportes Públicos        | Elevador/Ascensor             |
| Transporte e Mobilidade            | Transportes Públicos        | Praça de táxis  |
| Transporte e Mobilidade            | Infraestruturas Náuticas    | Terminal de cruzeiros         |
| Transporte e Mobilidade            | Infraestruturas Náuticas    | Marina          |
| Transporte e Mobilidade            | Infraestruturas Náuticas    | Cais            |
| Transporte e Mobilidade            | Infraestruturas Rodoviárias | Posto de abastecimento        |
| Transporte e Mobilidade            | Infraestruturas Rodoviárias | Ponto de carregamento de veículos elétricos |
| Transporte e Mobilidade            | Mobilidade suave            | Doca de bicicletas            |
| Transporte e Mobilidade            | Mobilidade suave            | Doca de trotinetes            |
| Transporte e Mobilidade            | Transporte Aéreo            | Aeroporto       |
| Transporte e Mobilidade            | Transporte Aéreo            | Terminal        |
| Transporte e Mobilidade            | Transporte Aéreo            | Heliporto       |
| Transporte e Mobilidade            | Estacionamento| Parque de estacionamento      |
| Serviços Públicos e Governamentais | Segurança     | Esquadra PSP    |
| Serviços Públicos e Governamentais | Segurança     | Posto GNR       |
| Serviços Públicos e Governamentais | Segurança     | Quartel de bombeiros          |
| Serviços Públicos e Governamentais | Segurança     | Prisão          |
| Serviços Públicos e Governamentais | Administração Pública       | Câmara Municipal|
| Serviços Públicos e Governamentais | Administração Pública       | Junta de Freguesia            |
| Serviços Públicos e Governamentais | Administração Pública       | Tribunal        |
| Serviços Públicos e Governamentais | Administração Pública       | Ministério      |
| Serviços Públicos e Governamentais | Administração Pública       | Embaixada       |
| Serviços Públicos e Governamentais | Administração Pública       | Conservatória   |
| Serviços Públicos e Governamentais | Administração Pública       | Loja do cidadão |
| Serviços Públicos e Governamentais | Administração Pública       | Finanças        |
| Serviços Públicos e Governamentais | Serviços      | Estação de correios           |
| Serviços Públicos e Governamentais | Serviços      | Abrigo para animais           |
| Educação e Conhecimento            | Educação      | Creche/Jardim de infância   |
| Educação e Conhecimento            | Educação      | Escola 1º ciclo  |
| Educação e Conhecimento            | Educação      | Escola 2º e 3º ciclo          |
| Educação e Conhecimento            | Educação      | Escola secundária             |
| Educação e Conhecimento            | Educação      | Universidade    |
| Educação e Conhecimento            | Educação      | Instituto Politécnico         |
| Educação e Conhecimento            | Educação      | Ensino Profissional           |
| Educação e Conhecimento            | Educação      | Biblioteca      |
| Saúde  | Infraestruturas de Saúde    | Hospital        |
| Saúde  | Infraestruturas de Saúde    | Clínica         |
| Saúde  | Infraestruturas de Saúde    | Farmácia        |
| Saúde  | Infraestruturas de Saúde    | Centro de saúde |
| Saúde  | Infraestruturas de Saúde    | Posto de primeiros socorros      |
| Saúde  | Infraestruturas de Saúde    | Desfibrilhador  |
| Saúde  | Infraestruturas de Saúde    | Termas          |
| Saúde  | Apoio Social  | Lar de idosos   |
| Comércio e Serviços  | Retalho       | Mercado         |
| Comércio e Serviços  | Retalho       | Feira/mercado   |
| Cultura, Lazer e Desporto          | Cultura       | Cinema          |
| Cultura, Lazer e Desporto          | Cultura       | Centro de conferências        |
| Cultura, Lazer e Desporto          | Cultura       | Sala de espetáculos e auditórios            |
| Cultura, Lazer e Desporto          | Cultura       | Teatro          |
| Cultura, Lazer e Desporto          | Cultura       | Museu           |
| Cultura, Lazer e Desporto          | Lazer         | Parque          |
| Cultura, Lazer e Desporto          | Lazer         | Casino          |
| Cultura, Lazer e Desporto          | Lazer         | Jardim          |
| Cultura, Lazer e Desporto          | Lazer         | Parque infantil |
| Cultura, Lazer e Desporto          | Desporto      | Campo de futebol|
| Cultura, Lazer e Desporto          | Desporto      | Campo de golfe  |
| Cultura, Lazer e Desporto          | Desporto      | Piscina         |
| Cultura, Lazer e Desporto          | Desporto      | Parque desportos radicais     |
| Cultura, Lazer e Desporto          | Desporto      | Estádio         |
| Cultura, Lazer e Desporto          | Desporto      | Equipamento de desporto ao ar livre  |
| Turismo e Alojamento | Alojamento    | Hotel           |
| Turismo e Alojamento | Alojamento    | Pousada/Hostel  |
| Turismo e Alojamento | Alojamento    | Alojamento local|
| Turismo e Alojamento | Pontos Turísticos           | Miradouro       |
| Turismo e Alojamento | Pontos Turísticos           | Monumento       |
| Turismo e Alojamento | Pontos Turísticos           | Posto de turismo|
| Culto e Espiritualidade            | Lugares de culto            | Igreja          |
| Culto e Espiritualidade            | Lugares de culto            | Mesquita        |
| Culto e Espiritualidade            | Lugares de culto            | Cemitério       |
| Ambiente e Natureza  | Recursos Naturais           | Floresta        |
| Ambiente e Natureza  | Recursos Naturais           | Lago            |
| Ambiente e Natureza  | Recursos Naturais           | Praia           |
| Ambiente e Natureza  | Áreas Protegidas            | Reserva natural |
| Ambiente e Natureza  | Áreas Protegidas            | Parque natural  |
| Infraestrutura Técnica e Resíduos  | Energia e Água| Subestação elétrica           |
| Infraestrutura Técnica e Resíduos  | Energia e Água| Estação de tratamento         |
| Infraestrutura Técnica e Resíduos  | Energia e Água| Fontanário/ponto de água      |
| Infraestrutura Técnica e Resíduos  | Ambiente      | Estação Meteorológica      |
| Infraestrutura Técnica e Resíduos  | Gestão de resíduos          | Ecoponto        |
| Infraestrutura Técnica e Resíduos  | Gestão de resíduos          | Aterro sanitário|
| Infraestrutura Técnica e Resíduos  | Gestão de resíduos          | Central de recolha de resíduos|
| Espaço Público e Serviços          | Equipamento   | Instalações sanitárias públicas             |

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_3763/ETRS89-Portugal-TM06.html), por exemplo `"coordinateSystem": "EPSG:3763"`. Nos atributos (incluindo metainformação) que não sejam percentagens ou valores a variar entre 0 e 1, existe o campo `unitCode` que indica a unidade de medida do valor. Este campo é expresso usando o padrão [UN/CEFACT Common Codes](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes) (max. 3 carácteres).

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
