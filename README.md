
# 🚀 Alocação Dinâmica de Memória em Sistemas Embarcados (Arduino)

Este repositório apresenta um exemplo prático e didático de como a **Alocação Dinâmica de Memória** pode ser utilizada em sistemas embarcados, especificamente com a plataforma Arduino. O objetivo é demonstrar a flexibilidade do `malloc()` e a importância do `free()` em ambientes com recursos de memória limitados.

Este projeto foi desenvolvido como parte da minha jornada de aprendizado no **Programa de Residência em Sistemas Embarcados** promovido por **FIAP, Alura e CPQD**.

---

## 💡 O Conceito por Trás

Em microcontroladores, a gestão da memória RAM é um fator crítico para a performance e a segurança.

### O Desafio da Alocação Estática
A alocação estática (`int meuArray[100];`) define o tamanho das estruturas de dados em tempo de compilação. Isso gera rigidez, podendo levar a:
* **Desperdício de RAM:** Reservar mais memória do que o necessário.
* **Erros de Estouro (Buffer Overflow):** Falha se a demanda de memória exceder o tamanho predefinido.

### A Solução da Alocação Dinâmica
A alocação dinâmica permite que o programa solicite blocos de memória da *heap* (memória livre) **em tempo de execução**. As funções `malloc()`, `calloc()`, `realloc()` e `free()` são essenciais para gerenciar esse tipo de memória. O **tempo de vida** da memória alocada dinamicamente é **explicitamente controlado** pelo desenvolvedor, oferecendo:
* **Flexibilidade:** Alocar apenas o volume exato de memória necessário, adaptando-se a volumes de dados variáveis ou desconhecidos previamente.
* **Robustez:** A capacidade de verificar o sucesso da alocação (`NULL` em caso de falha) permite um tratamento de erros mais eficaz.
* **Otimização:** Liberar a memória com `free()` quando não é mais necessária previne "memory leaks" (vazamentos de memória), garantindo a estabilidade do sistema a longo prazo.

---

## 🛠️ Como Funciona o Exemplo

Este projeto demonstra a alocação dinâmica para armazenar leituras de um sensor analógico (potenciômetro) em um array.

* No `void setup()`, um array de inteiros é alocado dinamicamente usando `malloc()` para armazenar um número predefinido de leituras (`numReadings`).
* O programa aguarda 5 segundos, permitindo a interação com o potenciômetro na simulação.
* As leituras do pino analógico `A0` são realizadas e armazenadas no array alocado.
* As leituras são impressas no Monitor Serial.
* A memória alocada é **liberada** com `free()` para evitar vazamentos de memória.
* O `void loop()` permanece vazio, pois a demonstração ocorre inteiramente no `setup()`.

---

## 💻 Como Rodar / Simular

### No Tinkercad (Recomendado para Visualização Rápida)
Você pode simular este projeto diretamente no navegador, sem precisar de hardware ou software adicional:
1.  Acesse o link do projeto no Tinkercad: [https://www.tinkercad.com/things/hb6LlqQqsk4-alocacao-dinamica-de-memoria](https://www.tinkercad.com/things/hb6LlqQqsk4-alocacao-dinamica-de-memoria)
2.  Clique em "Iniciar Simulação".
3.  Abra o "Monitor Serial" para ver as leituras.
4.  Durante a contagem regressiva de 5 segundos, gire o potenciômetro para observar a leitura de diferentes valores.

### Com Arduino IDE e Hardware Físico
1.  Clone este repositório ou baixe o arquivo `.ino`.
2.  Abra o arquivo `dynamic_memory_example.ino` no Arduino IDE.
3.  Conecte um potenciômetro ao pino analógico `A0` do seu Arduino (VCC na lateral do potenciômetro, GND na outra lateral, e o pino central no `A0`).
4.  Carregue o código para o seu Arduino.
5.  Abra o Monitor Serial (Ctrl+Shift+M) e defina a taxa de comunicação para 9600 baud.
6.  Observe as leituras após os 5 segundos de espera, e tente girar o potenciômetro durante esse período.
