# EXP-03-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resistor
# DATE :18/03/2024
# NAME : ROHIT KUMAR M
# ROLLNUMBER :212221220045
# DEPARTMENT:INFORMATION TECHNOLOGY

## AIM: 
To interface an FSR(force sensitive resistor) and scale the output voltage obtained to pressure applied 
 
### COMPONENTS REQUIRED:
1.	FSR  (force sensitive resistor)
2.	1 KΩ resistor 
3.	Arduino Uno 
4.	USB Interfacing cable 
5.	Connecting wires 


### THEORY: 
FSRs are basically a resistor that changes its resistive value (in ohms Ω) depending on how much it is pressed. These sensors are fairly low cost, and easy to use. They also vary some from sensor to sensor perhaps 10%. FSR's resistance changes as more pressure is applied. When there is no pressure, the sensor looks like an infinite resistor (open circuit), as the pressure increases, the resistance goes down. This graph indicates approximately the resistance of the sensor at different force measurements.
 

![image](https://user-images.githubusercontent.com/36288975/163532939-d6888ae1-4068-4d83-86a7-fc4c32d5179e.png)

### FIGURE 01 GRAPH OF FORCE vs RESISTANCE **




![image](https://user-images.githubusercontent.com/36288975/163532957-82d57567-a1c3-48c5-8a87-7ea66d6fca49.png)




### FIGURE 02 FORCE SENSITIVE RESITOR FOIL DISC TYPE  

FSRs are often a polymer with conductive material silk-screened on. That means they're plastic and the connection tab is crimped on somewhat delicate material. The best way to connect to these is to simply plug them into a breadboard.

The easiest way to measure a resistive sensor is to connect one end to power and the other to a pull-down resistor to ground. Then the point between the fixed pull down resistor and the variable FSR resistor is connected to the analog input of a microcontroller such as an Arduino The way this works is that as the resistance of the FSR decreases, the total resistance of the FSR and the pull down resistor decreases from about 100Kohm to 10Kohm. That means that the current flowing through both resistors increases which in turn causes the voltage across the fixed 10K resistor to increase.

 ![image](https://user-images.githubusercontent.com/36288975/163532972-2b909551-12c9-485d-adb1-d1e988d557bd.png)

### TABLE -01 FORCE AND OUTPUT VOLTAGES**
	
  Table -01 indicates the approximate analog voltage based on the sensor force/resistance w/a 5V supply and 10K pull down resistor.

### Vo = Vcc ( R / (R + FSR) )								Eq-01

****Where R= 1KΩ in this experiment 
****That is, the voltage is proportional to the inverse of the FSR resistance.










![image](https://user-images.githubusercontent.com/36288975/163532979-a2a5cb5c-f495-442c-843e-bebb82737a35.png)



### FIGURE-03 CIRCUIT DIAGRAM

![M ROHIT KUMAR (212221220045)_page-0001](https://github.com/rohitkumar20700000/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/130482461/2f7fc70b-f923-47f8-9e8d-05ed1d82a2c6)


### SCHEMATIC DIAGRAM
## OFF :

![Screenshot 2024-03-03 172157](https://github.com/rohitkumar20700000/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/130482461/12fd3e1e-a738-4426-ba2e-32753ab1f232)

## ON :
![Screenshot 2024-03-03 172142](https://github.com/rohitkumar20700000/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/130482461/71265356-e6a1-42c5-9f76-8c2b92164c94)



### PROCEDURE:
1.	Connect the circuit as per the circuit diagram 
2.	Connect the board to your computer via the USB cable.
3.	If needed, install the drivers.
4.	Launch the Arduino IDE.
5.	Select the board (If you the board is arduino uno, select accordingly).
6.	Select your serial port, accordingly ( E.g. COM5 )
7.	Open the file of the program  and verify the error , clear if any errors that are existing 
8.	Upload the program and check for the physical working. 
9.	Ensure safety before powering up the device 
10.	Plot the graph for the output voltage vs the resistance 


### PROGRAM 
 ```
 212221220045
 ROHIT KUMAR M
 IT- 3rd YEAR
```

```
int led=7;
int fsr;

void setup()
{
  pinMode(led, OUTPUT);
  Serial.begin(9600);
}
void loop()
{
  fsr=analogRead(A0);
  Serial.print("raw value=");
  Serial.println(fsr);
  delay(500);
  int m;
  m=map(fsr,0,159,0,10);
  Serial.print("mapped value=");
  Serial.println(m);
  
  if(fsr>50)
  {
    digitalWrite(led,LOW);
    delay(500);
    digitalWrite(led,HIGH);
    delay(500);
  }
}
```

### TABLE -02 standard deviation table 
 <img width="542" alt="Screenshot 2024-03-01 214843" src="https://github.com/Prasanna-936/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/130341982/f6b94ea6-7ccf-4108-8781-3fc922d6d0dd">

## Figure 4 Graph comparison of applied and mapped forces

<img width="430" alt="Screenshot 2024-03-01 222831" src="https://github.com/Prasanna-936/EXPERIMENT-NO--04-PRESSURE-MEASUREMENT-USING-ARDUINO-AIM-To-interface-an-FSR-force-sensitive-resist/assets/130341982/1e558a46-6b98-4e0b-9075-313441a220c2">

### Population Standard Deviation
The population standard deviation, the standard definition of σ, is used when an entire population can be measured, and is the square root of the variance of a given data set. In cases where every member of a population can be sampled, the following equation can be used to find the standard deviation of the entire population:



Where
xi is an individual value
μ is the mean/expected value
N is the total number of values

For those unfamiliar with summation notation, the equation above may seem daunting, but when addressed through its individual components, this summation is not particularly complicated. The i=1 in the summation indicates the starting index, i.e. for the data set 1, 3, 4, 7, 8, i=1 would be 1, i=2 would be 3, and so on. Hence the summation notation simply means to perform the operation of (xi - μ)2 on each value through N, which in this case is 5 since there are 5 values in this data set.

``` μ = (0.9+2.02+2.99+4.03+4.95+5.97+6.92+7.94+9.03+10) / 10 = 5.484        
σ = √[(0.99- 5.484)^2 + (3 - 5.484)^2 + ... + (10- 5.484)^2)]/10
σ = √(12.13826 +9+16+25+36+49+64+64+81+100)/10 = 2.135739

```
















### RESULTS : 
Arduino uno is interfaced with FSR and output values are indicated on a graph.
