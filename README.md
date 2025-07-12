int *readings;   // Ponteiro: "chave" para nosso bloco de memória dinâmico.
int numReadings; // Quantidade de leituras que queremos guardar (definida em tempo de execução!).

void setup() {
  Serial.begin(9600); // Inicia comunicação serial.
  numReadings = 10;   // Exemplo: queremos 10 leituras.

  // Alocando memória: Pedimos ao Arduino o espaço exato na RAM para 'numReadings' inteiros.
  readings = (int *)malloc(numReadings * sizeof(int));
  
  if (readings == NULL) 
  {
    Serial.println("Memoria esgotada!"); // Tratamento de erro se a alocação falhar.
    return;
  }

  Serial.println("Gire o potenciometro agora! Leituras em 5 segundos...");
  
  delay(5000); 

  // Coleta as 10 leituras do pino A0 e armazena no array dinâmico.
  for (int i = 0; i < numReadings; i++) 
  {
    readings[i] = analogRead(A0);
  }

  // Imprime as leituras no Monitor Serial.
  for (int i = 0; i < numReadings; i++) {
    Serial.print("Leitura ");
    Serial.print(i);
    Serial.print(": ");
    Serial.println(readings[i]);
  }

  // Liberando memória: DEVOLVE o espaço alocado para o sistema.
  free(readings);
  

} 

void loop() 
{
 // loop() está vazio para esta demonstração.
}
