# Manual de Configuración. 
Redes de Computadoras 1 - Practica 2

## Topología de Red

La topología que se implemento en esta práctica esta compuesta por:

1. **VPC**
2. **Switch**
3. **Router**
4. **Maquina Virtual**

### Configuración de Topología

La topologia esta compuesta principalmente por un solo router, 2 switch, 5 VPC y una maquina virtual, se agrego una interfaz más en el segundo slot a un router. 

Las conexiones entre los equipos estan dadas de la siguiente forma. 

|Tipo de Host     |Nombre       | Conectado a       |Puerto/Interfaz  |
| --------------- | ----------- | ----------------- |---------------- |
|VPC              |PC1          |Finanzas-Ethernet 1|Ethernet0        |
|VPC              |PC2          |Finanzas-Ethernet 2|Ethernet0        |
|VPC              |PC3          |Ventas-Ethernet 1  |Ethernet0        |
|VPC              |PC4          |Ventas-Ethernet 2  |Ethernet0        |
|VPC              |PC5          |Ventas-Ethernet 3  |Ethernet0        |
|Máquina Virtual  |TinyLinuxVM-1|Informatica-Eth1   |Ethernet0        |
|Switch           |Finanzas     |R1-FastEthernet 0/0|Ethernet0        |
|Switch           |Ventas       |R1-FastEthernet 0/1|Ethernet0        |
|Switch           |Informatica  |R1-FastEthernet 1/0|Ethernet0        |

Las configuraciones del router (tanto la dirección de red como la dirección ip de cada interfaz), se detalla en la siguiente tabla:


|Interfaz          |Dirección de Red |Direccion IP   |
| ---------------- | --------------- |-------------- |
|FastEthernet 0/0  |192.168.13.0/26  |192.168.13.1   |
|FastEthernet 0/1  |192.168.13.64/26 |192.168.13.65  |
|FastEthernet 1/1  |192.168.13.128/26|192.168.13.129 |


En los host se implementaron las siguientes configuraciones:

|Tipo de Host     |Nombre       | Conectado a |Direccion IP  |
| --------------- | ----------- | ----------- |------------- |
|VPC              |PC1          |Finanzas     |192.168.13.2  |
|VPC              |PC2          |Finanzas     |192.168.13.3  |
|VPC              |PC3          |Ventas       |192.168.13.66 |
|VPC              |PC4          |Ventas       |192.168.13.67 |
|VPC              |PC5          |Ventas       |192.168.13.68 |
|Máquina Virtual  |TinyLinuxVM-1|Informatica  |192.168.13.130|

Siendo la configuracion final la siguiente: 


|Tipo de Host     |Nombre       | Conectado a |Direccion IP  |Mascara de Red  |Gateway       |
| --------------- | ----------- | ----------- |------------- |--------------- |------------- |
|VPC              |PC1          |Finanzas     |192.168.13.2  |255.255.255.192 |192.168.13.1  |
|VPC              |PC2          |Finanzas     |192.168.13.3  |255.255.255.192 |192.168.13.1  |
|VPC              |PC3          |Ventas       |192.168.13.66 |255.255.255.192 |192.168.13.65 |
|VPC              |PC4          |Ventas       |192.168.13.67 |255.255.255.192 |192.168.13.65 |
|VPC              |PC5          |Ventas       |192.168.13.68 |255.255.255.192 |192.168.13.65 |
|Máquina Virtual  |TinyLinuxVM-1|Informatica  |192.168.13.130|255.255.255.192 |192.168.13.128|


Dando como resultado la topología de la siguiente forma:

