# Descrição Geral
Os modelos de dados a seguir para representar **Cadastro de rede de saneamento** são baseado nos requisitos da diretiva INSPIRE e nos conjuntos de dados de alto valor (HVD). Estes modelos utilizam o formato NGSI-LD, sendo é compatível com [ETSI GS CIM 009 V1.5.1, Context Information Management (CIM)-NGSI-LD API](https://www.etsi.org/deliver/etsi_gs/CIM/001_099/009/01.05.01_60/gs_cim009v010501p.pdf) da [ETSI](https://www.etsi.org/) e com os requisitos de dados de alto valor da UE.
Nas anotações é possível encontrar exemplos de utilização destes modelos.

Aqui descreve-se o modelo `Manhole`, que representa uma caixa de visita compatível com o [Smart data models](https://github.com/smart-data-models), que apresenta um conjunto vasto de propriedades para permitir uma melhor compatibilidade com INSPIRE e HVD.



## Propriedades do Modelo

| Propriedade | Tipo | Descrição | Nota |
|-------------|------|-----------|------|
| id | String | Identificador único da entidade | Formato URN (ex.: urn:ngsi-ld:Manhole:MNHL123) |
| type | String | Tipo da entidade | Deve ser sempre "Manhole" |
| dateCreated | Property:DateTime | Data e hora de criação do registo | Formato ISO 8601 |
| dateModified | Property:DateTime | Data e hora da última modificação | Formato ISO 8601 |
| source | Property:Text | Fonte original dos dados | URL ou descrição da origem dos dados |
| name | Property:Text | Nome da caixa de visita | -- |
| alternateName | Property:Text | Nome alternativo | Designação alternativa, normalmente mais curta |
| description | Property:Text | Descrição da câmara de visita | --|
| location | GeoProperty | Localização geográfica | Coordenadas no formato GeoJSON Point |
| address | Property:Object | Endereço da localização | Estrutura de endereço com rua, localidade, país, etc. |
| networkType                  | Propriedade     | Descrição do tipo de rede de sanemaento | Enumerado: <br>- `sewer`<br>- `stormwater`<br>- `combined` |
| refNetwork                | Relação         | Indentificador da rede a qu o componente pertence. | Normalmente um URN.|
| areaServed | Property:Text | Área geográfica servida | Descrição da área que esta câmara de visita serve |
| status | Property:Text | Estado operacional atual |  Enumerado: <br>- `operational`  <br>- `planned`  <br>- `underConstruction`  <br>- `underMaintenance`  <br>- `outOfService`  <br>- `abandoned` |
| category | Property:Array | Categoria da câmara de visita | Ex.: sanitary, storm, combined |
| dimension | Property:Object | Dimensões físicas | Objeto com diâmetro, profundidade e diâmetro da tampa, normalmente expresso em metros (MTR)|
| depth | Property:Number | Profundidade da câmara | Medida em metros (MTR) |
| material | Property:Text | Material de construção | Ex.: betão, tijolo, plástico |
| coverMaterial | Property:Text | Material da tampa | Ex.: ferro fundido, betão, compósito |
| coverShape | Property:Text | Forma da tampa | Ex.: circular, retangular |
| accessType | Property:Text | Tipo de acesso | Ex.: bloqueável, não bloqueável |
| manufacturer | Property:Text | Fabricante | Nome do fabricante |
| manufacturedAt | Property:DateTime | Data de fabrico | Data em que foi fabricada |
| installationDate | Property:DateTime | Data de instalação | Data em que foi instalada no local |
| lastInspection | Property:DateTime | Última inspeção | Data e hora da última inspeção realizada |
| maintenanceSchedule       | Propriedade     | Frequência de manutenção | Enumerado:  <br>- `annual` <br>- `biannual` <br>- `quarterly` <br>- `monthly` |
| connectedTo | Relationship:Array | Ligações | Lista de condutas ou outras câmaras conectadas |
| maintenanceHistory | Property:Array | Histórico de manutenção | Lista de atividades de manutenção realizadas |
| owner | Relationship:Array | Proprietário | Entidade proprietária da câmara de visita |
| version          | Propriedade      | Versão do modelo | Exemplo: 1.3 |
| updateFrequency  | Propriedade      |  Frequência de atualização  |Exemplo: mensal |
| dataProvider     | Propriedade      | Provedor de dados | Exemplo:  "CMLisboa" |
| datasetResponsibleParty | Propriedade | Responsável pelo conjunto de dados | Exemplo: "CMLisboa" |
| license         | Propriedade      |Licença dos dados | [Licença Creative Commons](https://creativecommons.org/licenses/by/4.0/) | 


Os atributos obrigatórios são:

- `id`
- `name`
- `type`
- `location`

