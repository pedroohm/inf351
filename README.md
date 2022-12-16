# INF 351 - Sistemas Embarcados
Tarefas desenvolvidas e trabalhadas ao longo da disciplina de sistemas embarcados

Links para projetos no Tinkercad:
- [Sinal de trânsito](https://www.tinkercad.com/things/cqZiBnmquDY-inf-351-sinal-com-delay/editel?sharecode=8amqkm1yjkt6Jg-5jGzq1_opUrOBXxqCrwtUhF2Ozps): Problema inicial, para primeiro contato com arduino resistores e LED's. Foram utilizados 6 resistores de 800 ohms, 6 leds, 1 arduino uno e um switch com resistor pull up para iniciar o sistema.

- [Sinal de trânsito com função millis()](https://www.tinkercad.com/things/cqZiBnmquDY-inf-351-sinal-com-delay/editel?sharecode=8amqkm1yjkt6Jg-5jGzq1_opUrOBXxqCrwtUhF2Ozps): Outra solução para o problema inicial, mas com utilização da função millis que ao contrário da delay, não mantém a espera ocupada. Foram utilizados 6 resistores de 800 ohms, 6 leds, 1 arduino uno.

- [Ledreg com Joystick Shield](https://embarcados.com.br/wp-content/uploads/2016/07/2016-07-04-16.49.45-e1467664974367-595x418.jpg) : Controlador de luminosidade para LED rgb, com possibiidade de alternar as cores pelos botões dispostos do lado direito do shield.
~~~C++
int red, blue, green, x, y,z;

void setup() {
  pinMode(9, OUTPUT); // vermelho
  pinMode(10, OUTPUT); // azul
  pinMode(11, OUTPUT); // verde

  red = 255;
  blue = 255;
  green = 255;
  x = 9; y=10, z=11;
  Serial.begin(9600);
  pinMode(2, INPUT); // A a F
  pinMode(3, INPUT); // A a F
  pinMode(4, INPUT); // A a F
  pinMode(5, INPUT); // A a F
  pinMode(6, INPUT); // A a F
  pinMode(7, INPUT); // A a F
  pinMode(8, INPUT); //joystick button;
    
}

void loop() {
  
  int joyX = analogRead(A0); // valor de 0 a 1023 eixo X
  int joyY = analogRead(A1); // valor eixo Y sobe e desce

  //analogWrite(y, joyY/4);
  
  if ( digitalRead(5) == LOW){
    analogWrite(x, joyY/4);
  }  
  else if ( digitalRead(2) == LOW) {
    analogWrite(y, joyY/4);
  }
  else if ( digitalRead(3) == LOW) {
    analogWrite(z, joyY/4);
  }

  if ( digitalRead(4) == LOW)  {
    red = 255, blue = 255, green = 255;
    analogWrite(9, red);
    analogWrite(10, green);  
    analogWrite(11, blue);    
  }
  
}
~~~

- [Exemplo de utilização software serial](https://www.tinkercad.com/things/loPFmKxhuwC-copy-of-software-serial/editel?sharecode=ib6ayoHrM39-gHRWWf9Cjs5Zq3VgeWTc5gOAL_PCwqU): Comunicação entre dois arduinos pelos pinos pwm.

- [Comunicação I2C](https://www.tinkercad.com/things/3JF9ul2pKwb-copy-of-i2c-communicationled/editel?sharecode=VOFLMu5qgx3ez8kDPTSAdcrfTTn_MeJQh00cRs4VLHc): Comunicação entre dois arduinos mestre e súdito acendendo LED.

- [Jogo para módulo LCD 16x2](https://www.tinkercad.com/things/jXHLoEPEHzJ-dino-sem-internet/editel?sharecode=AAsz6RJW4JIby4PtCG72CrTYI3HuVMdCgkEFugpKcro): Jogo com menu inicial, adaptável para 2.



