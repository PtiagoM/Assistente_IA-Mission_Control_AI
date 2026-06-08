# Mission Control IA — Prompt and Artificial Intelligence

Sistema inteligente de monitoramento para controle básico de uma missão espacial experimental, com uso de IA local para apoiar a geração, interpretação e análise operacional dos dados da missão.

---

## Informações da entrega

**Nome da missão:** Artemis Deep Scan

**Modelo de IA utilizado:** Llama 3.2 1B via Ollama

**Vídeo de demonstração:** INSERIR LINK DO VÍDEO AQUI

---

## Integrantes

* Caio César Portela França — RM: 573127
* Gustavo Curis de Francisco — RM: 569704
* Tiago Pimentel Muniz — RM: 574148

---

## Visão geral

O **Mission Control IA** é uma central de monitoramento de missão espacial experimental desenvolvida em Python.

O sistema acompanha dados simulados da missão, como temperatura, comunicação, energia, oxigênio e estabilidade operacional. A partir desses dados, ele gera alertas automáticos, classifica riscos e apresenta recomendações para tomada de decisão.

A inteligência artificial é integrada ao sistema por meio do modelo **Llama 3.2 1B**, executado localmente via **Ollama**. A IA atua como uma camada de apoio à interpretação da missão, analisando o contexto operacional e gerando respostas em linguagem natural.

---

## Objetivo do projeto

Desenvolver uma solução com IA integrada capaz de:

* gerar ou apoiar dados simulados de uma missão espacial;
* monitorar parâmetros operacionais da missão;
* identificar situações de alerta ou risco;
* exibir respostas da IA de forma legível;
* apresentar dados organizados em uma interface funcional;
* apoiar decisões operacionais em cenários críticos simulados.

---

## Parâmetros monitorados

O sistema monitora os seguintes parâmetros da missão:

| Parâmetro                | Descrição                                       |
| ------------------------ | ----------------------------------------------- |
| Temperatura interna      | Indica condição térmica dos módulos             |
| Comunicação com a base   | Mede qualidade do sinal e contato com a estação |
| Sistema de energia       | Representa bateria, geração solar e consumo     |
| Suporte de oxigênio      | Indica condição do sistema de suporte à vida    |
| Estabilidade operacional | Mede a condição geral dos módulos da missão     |

---

## Funcionalidades principais

* Configuração inicial da missão.
* Simulação de missão em ciclos de monitoramento.
* Geração de telemetria por regras internas ou com apoio de IA.
* Análise de temperatura, energia, comunicação, oxigênio e estabilidade.
* Geração automática de alertas.
* Classificação de risco operacional.
* Painel visual com cards, tabelas, gráficos e histórico.
* Aba específica para monitoramento da IA.
* Exibição do prompt enviado ao modelo.
* Exibição da resposta bruta da IA.
* Exibição da análise operacional da IA.
* Relatório da missão.
* Fallback determinístico caso a IA não responda.

---

## Uso de Inteligência Artificial

A IA é usada como uma camada de apoio ao sistema de monitoramento.

O modelo configurado é:

```text
llama3.2:1b
```

Executado localmente via:

```text
Ollama
```

A IA é utilizada para:

* apoiar a geração de telemetria simulada;
* interpretar o estado atual da missão;
* analisar dados calculados pelo sistema;
* explicar riscos operacionais;
* sugerir ações em linguagem natural;
* complementar a análise da missão.

A IA não substitui os cálculos determinísticos do sistema. Os motores de risco, energia, eventos e alertas continuam sendo executados em Python.

---

## System prompt da IA

O sistema utiliza um prompt contextualizado para orientar o modelo a agir como um assistente de controle de missão espacial.

Exemplo de contexto utilizado:

```text
Você é um assistente de operação de missão espacial.
Analise apenas os dados calculados pelo sistema.
Não invente telemetria e não altere risco, status, energia ou eventos.
Responda de forma curta, clara e adequada para um operador humano.
```

Esse contexto garante que a IA responda dentro da narrativa da missão e apoie a tomada de decisão sem substituir a lógica principal do sistema.

