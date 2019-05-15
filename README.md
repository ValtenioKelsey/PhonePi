## AV2
## Captação de dados em dispositivos abdroid.

# Passo 1
instalar o APP phonePi no dispositivo android

![App Store](https://github.com/ValtenioKelsey/PhonePi/blob/master/img1.png?raw=true)

1.1 Condições de funcionamento do APP:
    Os dispositivos a serem conectados precisam estar conectados na mesma rede (sem restrições). No caso do jaguar conectar na rede do próprio jaguar (jaguar-unifor).

1.1.2 colocar endereço de IP e porta, por padrão (porta 5000).

![App](https://github.com/ValtenioKelsey/PhonePi/blob/master/img2.png?raw=true)
![App](https://github.com/ValtenioKelsey/PhonePi/blob/master/img3.png?raw=true)

Após conectado, abrir o pronpt de comando e rodar o código do programa (https://github.com/priyankark/PhonePi_SampleServer ) em python.

A lógica de conectar os dados do sensor na rede ros implica em um código em python, para ler o arquivo txt do sensor, e enviar esses valores para um tópico ros. Assim foi implementado ao código de leitura as bibliotecas do ros para envio de dados: import rospy e from std_msgs.msg import String.

Na parte do código que há a leitura do arquivo txt proveniente do sensor selecionado, foi acrescido a parte do código para pegar o mesmo valor do sensor e subir para um tópico ros. Para isso foi criado a função Talker().

```
def talker(mx):
message = mx
pub = rospy.Publisher('chatter', String, queue_size=10) # Publica(a msg, tipo string, com uma fila de espera de ate 10 msgs [ para delay])
rospy.init_node('JaguarJoystickComm', anonymous=True)
rate = rospy.Rate(10) # 10hz
# while not rospy.is_shutdown():
hello_str = message
rospy.loginfo(hello_str)
pub.publish(hello_str)
#rate.sleep()
```

![Dados](https://github.com/ValtenioKelsey/PhonePi/blob/master/img4.png?raw=true)
