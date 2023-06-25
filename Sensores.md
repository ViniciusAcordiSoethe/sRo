# Classes dos componentes
## Sensor de Cor

```
class ColorSensor
```

O sensor de cor, de classe `ColorSensor`, é um "cubo"/componente responsável por realizar leituras diretamente a frente de sua face de leitura.
A leitura é realizada a uma distancia máxima de até 8 "blocos", em uma área de 5x5 `pixels` a partir de seu centro.
É calculada a média da leitura realizada e retornada ao usuário dependendo da forma de captura escolhida:

* Digital
```
bool leitura = Bot.GetComponent<ColorSensor>("meu sensor").Digital;
// Mesma coisa de: (Analog.Closest() != Colors.Black);
```
A captura digital do sensor de cor retorna verdadeiro caso o mesmo esteja vendo qualquer cor que seja distante de preto, e falso caso o mesmo esteja vendo a cor preta.
* Analog

```
Color leitura = Bot.GetComponent<ColorSensor>("meu sensor").Analog;
```
Já a captura analógica do sensor de cor, retorna um objeto da classe de apoio Color, podendo realizar outros métodos dessa classe que são melhores descritos abaixo no texto.
Mas já ilustrando superficialmente:

```
double d = leitura.Brightness; // retorna o valor de luminosidade da leitura em preto e branco
double d = leitura.Red; // retorna o valor de vermelho da leitura
double d = leitura.Green; // retorna o valor de verde da leitura
double d = leitura.Blue; // retorna o valor de azul da leitura
string s = leitura.ToString(); // retorna o nome da cor mais próxima lida
```

## Sensor Ultrassônico
O sensor ultrassônico emite 3 raios convergentes de sua superfície, como no esquema: /|\. E caso um objeto esteja sendo visto por um dos três raios, sua distância pode ser captada.
O alcance do ultrassônico é relativamente alto, indo de imediatamente a sua frente até o ponto de convergência dos raios múltiplos "blocos" de distância.

```
class UltrasonicSensor
```

O sensor ultrassônico emite 3 raios convergentes de sua superfície, como no esquema: `/|\`. E caso um objeto esteja sendo visto por um dos três raios, sua distância pode ser captada.
O alcance do ultrassônico é relativamente alto, indo de imediatamente a sua frente até o ponto de convergência dos raios múltiplos "blocos" de distância.

* Digital
```
bool leitura = Bot.GetComponent<UltrasonicSensor>("meu sensor").Digital;
// Mesma coisa de: (Analog != -1);
```

* Analog
```
double leitura = Bot.GetComponent<UltrasonicSensor>("meu sensor").Analog;
```

Já a captura analógica do sensor ultrassônico retorna a distância no qual está vendo um objeto, ou -1 caso não esteja captando nada.

## Sensor Toque

``` 
class TouchSensor
```
O sensor de toque é o sensor mais simples do sBotics. Sua única função é retornar se o mesmo está sendo pressionado pelo contato de outro objeto.

* Digital
```
bool leitura = Bot.GetComponent<TouchSensor>("meu sensor").Digital;
```
A captura digital do sensor de toque retorna se o mesmo está sendo pressionado ou não no momento da chamada.

* Analog
A classe em questão não possui propriedade de acesso analógica

## Buzzer
```
class Buzzer
```

O buzzer é utilizado para tocar sons. É possível acessá-lo utilizando a sintaxe abaixo:

```
Bot.GetComponent<Buzzer>("meu buzzer");
```

**Propriedades públicas:**

* `bool .Playing`: Retorna se o buzzer está tocando algum som naquele momento;

* `void .StopSound()` Para de tocar o som saíndo do buzzer;

* `void .PlaySound(double hertz, WaveFormats wave = WaveFormats.Square)`: Toca um som caso na frequencia especificada e em um determinado formato de onda (não obrigatório);

* `void .PlaySound(string note, WaveFormats wave = WaveFormats.Square)` : Toca um som caso o texto "note" equivaler a algum item no enumerador de apoio Solfege ou Notes, em um determinado formato de onda (não obrigatório);

* `void .PlaySound(Solfege note, WaveFormats wave = WaveFormats.Square)` : Toca um som do enumerador Solfege (Do, Re, Mi, Fa, Sol, La, Si, Do) em um determinado formato de onda (não obrigatório);

* `void .PlaySound(Notes note, WaveFormats wave = WaveFormats.Square)` : Toca um som do enumerador Notes (C, D, E, F, G, A, B) em um determinado formato de onda (não obrigatório).

##Luz LED

```
class Light
```
A luz LED (light) é utilizado para mostrar cores. É possível acessá-la utilizando a sintaxe abaixo:
```
Bot.GetComponent<Light>("meu LED");
```
**Propriedades públicas:**
* `bool .Lit`: Retorna se a luz está ligada ou não.
* `Color .Color`: Retorna a cor (classe de apoio Color) atual da lâmpada.

**Métodos públicos:**

* `void .TurnOn(Color color)`: Liga a luz na cor (classe de apoio Color) especificada;
* `void .TurnOff()`: Desliga a lâmpada, a retornando para a tonalidade azul "original".

Ps.: Para ligar a lâmpada usando uma string, ver os métodos estáticos da classe de apoio Color como `Color.ToColor("Preto")`.
## Servomotor

```
class Servomotor
```

O servomotor é um componente que pode ser rotacionado utilizando uma força, travado e (por não ser apenas um motor, mas sim um servomotor) pode ter seu ângulo retornado. Para acessar um motor, utilize a sintaxe abaixo:

```
Bot.GetComponent<Servomotor>("meu motor");
```
* `double .Angle`: Utilize isso para pegar o ângulo atual de rotação do motor;
  
* `bool .Locked`: Booleano que pode ser definido para travar qualquer rotação do motor (valor padrão = true);
  
* `double .Force`: Double para definir a força (positiva ou negativa) que será exercida pelo motor aos seus objetos conectados (valor padrão = 0).

```
// Exemplo de uso:
Bot.GetComponent<Servomotor>("meu motor").Locked = False;
Bot.GetComponent<Servomotor>("meu motor").Force = -500;
```

## Sensores Internos do Robô
```
class Bot = __sBotics__RobotController
```

Bot não é "só mais um" componente, ela representa apenas a classe reservada `__sBotics__RobotController`,
que não pode ser diretamente chamada pelo usuário (por possuir o prefixo `__sBotics__`) 
e está inclusa apenas em uma única peça no robô, como um "componente central".
Entretanto, há algumas propriedades e métodos que podem ser utilizados.

  **Propriedades públicas:**

* `double .Inclination`: Retorna a angulação do componente central em relação ao plano;
* `double .Compass`: Retorna a angulação do componente central em relação ao norte geográfico;
* `double .Speed`: Retorna a velocidade no qual o componente central está se deslocando.

**Métodos públicos:**
```
T .GetComponent<T>(string name)
```
Já discutido inúmeras vezes neste texto, busca o componente da classe T com o nome especificado;

```
string[] .Components()
```
Retorna um array de string (string[]) com o nome de todos os componentes.