![image](https://user-images.githubusercontent.com/37676214/91649063-cacb4080-ea2c-11ea-83c9-ce2ccfd494e7.png)

## Configuracion de los Equipos

### VPC

Colocar una VPC y posteriormente configurarla se realizan los siguiente pasos:

 1. Se toma selecciona una imagen de VPC entre los dispositivos. 
 2. Se arrastra el dispositivo al area de trabajo.
 3. Se enciende (Click derecho -> Start).
 4. Se entra a la terminal del dispositivo (Click derecho -> Console).
 
Una vez en el terminal del dispositivo se siguen los siguientes pasos.

 1. Se le asigna una dirección IP al dispositivo, con su respectiva mascara de subred. 
```sh
# ip [direccion/mascara gateway]
```
 2. Se salvan los cambios.
```sh
# save
``` 
 3. Opcionalmente se puede visualizar si la dirección ip.
```sh
# show ip
```

#### Configuración de PC1

Siguiendo el algoritmo anterior dispositivo PC1 se configuró de la siguiente forma.

-
![image](https://user-images.githubusercontent.com/37676214/91649124-9dcb5d80-ea2d-11ea-8bf2-1c894bccdcce.png)

#### Configuración de PC2

Siguiendo el algoritmo anterior dispositivo PC2 se configuró de la siguiente forma.

-
![image](https://user-images.githubusercontent.com/37676214/91649148-e84cda00-ea2d-11ea-812d-2e9ebb194e6f.png)

#### Configuración de PC3

Siguiendo el algoritmo anterior dispositivo PC3 se configuró de la siguiente forma.

-
![image](https://user-images.githubusercontent.com/37676214/91649185-6ad59980-ea2e-11ea-9eb3-c54a010dde4f.png)

#### Configuración de PC4

Siguiendo el algoritmo anterior dispositivo PC4 se configuró de la siguiente forma.

-
![image](https://user-images.githubusercontent.com/37676214/91649205-a83a2700-ea2e-11ea-9ccc-19544327df2d.png)

#### Configuración de PC5

Siguiendo el algoritmo anterior dispositivo PC5 se configuró de la siguiente forma.

-
![image](https://user-images.githubusercontent.com/37676214/91649225-ed5e5900-ea2e-11ea-86d1-315b91633c70.png)

### Configuración de la maquina virtual.

Para configurar la maquina virtual se sigue el siguiente algoritmo. 

1. Se enciende el dispositivo (Click derecho -> Start).

Nota: Esta maquina virtual debe haber sido creada previamene en VMWare o en VirtualBox y haber sido importada a GNS3.

2. Una vez encendida la maquina virtual, vamos a su configuración.

3. Abrimos Panel de control.
-
![image](https://user-images.githubusercontent.com/37676214/90329539-efbab080-df62-11ea-8366-35f1ca94eed2.png)

4. Abrimos Network
-
![image](https://user-images.githubusercontent.com/37676214/90329552-0fea6f80-df63-11ea-84f8-9efe2cf8f57a.png)

5. Ingresamos la configuración correspondiente. 

6. Damos click donde dice aplicar. 
-
![image](https://user-images.githubusercontent.com/37676214/91649283-75446300-ea2f-11ea-95e4-c62502f56ff7.png)

7. Cerramos.

8. Opcional
- Verificamos la configuración el siguiente comando la terminal.
```sh
$ ifconfig
``` 
-
![image](https://user-images.githubusercontent.com/37676214/91649295-9907a900-ea2f-11ea-9bed-8cf35c8b83b2.png)


### Configuración del Router


***Nota***: hay que añadir una interfaz mas al router. 

-
![image](https://user-images.githubusercontent.com/37676214/91649531-99ee0a00-ea32-11ea-8eef-198b8f9da006.png)

-
![image](https://user-images.githubusercontent.com/37676214/91649539-a3777200-ea32-11ea-95ac-d237b301db2a.png)

Para configurar el router, se sigue el siguente algoritmo.


1. Se arrasta el router al area de trabajo.
2. Se enciende (Click derecho -> Start).
3. Se entra al terminal (Click derecho -> console).
4. Se entra a modo privilegiado en el router.

```sh
R1 > enable
``` 

5. Opcionalmente podemos visualizar un resumen de la interfaz ip. 

```sh
R1# show ip interface brief
``` 
Obteniendo el siguiente resultado. 

-
![image](https://user-images.githubusercontent.com/37676214/91649603-f6512980-ea32-11ea-8526-85b01e25391c.png)

6. Procedemos a ingresar en la configuración del router.

```sh
R1# configure terminal
``` 

7. Configuramos la interfaz.

```sh
R1(config)# int fastethernet 0/0
``` 

8. Insertamos la dirección IP que tendrá ese puerto.

```sh
R1(config-if)# ip address 192.168.13.1 255.255.255.192
``` 

9. Configuramos la velocidad de la interfaz.

```sh
R1(config-if)# speed auto 
``` 

10. Coguramos el modo full-duplex de la interfaz.

```sh
R1(config-if)# full-duplex
``` 

11. Encendemos la interfaz.

```sh
R1(config-if) # no shutdown
``` 

12. Salimos de la configuracion de la interfaz.

```sh
R1(config-if)# exit 
``` 

13. Repetimos del paso 7 al 12 con los siguientes valores
-Interfaz: FastEthernet 0/1 
-IP:       192.168.13.65
-Mascara:  255.255.255.192
**-**
-Interfaz: FastEthernet 1/1 
-IP:       192.168.13.129
-Mascara:  255.255.255.192

14. Salimos de la configuracion del Router

```sh
R1(config)# exit 
``` 

15. Guardamos los cambios.

```sh
R1# write memory 
``` 

15. Verificamos que la configuracion este bien.  

```sh
R1# show ip interface brief
``` 
Si todo esta bien el router deberia tener este resumen de interfaz ip. 

-
![image](https://user-images.githubusercontent.com/37676214/91649658-5c3db100-ea33-11ea-8345-e6a794f2271e.png)


### Verificando Conexiones

Una vez, conectado y configurado de la forma anteriormente descrita, las configuraciones ya nos deberian permitir la comunicacion entre todas las maquinas, Esto se puede corroborrar haciendo ping desde la terminal de cualquier host hacia cualquiera de las direcciones ip de los demás. 

#### TinyLinuxVM-1

- ![image](https://user-images.githubusercontent.com/37676214/91649792-ed615780-ea34-11ea-86ea-1926dcc5e1cf.png)

#### PC1

- ![image](https://user-images.githubusercontent.com/37676214/91649849-77a9bb80-ea35-11ea-8957-fabea7d3c88a.png)

#### PC2

- ![image](https://user-images.githubusercontent.com/37676214/90330801-dcacde00-df6c-11ea-9221-fb9d3fd0e730.png)

#### PC3

- ![image](https://user-images.githubusercontent.com/37676214/91651263-e1cb5c00-ea47-11ea-87ff-7f6fbff8d822.png)

#### PC4

- ![image](https://user-images.githubusercontent.com/37676214/91651286-2f47c900-ea48-11ea-8306-ae5eb87ab724.png)


#### PC5

- ![image](https://user-images.githubusercontent.com/37676214/91651297-69b16600-ea48-11ea-980a-397d35a6641f.png)

