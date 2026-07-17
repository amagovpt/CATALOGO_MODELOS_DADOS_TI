## Perguntas Frequentes (FAQ)

**Versão:** 1.5
**Data da última atualização:** 2 de julho de 2026

Este documento reúne um conjunto de perguntas frequentes com o objetivo de apoiar as entidades fornecedoras de dados na correta implementação dos modelos de dados e respetivas instruções.

Após a partilha dos modelos, têm sido identificadas algumas dificuldades e inconsistências na sua aplicação. Nesse sentido, esta FAQ apresenta exemplos práticos e esclarecimentos sobre situações comuns, com o intuito de promover a uniformização, qualidade e interoperabilidade dos dados.

Recomenda-se a leitura atenta deste documento antes da submissão dos dados, de forma a garantir o cumprimento dos requisitos definidos e evitar retrabalho.

Para qualquer questão adicional, por favor entre em contacto com a equipa de suporte.

## 1. Como atribuir os identificadores únicos

<details>
  <summary>Como podemos garantir que os identificadores (campos ID) criados por diferentes entidades são únicos, sem necessidade de coordenação central?</summary>

**Resposta**
Para garantir a unicidade de identificadores recomendamos a utilização de **URN (Uniform Resource Names)** com uma estrutura hierárquica.

**Estrutura recomendada**

```json
urn:<organização>:<tipo-do-recurso>:<identificador-local>
```

**Exemplos ilustrativos:**

```json
urn:apa:FloodMonitoring:Mondego:2025-02-11T17:00:00
urn:ipma:WeatherStation:Lisboa:1234567
urn:epal:WaterQuality:Alcantara:20250211-001
urn:cmpeae:WaterConsumptionObserved:Local33:2025-02-18T08:00:00
```

**Componentes do identificador**

1. **Prefixo URN**: começa sempre com `urn:`
2. **Nome da organização**: sigla ou código único da entidade (ex: `apa`, `ipma`, `epal`)
3. **Tipo de recurso**: tipo do modelo (ex: `FloodMonitoring`, `WeatherStation`)
4. **Identificador local**: sequência de valores definida e mantida pela própria entidade, podendo incluir:
   - Localização geográfica
   - Timestamp
   - Sequências numéricas
   - Combinação de vários elementos

</details>

## 2. Sobre os metadados

<details>
  <summary>É suficiente os metadados estarem registados no portal dados.gov?</summary>

**Resposta**
Não. O registo dos metadados no portal dados.gov não é suficiente, uma vez que existem propriedades indisponíveis ou não totalmente compatíveis com o modelo de metadados definido.
Destacam-se, por exemplo:

- *Geographical coverage*: não pode ser representado apenas como uma lista de locais (nomes); 
- *Temporal coverage*: deve corresponder a um período, com as datas de início e fim devidamente preenchidas.

</details>

<details>
  <summary>Os metadados têm de estar disponíveis através de API?</summary>

**Resposta**
Sim. Embora o termo "dados" seja utilizado num sentido lato, considera-se que inclui toda a informação necessária para compreender o contexto e os valores disponibilizados, incluindo os metadados.

De acordo com o Aviso de Abertura de Concurso n.º 04/C19-i08/2024, ponto 3.2(b) ("Condições específicas de acesso à candidatura"), os dados a disponibilizar devem estar acessíveis através de API e também disponíveis para descarregamento em bloco.

Consequentemente, os metadados devem igualmente ser disponibilizados através de API e incluídos nos mecanismos de descarregamento em bloco, garantindo a sua consistência com os conjuntos de dados disponibilizados.

</details>

## 3. Especificações técnicas de integração e os modelos de dados

<details>
  <summary>O documento de Especificações Técnicas para Integração de Sistemas define os modelos de dados que as entidades têm de adotar?</summary>

