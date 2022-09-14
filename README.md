> Lucero Naranjo Hector A. - 19211673

# Seven Segment Display (4 digits)
![image](https://user-images.githubusercontent.com/95378364/190031994-da61a5b3-0a19-437f-8bf3-2b085efac7f6.png)

**Que son?**

Los display de 7 segmentos son dispositivos de visualizacion utilizados para representar numerales decimales, asi como ser una laternativa a los displays de matriz que son mas complejos.

Se llaman displays de segmentos porque esta compuesto de varios segmentos que se prenden o apagan para dar la forma del numero deseado. 
Los segmentos suelen ser de leds indivduales o de cristales liquidos.

Existen dos tipos diferentes de displays de 7 segmentos: de ánodo común y de cátodo común. 

En el tipo de ánodo común, todos los ánodos del display están conectados a un pin común, generalmente la fuente de alimentación, y los LED se controlan mediante los cátodos con la conexión a tierra encendida y la potencia pagada. 

En el tipo de cátodo común, todos los cátodos están conectados a un pin común, en este caso generalmente la conexión a tierra, y los LED los controla el estado de los ánodos con la conexión a tierra apagada y la potencia encendida.

## Funcionamiento
Cada uno de los segmentos que forman la pantalla están marcados con siete primeras letras del alfabeto ('a'-'g'), y se montan de forma que permiten activar cada segmento por separado, consiguiendo formar cualquier dígito numérico. A continuación se muestran algunos ejemplos:
- Si se activan o encienden todos los segmentos se forma el número "8".
- Si se activan sólo los segmentos: "a, b, c, d, e, f," se forma el número "0".
- Si se activan sólo los segmentos: "a, b, g, e, d," se forma el número "2".
- Si se activan sólo los segmentos: "b, c, f, g," se forma el número "4".

![image](https://user-images.githubusercontent.com/95378364/190032843-1c6cfb81-277d-40f4-9c57-f07da4f711fd.png)
![image](https://upload.wikimedia.org/wikipedia/commons/thumb/2/2b/Seven_segment_display-animated.gif/90px-Seven_segment_display-animated.gif)
> Segmentos e identificación de los mismos.

# Codigo
#define duration 5000 \
#define A 2\
#define B 3\
#define C 4\
#define D 5\
#define E 6\
#define F 7\
#define G 8\
#define DP 9\
#define disp1 10\
#define disp2 11\
#define disp3 12\
#define disp4 13

#define numbersegments { \
{1,1,1,1,1,1,0,0},\
{0,1,1,0,0,0,0,0},\
{1,1,0,1,1,0,1,0},\
{1,1,1,1,0,0,1,0},\
{0,1,1,0,0,1,1,0},\
{1,0,1,1,0,1,1,0},\
{1,0,1,1,1,1,1,0},\
{1,1,1,0,0,0,0,0},\
{1,1,1,1,1,1,1,0},\
{1,1,1,0,0,1,1,0},\
}

byte numbers[10][8] = numbersegments;

const int segments[8] = {A, B, C, D, E, F, G, DP};

void setup() \
{ \
  pinMode(A, OUTPUT);\
  pinMode(B, OUTPUT);\
  pinMode(C, OUTPUT);\
  pinMode(D, OUTPUT);\
  pinMode(E, OUTPUT);\
  pinMode(F, OUTPUT);\
  pinMode(G, OUTPUT);\
  pinMode(DP, OUTPUT);\
  pinMode(disp1, OUTPUT);\
  pinMode(disp2, OUTPUT); \ 
  pinMode(disp3, OUTPUT);\
  pinMode(disp4, OUTPUT);\
  digitalWrite(A, LOW);\
  digitalWrite(B, LOW);\
  digitalWrite(C, LOW);\
  digitalWrite(D, LOW);\
  digitalWrite(E, LOW);\
  digitalWrite(F, LOW);\
  digitalWrite(G, LOW);\
  digitalWrite(DP, LOW);\
  digitalWrite(disp1, LOW);\
  digitalWrite(disp2, LOW);\
  digitalWrite(disp3, LOW);\
  digitalWrite(disp4, LOW);\
 } 

 void loop()\
 { \
  for (int digit4=0; digit4<10; digit4++)\
  { \
    for (int digit3=0; digit3<10; digit3++)\
     { \
       for (int digit2=0; digit2<10; digit2++)\
        { \
          for (int digit1=0; digit1<10; digit1++)\
           { \
             for (int t=0; t<30; t++)\
              { \
                setsegments(digit1, disp1, duration);\
                setsegments(digit2, disp2, duration);\
                setsegments(digit3, disp3, duration);\
                setsegments(digit4, disp4, duration);\
               }\
            }\
         }\
      }\
   }\
 } \       

  void setsegments(int number, int digit, int ontime)\
  { \
    for (int seg=0; seg<8; seg++)\
    { \
      if(numbers[number][seg]==1)\
      { \
        digitalWrite(segments[seg], HIGH);\
      }\
      else \
      {\
        digitalWrite(segments[seg], LOW);\
      }\
    }\
    digitalWrite(digit, HIGH);\
    delayMicroseconds(ontime);\
    digitalWrite(digit, LOW);\
  }\

