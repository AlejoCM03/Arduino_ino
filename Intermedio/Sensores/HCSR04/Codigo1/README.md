## SENSORES

### SENSOR ULTRASONICO MÓDULO HC-SR04

![Codigo1](C:\Users\Alejandro\Pictures\Screenshots\codigo1.png)

```arduino
// C++ code
//
int trig = 3;
int echo = 2;
int duracion;
int distancia;


void setup()
{
  Serial.begin(9600);
  pinMode(trig, OUTPUT); //Ya que esta va a representar el emisor
  pinMode(echo, INPUT); //Ya que va a representar el receptor
  //Hastaeste punto ya detecta la distancia
}

void loop()
{
  digitalWrite(trig, HIGH); //Para que de el "Disparo"
  delay(10); // Esperar un momento
  digitalWrite(trig, LOW); //Apagar el emisor
  duracion = pulseIn(echo, HIGH);
  //Se utiliza para devolver el tiempo en microsegundos del "disparo"
  distancia = (duracion/2)/29;
  /*
  se divide entre dos debido a que la duracion sera del punto que va
  hasta el punto que regresa, por lo que nos da la el tiempo de ida
  y el tiempo de vuelta.
  
  Se divide entre 29 debido a que ahora se quiere hacer una conversion
  de micorsegundos a centimetros, haciendo uso de la siguiente logica
  Basandose en la velocidad del sonido en aire quees igual a 343 metros por segundo
  
  La velocidad del sonio en centimetros por segundo es de 34300 cm/s
  por lo que, es igual a 0.0343cm/microsegundos
  
  Para obtener la distancia, sacamos el inverso de la velocidad
  1/0.0343 dando un valor aproximado de 29
  */
  Serial.println(distancia);
}

```