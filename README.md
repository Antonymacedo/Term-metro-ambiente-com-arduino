# Termometro ambiente com arduino
Um termômetro que mede temperatura ambiente usando Arduino Uno;

__Como Funciona:__
O sensor TMP detecta a temperatura ambiente e converte em tensão proporcional,
O Arduino lê a tensão na entrada analógica A0 e a converte em temperatura (em graus Celsius),
A temperatura é exibida no display LCD.

__Os materiais são:__

.Tela LCD

.Resistor de 220Ω

.Sensor de temperatura (TMP)

.Potênciometro

.Arduino Uno


![arduino p1](https://github.com/user-attachments/assets/11b58b02-15c0-4b9b-8999-c27e6e64cdd9)



# Esquema de Conexão:


•**Sensor TMP:**

Pino 1 (VCC): Conecte ao 5V do Arduino.

Pino 2 (VOUT): Conecte à entrada analógica A0 do Arduino.

Pino 3 (GND): Conecte ao GND do Arduino.
______________________________________________________________________________________________________________________________________________________________________
•__Display LCD 16x2:__

Pinos de Controle:

RS: Conecte ao pino digital 12 do Arduino.

E: Conecte ao pino digital 11 do Arduino.

Pinos de Dados:

D4, D5, D6, D7: Conecte aos pinos digitais 5, 4, 3, 2 do Arduino, respectivamente.

Pino de Contraste:

Conecte o meio do potenciômetro ao pino V0 do LCD, um terminal ao GND e o outro ao 5V.
__________________________________________________________________________________________________________________________________________________________________________
•__Alimentação:__

VSS: Conecte ao GND.

VDD: Conecte ao 5V.

A (LED+): Conecte ao 5V (opcional, para retroiluminação).

K (LED-): Conecte ao GND (opcional).

# Código

```
#include <LiquidCrystal.h>

// Inicializando o LCD (RS, E, D4, D5, D6, D7)
LiquidCrystal lcd(7, 8, 9, 10, 11, 12);

const int sensorPin = A0;

void setup() {
  lcd.begin(16, 2); // Configura o LCD como 16 colunas e 2 linhas
  lcd.print("Inicializando...");
  delay(2000);
  lcd.clear();
}

void loop() {
  int sensorValue = analogRead(sensorPin);
  float voltage = sensorValue * (5.0 / 1023.0);  // Converte para tensão
  float temperature = voltage * 100;            // Converte para °C
  
  lcd.setCursor(0, 0);
  lcd.print("Temp: ");
  lcd.print(temperature);
  lcd.print(" C");
  
  delay(1000);
}
```
# Projeto no simulador 

https://www.tinkercad.com/things/8bG02cF6Bpi-termometro-ambiente-
