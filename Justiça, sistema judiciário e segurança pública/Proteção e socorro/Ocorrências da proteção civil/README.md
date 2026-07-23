# Descrição

O modelo de dados a seguir para representar **Ocorrências da proteção civil**
é o `EmergencyIncident` inspirado no [FIWARE Smart Data Models](https://github.com/smart-data-models/).
Este modelo utiliza o formato NGSI-LD, sendo compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM) - NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf), da [ETSI](https://www.etsi.org/).
Nas anotações é possível encontrar um exemplo deste modelo, e de outros relacionados, ilustrando o seu uso no âmbito da [ENTI](https://www.ama.gov.pt/web/agencia-para-a-modernizacao-administrativa/estrategia-nacional-de-territorios-inteligentes). Embora genérico, o modelo é compatível a Norma Operacional Permanente (NOP) 3101, na sua redação de 2019.

## Propriedades

Na tabela abaixo são apresentadas as propriedades presentes no modelo de dados.

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|-------------------------|
| id | URI | Identificador único da entidade | Ver [Regra para geração de identificadores únicos](/FAQ.md). |
| type | String | Tipo de entidade | Valor constante igual a `EmergencyIncident`|
| address    | Object          | Morada associada ao ponto de medição | Inclui país, localidade, rua, código postal. Modelo: [ https://schema.org/address]( https://schema.org/address)  |
| address.addressCountry | String    | Nome do país | Modelo: [https://schema.org/addressCountry](https://schema.org/addressCountry)      |
| address.addressLocality| String    | Localidade em que se situa o endereço da rua e que se encontra na região. Normalmente a freguesia para Portugal.         | Modelo: [https://schema.org/addressLocality](https://schema.org/addressLocality)     |
| address.addressRegion  | String    | Região em que se situa a localidade e que se encontra no país | Modelo: [https://schema.org/addressRegion](https://schema.org/addressRegion)
| address.addressMunicipality       | String    | Concelho é um tipo de divisão administrativa que, em alguns países, é gerida pelo governo local |  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| address.addressDistrict       | String    | Distrito é um tipo de divisão administrativa que, em alguns países, é gerida pelo governo local |  Modelo: [https://schema.org/Text](https://schema.org/Text)    |
| address.streetAddress  | String    | Endereço da rua         | Modelo: [https://schema.org/streetAddress](https://schema.org/streetAddress)       |
| areaServed        | String | Área afetada pela ocorrência  | A usar quando não é possível atribuir um morada à ocorrência. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| dateCreated        | DateTime | Data e hora da criação  |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| dateModified        | DateTime | Registo de data e hora da última modificação da entidade |  Este será normalmente atribuído pela plataforma de armazenamento. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| description         | String          | Descrição textual da ocorrência | Modelo: [https://schema.org/Text](https://schema.org/Text) |
| coordinatingAgencies | Array  | Entidades envolvidas na gestão da ocorrência    |  Lista de nomes das entidades. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| endDate        | DateTime | Data e hora do fecho administrativo da ocorrência  | Se não existir valor para este atributo, o mesmo deve ser omitido. De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| incidentPriority    | String | Importância da ocorrência         |   Enumerado: <br>- Reduzida,<br>- Moderada, <br>- Elevada. <br> Modelo: [https://schema.org/Text](https://schema.org/Text) |
| incidentType        | String | Tipo de incidente |  De acordo com a NOP 3101. Enumerado:<br> Cheia,<br>- Vento forte,<br>- Sismo,<br>- Nevão,<br>- Onda de calor,<br>- Onda de frio,<br>- Seca,<br>- Inundação por galgamento costeiro,<br>- Erosão costeira,<br>- Colapso de cavidades subterrâneas,<br>- Erupção vulcânica,<br>- Queda de meteorito ,<br>- Enxurrada ou aluvião,<br>- Incêndio em edifícios habitacionais,<br>- Incêndio em estacionamentos,<br>- Incêndio em edifícios administrativos,<br>- Incêndio em edifícios escolares,<br>- Incêndio em edifícios hospitalares e lares de idosos,<br>- Incêndio em recintos de espetáculos e reuniões públicas,<br>- Incêndio em edifícios hoteleiros e de restauração,<br>- Incêndio em edifícios comerciais e gares de transporte,<br>- Incêndio em edifícios e recintos desportivos e de lazer,<br>- Incêndio em museus e galerias de arte,<br>- Incêndio em bibliotecas e arquivos,<br>- Incêndio em edifícios prisionais, militares, ou de força de segurança,<br>- Incêndio em edifícios e recintos industriais, oficinas e armazéns,<br>- Incêndio em edifícios degradados ou devolutos,<br>- Incêndio em equipamentos ou produtos,<br>- Incêndio em transporte rodoviário,<br>- Incêndio em transporte aéreo,<br>- Incêndio em transporte ferroviário,<br>- Incêndio em transporte aquático,<br>- Atropelamento rodoviário,<br>- Acidente rodoviário,<br>- Acidente com tratores e máquinas,<br>- Acidente aéreo,<br>- Atropelamento ferroviário,<br>- Acidente Ferróviário,<br>- Acidente aquático,<br>- Acidente com transporte suspenso,<br>- Acidente Radiológico,<br>- Acidente Químico,<br>- Acidente biológico,<br>- Fuga de gás,<br>- Queda de satélite,<br>- Incêndio rural,<br>- Consolidação de rescaldo de incêndio rural,<br>- Gestão de combustível,<br>- Queima,<br>- Incêndio em Detritos,<br>- Queda de árvore,<br>- Desabamento de estruturas edificadas,<br>- Queda de elementos de construção,<br>- Deslizamento de terras,<br>- Inundação de estruturas,<br>- Desentupimento / Tamponamento,<br>- Queda de redes de eletricidade  ,<br>- Avaria na rede de abastecimento de água,<br>- Avaria na rede de abastecimento de gás,<br>- Avaria em oleoduto ou gasoduto,<br>- Queda de estruturas,<br>- Colapso de galerias e cavidades artificiais,<br>- Rutura de barragem,<br>- Explosão,<br>- Limpeza de via ou Sinalização de Perigo,<br>- Abastecimento de Água,<br>- Evacuação de Pessoas e Bens,<br>- Apoio à Busca pessoas,<br>- Resgate de pessoas,<br>- Resgate de animais,<br>- Prevenção a queimadas,<br>- Escoramento ou remoção de elementos em perigo de queda,<br>- Operação nacional de proteção e socorro,<br>- Missão internacional ,<br>- Incêndio Parques Fotovoltaicos e Eólicos,<br>- Apoio à Estabilização de Emergência pós Incêndio Rural,<br>- Acidente em Escadas ou Tapetes Rolantes,<br>- Poluição Aquática,<br>- Poluição Terrestre,<br>- Poluição Atmosférica,<br>- Queda de redes de comunicações,<br>- Controlo de Pragas e Espécies Invasoras,<br>- Prevenção a aterragem de aeronaves. <br>  Modelo: [https://schema.org/Text](https://schema.org/Text) |
| incidentCode | Integer | Código da ocorrência | Código para o tipo de ocorrência, segundo a NOP 3101. Modelo: [https://schema.org/Integer](https://schema.org/Integer) |  
| internalId | String | Identificador interno | Identificador usado no sistema interno da entidade, que permite aceder posteriormente a informação extra ou possibilita o enriquecimento dos dados em processos de transformação. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| location | GeoJSON | Referência Geojson para o objecto hidrográfico |  Valores possíveis: 'Point', 'LineString', 'Polygon', 'MultiPoint', 'MultiLineString' ou 'MultiPolygon'  |
| reportedBy          | String | Entidade que relatou o incidente|  Enumerado: <br>- 112,<br>- ANEPC,<br>- Bombeiros,<br>- Câmara Municipal,<br>- Posto de vigia,<br>- Sistema automático,<br>- Cidadão,<br>- Outro/Desconhecido. <br> Modelo: [https://schema.org/Text](https://schema.org/Text)  |
| resourcesDeployed   | Array  | Recursos utilizados na resposta ao incidente  |  Lista de objetos com definição do tipo e quantidade. O tipo é definido na propriedade `resourceType` e pode tomar os valores: <br>- Meios Aéreos, <br>- Meios Terrestes, <br>- Meios Aquáticos , <br>- Operacionais. A quantidade é definida pela propriedade inteira `quantity`.  |
| severity | String | Nível de gravidade do incidente | Enumerado: <br>- Baixo,<br>- Médio,<br>-  Alto. Modelo: [https://schema.org/Text](https://schema.org/Text) |
| startDate        | DateTime | Data e hora do início da ocorrência  |  De acordo com a norma  [ISO 8601-1:2019](https://www.iso.org/standard/70907.html). Modelo: [https://schema.org/DateTime](https://schema.org/DateTime)  |
| status   | String | Estado atual do incidente       | Enumerado: <br>- Despacho, <br>- Em curso, <br>- Em resolução, <br>- Vigilância, <br>- Encerrado.  Modelo: [https://schema.org/Text](https://schema.org/Text) |

## Propriedades obrigatórias

Os atributos obrigatórios são:

- `id`
- `type`
- `address
- `dateCreated`
- `dateModified`
- `startDate`
- `location`
- `status`
- `incidentType`
- `incidentCode`
- `resourcesDeployed`

## Notas

Para alguns dos campos é requerida metainformação. A compatibilidade com a especificação acima é garantida, mas possibilita uma melhor interpretação dos valores incluídos nos campos. Neste modelo, para a propriedade `location` é necessário adicionar como metainformação o campo `coordinateSystem`, tendo este valor um código [EPSG](https://epsg.org/crs_4258/ETRS89.html), por exemplo `"coordinateSystem": "EPSG:4258"`.

A definição do modelo de dados no catálogo nacional de dados é um processo contínuo, podendo surgir alterações ao longo do tempo, que devem de ser incorporadas nos sistemas em produção. Além disso, o modelo permite a inclusão de atributos e de metainformação específica para determinados verticais. No entanto, esses atributos podem ser ignorados quando há integração de dados provenientes de várias entidades, sendo apenas usados os atributos aqui descritos.