**Resposta**
Não. O documento de [Especificações Técnicas para Integração de Sistemas](https://doc.territoriosinteligentes.gov.pt/api/assets/c077f7b0-aa6c-4793-a6b7-3fb8fa626e88)  aplica-se exclusivamente às interligações entre sistemas, definindo os protocolos, formatos de mensagens e requisitos de segurança a cumprir no âmbito de integrações programáticas entre plataformas e o integrador de dados da ARTE.

Os [modelos de dados](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/), por sua vez, dizem respeito à estrutura e à semântica da informação produzida e disponibilizada por cada entidade. A sua adoção é obrigatória e independente da existência de uma integração de sistemas.
</details>

## 4. Integração de mapas (WMS) vs. disponibilização de dados geográficos nos modelos de dados

<details>
  <summary>O documento de Especificações Técnicas para Integração de Sistemas refere o protocolo WMS (Web Map Service) para sistemas que disponibilizam informação cartográfica. É necessário disponibilizar dados geográficos através de WMS?</summary>

**Resposta**
Não. O **WMS (Web Map Service)** é um protocolo de integração de sistemas utilizado para disponibilizar representações visuais de mapas (imagens), sendo tipicamente aplicado em integrações entre sistemas cartográficos e outras plataformas (por exemplo, *mapas base*).

A disponibilização de dados geográficos estruturados é uma questão distinta, relacionada com o formato e a forma como a informação de localização é representada nos modelos de dados.

Nesse contexto, a representação dos dados geográficos depende do modelo adotado:

* Nos **Smart Data Models FIWARE**, em formato **NGSI-LD** (utilizados na maioria dos modelos deste repositório), os campos de localização são representados como `GeoProperty`, contendo geometrias em formato **GeoJSON** (por exemplo, `Point`, `Polygon`, `LineString`). Este é o caso da generalidade dos modelos, como `ParkingAccess`, `OffStreetParking`, `WaterNetworkMonitoring`, entre outros;
* Alguns modelos podem ainda referenciar sistemas de coordenadas específicos (por exemplo, `EPSG:4258`, utilizado na Carta Administrativa de Portugal).

Em qualquer dos casos, o formato subjacente para a representação da informação geográfica é o **GeoJSON**, podendo variar o tipo de geometria conforme o modelo.

Assim, uma entidade que disponibilize dados com componente geográfica através de uma API REST deve garantir que os campos espaciais seguem o formato definido no modelo de dados adotado.
</details>

## 5. Sobre API e a disponibilização de dados em lote

<details>
  <summary>O catálogo nacional de modelo de dados não indica qual o modelo a seguir para conjuntos de dados (ex.: respostas de APIs). Qual é a abordagem recomendada?</summary>

**Resposta**
A maioria dos modelos do [Catálogo Nacional de Modelos de Dados (CNMD)](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/) é serializada em [JSON-LD](https://www.w3.org/TR/json-ld11/), de acordo com o standard [NGSI-LD](https://www.etsi.org/deliver/etsi_gr/CIM/001_099/008/01.03.01_60/gr_CIM008v010301p.pdf). O objetivo é permitir a partilha de informação de contexto (tempo, espaço e relações) num cenário de interoperabilidade entre sistemas.

Neste contexto, quando se pretende disponibilizar um conjunto de dados (por exemplo, como resposta a uma API), a abordagem recomendada é a seguinte:

* A resposta deve ser estruturada como um **array**;
* Cada elemento do array deve corresponder a uma entidade individual;
* Cada entidade deve estar em conformidade com o modelo de dados aplicável ao domínio em causa.

**Exemplo (simplificado):**

```json
[
  { "id": "urn:example:1", "type": "EntityType", "name": {"type": "Property", "value": "ValueName"} },
  { "id": "urn:apa:AirQualityStation-3072", "type": "PointOfInterest", "name": {"type": "Property", "value": "Entrecampos"} }
]
```
</details>

<details>
  <summary>Os dados têm de ser disponibilizados exclusivamente em JSON-LD (NGSI-LD)?</summary>

**Resposta**
Não. Os dados podem ser disponibilizados em diferentes formatos, desde que sejam semanticamente equivalentes.

No entanto, pelo menos um dos formatos disponibilizados deve estar em conformidade com o modelo de dados definido no Catálogo Nacional de Modelos de Dados (CNMD). Quando o exemplo é apresentado em **JSON-LD**, seguindo o standard **NGSI-LD**, esse deve ser o formato base e disponibilizado por omissão.

Outros formatos (por exemplo, JSON simplificado) podem ser disponibilizados adicionalmente, desde que:

* sejam semanticamente equivalentes ao modelo original;
* não impliquem perda de informação relevante;
* sejam explicitamente solicitados através de parâmetros na API.

Desta forma, garante-se a interoperabilidade com o ecossistema, sem limitar a flexibilidade na utilização dos dados.
</details>

<details>
  <summary>Os exemplos disponíveis no Catálogo Nacional de Modelo de Dados têm extensão JSON. Quer dizer que o seu conteúdo pode ser JSON?</summary>

**Resposta**
Não. Embora os exemplos do [Catálogo Nacional de Modelo de Dados](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/) tenham essa extensão, ela não deve ser usada como indicadora do conteúdo, que é o JSON-LD (ver questão anterior). Note-se que a extensão não é relevante quando os dados são disponibilizados por API. Nessa situação, a resposta deve ter, entre outros, o cabeçalho HTTP ```content-type``` o valor ```application/ld+json```.

</details>

## 6. Sobre as propriedades obrigatórias

<details>
  <summary>O modelo de dados que quero usar e que está disponível no Catálogo Nacional de Modelo de Dados indica um conjunto de propriedades obrigatórias. Tenho sempre de as incluir?</summary>

**Resposta**
Sim. No [Catálogo Nacional de Modelo de Dados](https://github.com/amagovpt/CATALOGO_MODELOS_DADOS_TI/), se as propriedades foram consideradas obrigatórias, então devem estar *sempre presentes* quando os dados são disponibilizados, com um valor admissível no domínio da propriedade.

</details>

<details>
  <summary>Para uma propriedade obrigatória do tipo String, posso utilizar uma sequência vazia ("")?</summary>

**Resposta**
Não. Uma sequência vazia não é um valor admissível para uma propriedade obrigatória e não cumpre os requisitos de qualidade de dados.

Uma propriedade obrigatória deve conter um valor válido, significativo e não ambíguo.

**Exemplos de valores inválidos:**

```json id="e7k2lm"
{
  "name": null,
  "type": "",
  "name": " ",
  "name": "                 "
}
```
</details>

<details>
  <summary>Como proceder quando uma propriedade obrigatória não tem valor disponível?</summary>

**Resposta**
Se uma propriedade está definida como obrigatória, é porque foi considerado que existe (ou deve existir) um valor válido para a mesma.

Caso, numa determinada entidade, não exista valor disponível, isso indica uma lacuna na origem dos dados que deve ser corrigida. O incentivo do concurso deve ser utilizado precisamente para melhorar a qualidade e completude da informação na fonte.

Não é admissível atribuir valores inválidos, artificiais ou inconsistentes apenas para cumprir formalmente o modelo de dados.

**O que fazer na prática**

- Validar se a ausência de valor resulta de um erro no processo de recolha ou integração de dados;
- Corrigir o problema na origem, garantindo que a informação passa a ser registada;
- Confirmar se o modelo de dados está corretamente interpretado;
- Em caso de dúvida, contactar a equipa responsável pelo modelo antes de submeter os dados.

**Exemplos de valores inválidos:**

```json 
{
  "location": null,
  "location": {},
  "dateObserved": "",
  "dateObserved": "-",
  "dateObserved": null
}
```

</details>

## 7. Sobre as propriedades em geral

<details>
  <summary>Como proceder quando uma propriedade não tem valor disponível?</summary>

**Resposta**
Se uma propriedade de um modelo não tem valor, então deve ser omitida do modelo de dados, mesmo que essa falta de valor seja esporádica. Ou seja, todas as propriedades presentes nos modelos de dados têm de ter um valor válido.

Excecionalmente, e apenas para os modelos onde existam intervalos de datas (data de início e data de fim), se permite que propriedade que representa a data de fim esteja presente no modelo com o valor null.

Não é admissível atribuir valores inválidos, artificiais ou inconsistentes apenas para cumprir formalmente o modelo de dados.
</details>

## 8. Sobre Modelos em geral

<details>
  <summary>Não encontro um modelo adequado aos meus dados. O que devo fazer?</summary>

**Resposta:** Se não existir um modelo adequado aos dados que pretende disponibilizar, pode reportar essa necessidade à **Equipa dos Territórios Inteligentes** através do email [territorios.inteligentes@arte.gov.pt](mailto:territorios.inteligentes@arte.gov.pt).
</details>

### Histórico de alterações

* **v1.5 (2026-07-02)** – Adicionada FAQ sobre extensão JSON dos ficheiros exemplo
* **v1.4 (2026-06-22)** – Adicionada FAQ sobre modelos em falta
* **v1.3 (2026-05-19)** – Adicionada FAQ sobre propriedades optativas para as quais não se tem valor
* **v1.2 (2026-04-07)** – Adicionadas FAQ sobre propriedades obrigatórias, API e reestruturação do documento
* **v1.1 (2026-03-16)** – Adicionadas FAQ sobre especificações técnicas de integração e dados geográficos
* **v1.0 (2026-02-12)** – Versão inicial
