# Descrição

O modelo de dados apresentado de seguida representa **observações da qualidade da água** numa determinada secção de uma massa de água, como um rio, lago ou mar.
É compatível com o modelo [`WaterQualityObserved`](https://github.com/smart-data-models/dataModel.WaterQuality/blob/master/WaterQualityObserved/doc/spec.md), versão 0.0.6.
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, que ilustra a sua utilização no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes).

## Propriedades

Na tabela abaixo são apresentadas todas as propriedades constantes da especificação, incluindo as subpropriedades do objeto `address`.

| Propriedade | Tipo | Descrição | Nota |
| --- | --- | --- | --- |
| id | URI | Identificador único da entidade. | Obrigatória. Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo da entidade NGSI-LD. | Obrigatória. Valor fixo: `WaterQualityObserved`. |
| Al | Número | Alumínio. Concentração de alumínio. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| As | Número | Arsénio. Concentração de arsénio. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| B | Número | Boro. Concentração de boro. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| Ba | Número | Bário. Concentração de bário. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Cd | Número | Cádmio. Concentração de cádmio. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Chla | Número | Concentração de clorofila A. | Valor mínimo: 0. |
| Cl- | Número | Concentração de cloretos. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| Cr | Número | Crómio. Concentração de crómio. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Cr-III | Número | Crómio III. Concentração de crómio no estado de oxidação +3. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Cr-VI | Número | Crómio VI. Concentração de crómio no estado de oxidação +6. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Cu | Número | Cobre. Concentração de cobre na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| Fe | Número | Ferro. Concentração de ferro na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Hg | Número | Mercúrio. Concentração de mercúrio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| N-TOT | Número | Azoto total. Soma do azoto na forma de nitrato (NO3-N), nitrito (NO2-N), amónia (NH3-N) e do azoto ligado organicamente. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| NH3 | Número | Concentração de amónia na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| NH4 | Número | Concentração de amónio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| NO2 | Número | Concentração de nitritos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| NO3 | Número | Concentração de nitratos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| Ni | Número | Níquel. Concentração de níquel na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| O2 | Número | Nível de oxigénio livre, não combinado, presente na água. | Valor mínimo: 0. |
| P-PO4 | Número | Fósforo-fosfato. Concentração de fósforo na forma de fosfato. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| P-TOT | Número | Fósforo total. Medida de todas as formas de fósforo na água, incluindo as formas dissolvidas e particuladas, orgânicas e inorgânicas. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| PC | Número | Concentração do pigmento ficocianina, que pode ser medida para estimar especificamente a concentração de cianobactérias. | Valor mínimo: 0. |
| PE | Número | Concentração do pigmento ficoeritrina, que pode ser medida para estimar especificamente a concentração de cianobactérias. | Valor mínimo: 0. |
| PO4 | Número | Concentração de fosfatos na amostra de água. | Valor mínimo: 0. |
| Pb | Número | Chumbo. Concentração de chumbo na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Se | Número | Selénio. Concentração de selénio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Sn | Número | Estanho. Concentração de estanho na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| THC | Número | Hidrocarbonetos. Concentração total de hidrocarbonetos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| TKN | Número | Azoto Kjeldahl total. Medida que determina as formas orgânicas e inorgânicas de azoto. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| TO | Número | Teor total de óleo. Concentração de óleo. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| Zn | Número | Zinco. Concentração de zinco. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| address    | Object          | Morada associada ao ponto de medição | Inclui município, região, rua, número e código postal, entre outros. Modelo: [https://schema.org/address](https://schema.org/address). A localidade tem de ser coincidente com o município. As regiões correspondem às NUTS 2 conforme nomenclatura do INE |
| address.addressCountry| String    | Indica o país        | Por exemplo, Portugal. Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)     |
| address.addressLocality| String    | A localidade tem de ser coincidente com o município        | Este campo é obrigatório quando o atributo `address` é obrigatório. Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | A região em que se situa a localidade, e que fica no país | Este campo é obrigatório quando o atributo `address` é obrigatório. As regiões correspondem às NUTS 2 conforme nomenclatura do INE. Valores possíveis: 'Norte', 'Centro', 'Oeste e Vale do Tejo', 'Grande Lisboa', 'Península de Setúbal', 'Alentejo', 'Algarve', 'Região Autónoma dos Açores', 'Região Autónoma da Madeira'
| address.district  | String    | Um distrito é um tipo de divisão administrativa |  Este campo é obrigatório quando o atributo `address` é obrigatório. Valores possíveis: 'Açores', 'Aveiro', 'Beja', 'Braga', 'Bragança', 'Castelo Branco', 'Coimbra', 'Évora', 'Faro', 'Guarda', 'Madeira', 'Leiria', 'Lisboa', 'Portalegre', 'Porto', 'Santarém', 'Setúbal', 'Viana do Castelo', 'Vila Real', 'Viseu' |
| address.postalCode     | String    | Código postal | Modelo: [https://schema.org/postalCode](https://schema.org/postalCode)          |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)|
| address.streetNr       | String    | Número de polícia  |   Modelo: [https://schema.org/Text](https://schema.org/Text) |
| acrylamide | Número | Concentração de acrilamida. | Valor mínimo: 0. Normalmente expresso em  `μg/l`. |
| alkalinity | Número | A alcalinidade da água corresponde à sua capacidade de neutralização de ácidos e compreende o total das bases tituláveis. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| alternateName | String | Nome alternativo do elemento. | — |
| anionic-surfactants | Número | Concentração de tensioativos aniónicos. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| areaServed | String | Área geográfica onde é prestado um serviço ou disponibilizado um elemento. | Modelo de referência: [https://schema.org/Text](https://schema.org/Text). |
| bod | Número | Carência bioquímica de oxigénio (CBO): quantidade de oxigénio dissolvido necessária aos organismos biológicos aeróbios para decompor a matéria orgânica presente numa amostra de água, a uma determinada temperatura e durante um período específico. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| cationic-surfactants | Número | Concentração de tensioativos catiónicos. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| cod | Número | Carência química de oxigénio (CQO): medida indicativa da quantidade de oxigénio que pode ser consumida por reações numa solução analisada. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| componentAnalyzed | String | Símbolo do componente analisado na amostra. | — |
| componentName | String | Nome completo do componente analisado na amostra. | — |
| concentration | Número | Concentração do componente analisado na amostra. | Normalmente expresso em  `µg/l`. |
| conductance | Número | Condutância específica. | Valor mínimo: 0. |
| conductivity | Número | Condutividade elétrica. | Valor mínimo: 0. Normalmente expresso em  `µS/cm`. |
| dataProvider | String | Sequência de carateres que identifica o fornecedor da entidade de dados harmonizada. | — |
| dateCreated | Data/hora | Data e hora de criação da entidade. Este valor é normalmente atribuído pela plataforma de armazenamento. | — |
| dateModified | Data/hora | Data e hora da última alteração da entidade. Este valor é normalmente atribuído pela plataforma de armazenamento. | — |
| dateObserved | String | Data e hora da observação, em formato ISO 8601 UTC. Pode representar um instante específico ou um intervalo ISO 8601. | Obrigatória. Formato ISO 8601 UTC; admite um instante ou um intervalo. Modelo de referência: [https://schema.org/DateTime](https://schema.org/DateTime). |
| description | String | Descrição do elemento. | — |
| enterococci | Número | Concentração de enterococos. | Valor mínimo: 0. Normalmente expresso em  número total de bactérias por 100 mL. |
| escherichiaColi | Número | Concentração de Escherichia coli. | Valor mínimo: 0. Normalmente expresso em  número total de bactérias por 100 mL. |
| flow | Número | Caudal de água observado. | Normalmente expresso em  metros cúbicos por hora. |
| fluoride | Número | Concentração de fluoretos. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| location | GeoJSON | Referência geográfica GeoJSON do elemento. Pode ser Point, LineString, Polygon, MultiPoint, MultiLineString ou MultiPolygon. | Obrigatória. Geometrias admitidas: `Point`, `LineString`, `Polygon`, `MultiPoint`, `MultiLineString` e `MultiPolygon`. |
| measurand | Array | Lista de strings com os detalhes de grandezas adicionais disponibilizadas pela observação. | Deve conter pelo menos um elemento. |
| M656PH051 | Número | Concentração do analito identificado no relatório pelo código M656PH051. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| name | String | Nome do elemento. | — |
| non-ionic-surfactants | Número | Concentração de tensioativos não iónicos. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| orp | Número | Potencial de oxidação-redução. | Valor mínimo: 0. |
| owner | Array de URI | Lista de identificadores únicos dos proprietários da entidade. | Lista de identificadores de entidades. |
| pH | Número | Acidez ou basicidade de uma solução aquosa. | Valor entre 0 e 14. |
| coliformBacteria | Número | Concentração de bactérias coliformes na amostra de água. | Valor mínimo: 0. Normalmente expresso em  número de bactérias por 100 ml (`N/100ml`). |
| residualDisinfectant | Número | Concentração do desinfetante residual presente na água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| odour25C | Número | Cheiro da água determinado à temperatura de 25 °C. | Valor mínimo: 0. Normalmente expresso em  fator de diluição. |
| taste25C | Número | Sabor da água determinado à temperatura de 25 °C. | Valor mínimo: 0. Normalmente expresso em  fator de diluição. |
| colour | Número | Cor da água analisada. | Valor mínimo: 0. Normalmente expresso em  `mg/l PtCo`. |
| colonyCount22C | Número | Número de colónias determinado à temperatura de 22 °C. | Valor mínimo: 0. Normalmente expresso em  `N/ml a 22ºC`. |
| colonyCount36C | Número | Número de colónias determinado à temperatura de 36 °C. | Valor mínimo: 0. Normalmente expresso em  `N/ml a 36ºC`. |
| Ca | Número | Cálcio. Concentração de cálcio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l Ca`. |
| clostridiumPerfringens | Número | Concentração de *Clostridium perfringens* na amostra de água. | Valor mínimo: 0. Normalmente expresso em  número de bactérias por 100 ml (`N/100ml`). |
| totalHardness | Número | Dureza total da água, expressa em carbonato de cálcio. | Valor mínimo: 0. Normalmente expresso em  `mg/l CaCO3`. |
| indicativeDose | Número | Dose indicativa associada à água analisada. | Valor mínimo: 0. Normalmente expresso em  `mSv`.  |
| grossAlphaActivity | Número | Atividade alfa total medida na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `Bq/l`.  |
| grossBetaActivity | Número | Atividade beta total medida na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `Bq/l`.  |
| Po210 | Número | Polónio-210. Atividade do polónio-210 na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `Bq/l`. |
| Ra226 | Número | Rádio-226. Atividade do rádio-226 na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `Bq/l`. |
| U234 | Número | Urânio-234. Atividade do urânio-234 na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `Bq/l`. |
| U238 | Número | Urânio-238. Atividade do urânio-238 na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `Bq/l`. |
| radon | Número | Atividade de radão presente na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `Bq/l`. |
| Mg | Número | Magnésio. Concentração de magnésio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l Mg`. |
| Mn | Número | Manganês. Concentração de manganês na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l Mn`. |
| oxidability | Número | Oxidabilidade da água, expressa em quantidade equivalente de oxigénio. | Valor mínimo: 0. Normalmente expresso em  `mg/l O2`. |
| K | Número | Potássio. Concentração de potássio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l K`. |
| Sb | Número | Antimónio. Concentração de antimónio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l Sb`.  |
| benzene | Número | Concentração de benzeno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| benzoAPyrene | Número | Concentração de benzo(a)pireno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| bromate | Número | Concentração de bromatos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l BrO3`.  |
| totalOrganicCarbon | Número | Carbono orgânico total, COT, presente na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l C`. |
| cyanides | Número | Concentração de cianetos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l CN`.  |
| chlorite | Número | Concentração de cloritos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. O valor paramétrico depende do sistema de desinfeção existente. |
| chlorate | Número | Concentração de cloratos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. O valor paramétrico depende do sistema de desinfeção existente. |
| dichloroethane1_2 | Número | Concentração de 1,2-dicloroetano na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| totalPAH | Número | Concentração total de hidrocarbonetos aromáticos policíclicos, HAP, na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| benzoBFluoranthene | Número | Concentração de benzo(b)fluoranteno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| benzoKFluoranthene | Número | Concentração de benzo(k)fluoranteno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| benzoGhiPerylene | Número | Concentração de benzo(ghi)perileno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| indeno123CdPyrene | Número | Concentração de indeno(1,2,3-cd)pireno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| totalPesticides | Número | Concentração total de pesticidas na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| bentazone | Número | Concentração de bentazona na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| chlorpyrifos | Número | Concentração de clorpirifos na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| dimethoate | Número | Concentração de dimetoato na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| diuron | Número | Concentração de diurão na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| imidacloprid | Número | Concentração de imidaclopride na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| sMetolachlor | Número | Concentração de S-metolacloro na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| MCPA | Número | Concentração de MCPA na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| dimethenamidP | Número | Concentração de dimetenamida-P na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| metribuzin | Número | Concentração de metribuzina na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| legionella | Número | Concentração de Legionella na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `UFC/l` (Unidades Formadoras de Colónias por litro).  |
| terbuthylazine | Número | Concentração de terbutilazina na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| desethylTerbuthylazine | Número | Concentração de desetilterbutilazina na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| omethoate | Número | Concentração de ometoato na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| metalaxyl | Número | Concentração de metalaxil na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| tebuconazole | Número | Concentração de tebuconazol na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| glyphosate | Número | Concentração de glifosato na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| AMPA | Número | Concentração de AMPA na amostra de água. | Valor mínimo: 0. Normalmente expresso em `µg/l`. |
| Na | Número | Sódio. Concentração de sódio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `mg/l Na`.  |
| tetrachloroetheneAndTrichloroethene | Número | Concentração total de tetracloroeteno e tricloroeteno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`.  |
| tetrachloroethene | Número | Concentração de tetracloroeteno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| trichloroethene | Número | Concentração de tricloroeteno na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| totalTrihalomethanes | Número | Concentração total de trihalometanos, THM, na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| chloroform | Número | Concentração de clorofórmio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| bromoform | Número | Concentração de bromofórmio na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| bromodichloromethane | Número | Concentração de bromodiclorometano na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| dibromochloromethane | Número | Concentração de dibromoclorometano na amostra de água. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| refPointOfInterest | URI | Referência a um ponto de interesse associado à observação. | Relação NGSI-LD para o ponto de interesse. |
| salinity | Número | Quantidade de sais dissolvidos na água. | Valor mínimo: 0. |
| seeAlso | URI ou Array de URI | URI, ou lista de URI, que apontam para recursos adicionais sobre o elemento. | Pode ser um único URI ou uma lista não vazia de URI. |
| source | String | Fonte original dos dados da entidade, expressa como URL. Recomenda-se o nome de domínio totalmente qualificado do fornecedor ou o URL do objeto de origem. | Deve identificar a origem por URL. |
| sulphate | Número | Concentração de sulfatos. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| sulphite | Número | Concentração de sulfitos. | Valor mínimo: 0. Normalmente expresso em  `mg/l`. |
| tds | Número | Sólidos dissolvidos totais. | Valor mínimo: 0. |
| temperature | Número | Temperatura. | — |
| total-surfactants | Número | Concentração total de tensioativos. | Valor mínimo: 0. Normalmente expresso em  `µg/l`. |
| tss | Número | Sólidos suspensos totais. | Valor mínimo: 0. |
| turbidity | Número | Quantidade de luz dispersa pelas partículas presentes na coluna de água. | Valor mínimo: 0. |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address`
- `dateObserved`
- `location`

Têm de ser incluídas os valores de *todos* os parâmetros de decorrem de imposições legais [Decreto-Lei n.º 69/2023, de 21 de agosto](https://diariodarepublica.pt/dr/detalhe/decreto-lei/69-2023-220113533) e [Diretiva (UE) 2020/2184 do Parlamento Europeu e do Conselho de 16 de dezembro de 2020 relativa à qualidade da água destinada ao consumo humano](https://eur-lex.europa.eu/eli/dir/2020/2184/oj?locale=pt#ntr28-L_2020435PT.01000101-E0028), podendo estes variar dependendo do tipo de água a analisar e do usufruto que a água terá.

## Notas

Para alguns campos é necessária metainformação que permita interpretar corretamente os valores transmitidos. Neste perfil, para a propriedade `location`, deve ser acrescentado o campo de metainformação `coordinateSystem`, cujo valor identifica o sistema de referência de coordenadas através de um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo, `"coordinateSystem": "EPSG:4258"`. Consideram-se ainda, para as medidas onde haja imposição legal, a metainformação `minimumValue` e `maximumValue`, ambas cadeias de caracteres que permitem indicar valores limite nesta amostra, `parametricValue`que indica o valor de referência, `originalUnit`que inclui informação sobre as unidades relativas ao valor paramétrico, `analysesAboveParametricValue` que indica quantas análises estão acima do valor paramétrico, `analysesPlanned`e `analysesPerformed`, que indicam desvios nas análises e `measurementTemperature` para indicar qual a temperatura em que foi feita a medição.

Nos atributos, incluindo a respetiva metainformação, que não correspondam a percentagens nem a valores adimensionais entre 0 e 1, o campo `unitCode` deve indicar a unidade de medida. Este campo é expresso através dos códigos comuns [UN/CEFACT](http://wiki.goodrelations-vocabulary.org/Documentation/UN/CEFACT_Common_Codes), com um máximo de três carateres.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, pelo que podem surgir alterações que devem ser incorporadas nos sistemas em produção. O modelo permite ainda a inclusão de atributos e de metainformação específicos de determinados verticais. Contudo, esses elementos podem ser ignorados na integração de dados provenientes de várias entidades, sendo utilizados como referência comum os atributos aqui descritos.