---

## Funcionamento da IA no sistema

A IA aparece principalmente na aba **AI Mission Advisor**, que apresenta:

* **Logs da IA:** histórico das chamadas ao modelo, tempo de resposta, validação, fallback e erros.
* **Prompt enviado à IA:** mostra o contexto e os dados enviados ao modelo.
* **Resposta bruta da IA:** mostra o retorno real do modelo.
* **Análise operacional da IA:** mostra a resposta organizada para leitura do operador.

Além disso, o Cockpit Geral exibe o status do módulo de IA como uma prioridade operacional, indicando se a IA está operante, em fallback ou indisponível.

---

## Demonstração do sistema

Adicione os prints reais do sistema funcionando na pasta `assets/`.

### Configuração da missão com IA




### Cockpit Geral com alerta operacional




### AI Mission Advisor com prompt e resposta da IA




### Relatório ou cenário crítico da missão

![Relatório da missão](assets/relatorio_missao.png)

---

## Como executar o sistema

### 1. Instalar dependências

Certifique-se de ter o Python instalado.

Depois, na raiz do projeto, instale as dependências necessárias:

```bash
pip install -r requirements.txt
```

Caso o projeto não utilize `requirements.txt`, execute diretamente o arquivo principal.

---

## Configuração da IA com Ollama

O sistema também funciona sem IA, usando regras internas.
Para utilizar a geração/análise com IA local, é necessário instalar o **Ollama** e baixar o modelo usado no projeto.

### 1. Verificar se o Ollama está instalado

No terminal, execute:

```bash
ollama --version
```

Se o terminal retornar a versão instalada, o Ollama está pronto para uso.

### 2. Baixar o modelo

Baixe o modelo utilizado no projeto:

```bash
ollama pull llama3.2:1b
```

Também é possível baixar e testar diretamente com:

```bash
ollama run llama3.2:1b
```

### 3. Iniciar o servidor local do Ollama

Antes de executar o sistema com IA, abra um terminal separado e rode:

```bash
ollama serve
```

Mantenha esse terminal aberto durante o uso do sistema.

Se aparecer uma mensagem informando que a porta já está em uso, provavelmente o Ollama já está rodando em segundo plano.

### 4. Testar o modelo

Em outro terminal, execute:

```bash
ollama run llama3.2:1b
```

Digite uma mensagem simples:

```text
Responda apenas: modelo funcionando
```

Se o modelo responder, a IA está pronta para ser usada no Mission Control IA.

### 5. Aquecer o modelo antes da apresentação

Para reduzir o atraso na primeira resposta, execute:

```bash
ollama run llama3.2:1b "Responda apenas: pronto"
```

---

## Executar o sistema integrado

Com o Ollama ativo, execute:

```bash
python main.py
```

Na tela inicial:

1. Configure a missão.
2. Selecione a fonte de dados com IA, caso deseje usar o modelo local.
3. Clique em **Iniciar missão**.
4. Acompanhe o Cockpit Geral, Telemetria, Energia, Comunicação, Alertas, IA e Relatório.

Se o Ollama não estiver rodando ou o modelo não responder, o sistema continua funcionando com regras internas e fallback determinístico.

---

## Cenários demonstrados

O sistema permite demonstrar:

* missão em operação nominal;
* queda de bateria;
* perda de comunicação;
* aumento de temperatura;
* redução de estabilidade;
* alerta de oxigênio;
* déficit energético;
* análise operacional da IA;
* fallback em caso de falha do modelo.

---

## Tecnologias utilizadas

* Python
* Tkinter
* Ollama
* Llama 3.2 1B
* Estruturas condicionais
* Listas e dicionários
* Funções modulares
* Simulação de dados operacionais
* Modelo de linguagem integrado
* Lógica de alertas e tomada de decisão

---

## Observação

O Mission Control IA é uma solução de simulação e demonstração. Os dados utilizados são simulados e foram estruturados para representar o funcionamento de uma central de monitoramento de missão espacial experimental.

O sistema prioriza clareza operacional, uso de IA integrada e tomada de decisão baseada em dados.

