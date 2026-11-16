# 🌍 Agente de Viagens Inteligente: Clima e Cotação de Moedas com Ollama

Este projeto é um notebook desenvolvido para o **Google Colab** que demonstra como criar um Agente de Inteligência Artificial autônomo. O agente utiliza o modelo **Llama 3.2 (3B)** rodando localmente via **Ollama** e é capaz de acessar a internet em tempo real através de *Function Calling* (Chamada de Ferramentas) para consultar o clima e taxas de câmbio.

## 🚀 Funcionalidades

* **Execução Local de LLM:** Utiliza o Ollama para rodar o modelo `llama3.2:3b` diretamente no ambiente do Colab.
* **Function Calling (Uso de Ferramentas):** O LLM decide autonomamente quando precisa buscar informações externas para responder à pergunta do usuário.
* **Consulta de Clima em Tempo Real:** Integração com a API `wttr.in` para buscar a temperatura atual de qualquer cidade.
* **Cotação de Moedas em Tempo Real:** Integração com a `AwesomeAPI` para buscar taxas de câmbio atualizadas (ex: BRL para JPY, USD para EUR).
* **Compatibilidade com OpenAI SDK:** O código utiliza a biblioteca oficial da OpenAI em Python, mas redireciona as chamadas para o servidor local do Ollama (`http://localhost:11434/v1`).

## 🛠️ Tecnologias Utilizadas

* [Python](https://www.python.org/)
* [Ollama](https://ollama.com/) (Servidor de LLMs locais)
* [Llama 3.2:3b](https://ollama.com/library/llama3.2) (Modelo de linguagem da Meta)
* [OpenAI Python SDK](https://github.com/openai/openai-python) (Como cliente REST para o Ollama)
* **APIs Externas:** `wttr.in` (Clima) e `AwesomeAPI` (Finanças)

## ⚙️ Como executar no Google Colab

1. **Abra um novo notebook** no [Google Colab]
2. **Copie e cole** o código fornecido em uma célula.
3. Certifique-se de que o ambiente de execução tem acesso à internet (padrão do Colab) e, opcionalmente, ative a aceleração por GPU (T4 GPU) em *Ambiente de Execução > Alterar tipo de ambiente de execução* para que o modelo responda mais rápido.
4. **Execute a célula**.

### O que o script faz por baixo dos panos:
1. Instala dependências do sistema e do Python (`zstd`, `ollama`, `openai`, `requests`).
2. Inicia o servidor do Ollama em segundo plano no Colab.
3. Baixa o modelo `llama3.2:3b` (isso pode levar alguns instantes na primeira execução).
4. Configura as funções Python e os "schemas" de ferramentas que o LLM precisa entender.
5. Inicia a conversa com a pergunta do usuário e processa as chamadas de API geradas pelo modelo.

## 💬 Exemplo de Uso

```python
print(agente_local("Vou sair do Brasil e ir para a Japão, qual o a temperatura do japão em dezembro?"))
