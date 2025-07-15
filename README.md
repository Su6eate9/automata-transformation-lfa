# 🔄 Conversor de Autômatos Finitos

Uma aplicação web interativa para conversão de autômatos finitos, implementando as transformações clássicas da teoria da computação: **AFe → AFN → AFD**.

## 📋 Índice

- [Visão Geral](#visão-geral)
- [Funcionalidades](#funcionalidades)
- [Como Usar](#como-usar)
- [Algoritmos Implementados](#algoritmos-implementados)
- [Exemplos](#exemplos)
- [Tecnologias](#tecnologias)
- [Estrutura do Projeto](#estrutura-do-projeto)

## 🎯 Visão Geral

Esta aplicação permite a conversão automática entre diferentes tipos de autômatos finitos:

- **AFe (Autômato Finito com ε-transições)** → **AFN (Autômato Finito Não-determinístico)**
- **AFN (Autômato Finito Não-determinístico)** → **AFD (Autômato Finito Determinístico)**

O sistema fornece uma interface intuitiva com visualização passo a passo dos algoritmos de conversão, incluindo logs detalhados e tabelas de transição.

## ✨ Funcionalidades

### 🔄 Conversão AFe → AFN

- Eliminação de ε-transições
- Cálculo de ε-closure para cada estado
- Reconstrução da função de transição
- Determinação de novos estados finais
- Log detalhado do processo

### ⚡ Conversão AFN → AFD

- Algoritmo de construção de subconjuntos
- Geração de estados compostos
- Eliminação de não-determinismo
- Criação de estado morto quando necessário
- Visualização completa do processo

### 📊 Visualização

- Interface com abas para cada tipo de conversão
- Tabelas de transição interativas
- Destaque para estados iniciais e finais
- Logs detalhados dos algoritmos
- Design responsivo e moderno

## 🚀 Como Usar

### Conversão AFe → AFN

1. **Acesse a aba "🔄 AFe → AFN"**
2. **Defina o AFe:**

   - **Estados**: Digite os estados separados por vírgula (ex: `0, 1, 2`)
   - **Alfabeto**: Digite os símbolos do alfabeto (ex: `a, b`)
   - **Estado inicial**: Digite o estado inicial (ex: `0`)
   - **Transições**: Digite uma transição por linha no formato `origem,símbolo,destino`
     ```
     0,a,1
     0,ε,2
     1,b,2
     ```
   - **Estados finais**: Digite os estados finais (ex: `1, 2`)

3. **Clique em "🚀 Processar AFe"** para validar a entrada
4. **Clique em "🔄 Converter AFe → AFN"** para executar a conversão
5. **Visualize os resultados** nas tabelas geradas e no log detalhado

### Conversão AFN → AFD

1. **Acesse a aba "⚡ AFN → AFD"**
2. **Defina o AFN:**

   - **Estados**: Digite os estados separados por vírgula (ex: `0, 1, 2, 3`)
   - **Alfabeto**: Digite os símbolos do alfabeto (ex: `a, b`)
   - **Estado inicial**: Digite o estado inicial (ex: `0`)
   - **Transições**: Digite uma transição por linha no formato `origem,símbolo,destino`
     ```
     0,a,2
     0,a,3
     2,b,1
     1,b,0
     ```
   - **Estados finais**: Digite os estados finais (ex: `0, 3`)

3. **Clique em "🚀 Processar AFN"** para validar a entrada
4. **Clique em "⚡ Converter AFN → AFD"** para executar a conversão
5. **Visualize os resultados** nas tabelas geradas e no log detalhado

## 🧮 Algoritmos Implementados

### Algoritmo AFe → AFN

O algoritmo implementa a eliminação de ε-transições através dos seguintes passos:

1. **Cálculo do ε-closure**

   ```
   ε-closure(q) = {q} ∪ {p | existe caminho de q para p usando apenas ε-transições}
   ```

2. **Reconstrução da função de transição**

   ```
   δ'(q, a) = ε-closure(δ(ε-closure(q), a))
   ```

3. **Determinação dos estados finais**
   ```
   F' = {q | ε-closure(q) ∩ F ≠ ∅}
   ```

### Algoritmo AFN → AFD (Construção de Subconjuntos)

O algoritmo implementa a construção de subconjuntos:

1. **Inicialização**

   ```
   q0' = {q0}
   ```

2. **Construção iterativa**

   ```
   Para cada conjunto de estados S e símbolo a:
   δ'(S, a) = ⋃(q∈S) δ(q, a)
   ```

3. **Estados finais**
   ```
   F' = {S | S ∩ F ≠ ∅}
   ```

## 📝 Exemplos

### Exemplo AFe → AFN

**Entrada (AFe):**

- Estados: `0, 1, 2`
- Alfabeto: `a, b`
- Estado inicial: `0`
- Transições:
  ```
  0,a,1
  0,ε,2
  1,b,2
  ```
- Estados finais: `1, 2`

**Saída (AFN):**

- Estados: `0, 1, 2`
- Alfabeto: `a, b`
- Estado inicial: `0`
- Transições:
  - `δ(0, a) = {1, 2}`
  - `δ(0, b) = ∅`
  - `δ(1, a) = ∅`
  - `δ(1, b) = {2}`
  - `δ(2, a) = ∅`
  - `δ(2, b) = ∅`
- Estados finais: `0, 1, 2`

### Exemplo AFN → AFD

**Entrada (AFN):**

- Estados: `0, 1, 2, 3`
- Alfabeto: `a, b`
- Estado inicial: `0`
- Transições:
  ```
  0,a,2
  0,a,3
  2,b,1
  1,b,0
  ```
- Estados finais: `0, 3`

**Saída (AFD):**

- Estados: `{0}, {2,3}, {1}, ∅`
- Estado inicial: `{0}`
- Transições determinísticas
- Estados finais: `{0}, {2,3}`

## 🛠️ Tecnologias

- **HTML5**: Estrutura da aplicação
- **CSS3**: Estilização com gradientes e animações
- **JavaScript (ES6+)**: Lógica dos algoritmos e interatividade
- **Design Responsivo**: Layout adaptável para diferentes dispositivos

## 📁 Estrutura do Projeto

```
├── index.html              # Arquivo principal da aplicação
```

## 🎨 Características da Interface

- **Design Moderno**: Interface com gradientes e animações suaves
- **Navegação por Abas**: Separação clara entre tipos de conversão
- **Feedback Visual**: Estados iniciais e finais destacados nas tabelas
- **Logs Detalhados**: Acompanhamento passo a passo dos algoritmos
- **Responsividade**: Adaptação automática para diferentes tamanhos de tela
- **Validação**: Verificação de entradas e tratamento de erros

## 🔧 Funcionalidades Adicionais

- **Botão Limpar**: Reset completo dos campos e resultados
- **Exemplos Integrados**: Casos de teste pré-preenchidos
- **Estado Morto**: Criação automática quando necessário no AFD
- **Formatação Automática**: Limpeza e organização das entradas
- **Símbolos Especiais**: Suporte para ε-transições com formatação especial

## 🎯 Casos de Uso

1. **Educacional**: Ferramenta para ensino de teoria da computação
2. **Acadêmico**: Verificação de exercícios e trabalhos
3. **Pesquisa**: Análise de propriedades de autômatos
4. **Desenvolvimento**: Prototipagem de reconhecedores de linguagens

## 📚 Conceitos Teóricos

A aplicação implementa conceitos fundamentais da teoria da computação:

- **Autômatos Finitos**: Modelos matemáticos para reconhecimento de linguagens regulares
- **ε-transições**: Transições que não consomem símbolos de entrada
- **Não-determinismo**: Capacidade de ter múltiplas transições para o mesmo símbolo
- **Determinismo**: Exatamente uma transição para cada par (estado, símbolo)
- **Equivalência**: Todos os tipos de autômatos reconhecem a mesma classe de linguagens

## 🚀 Execução

1. Faça o download do arquivo `index.html`
2. Abra o arquivo em qualquer navegador web moderno
3. A aplicação estará pronta para uso, sem necessidade de servidor

**Desenvolvido para auxiliar no estudo e compreensão da teoria dos autômatos finitos.**
