# 🤖 Robô Explorador

![Status do Projeto](https://img.shields.io/badge/status-em_desenvolvimento-blueviolet)
Este repositório contém o projeto de um Robô Explorador que calcula a probabilidade de existência de vida com base na luminosidade, umidade e temperatura em conjunto com um sensor PIR para verificar a presença. O robô é controlado atravès de um outro circuito simulado remotamente e os comandos sâo enviados via MQTT e sua conexâo é feita através de uma rede WI-Fi
---

## 📖 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Tecnologias e Componentes](https://github.com/gustavo-gbarreto/Robo-explorador-/tree/main?tab=readme-ov-file#%EF%B8%8F-tecnologias-e-componentes)  
- [Configuração do Ambiente](https://github.com/gustavo-gbarreto/Robo-explorador-/tree/main?tab=readme-ov-file#%EF%B8%8F-configura%C3%A7%C3%A3o-do-ambiente)
- [Configurando as conexões externas](https://github.com/gustavo-gbarreto/Robo-explorador-/tree/main?tab=readme-ov-file#%EF%B8%8F-configurando-as-conex%C3%B5es)
- [Como Usar](https://github.com/gustavo-gbarreto/Robo-explorador-/tree/main?tab=readme-ov-file#%EF%B8%8F-como-usar)
- [Autores](https://github.com/gustavo-gbarreto/Robo-explorador-/tree/main?tab=readme-ov-file#autores)
  

---

## 📍 Sobre o Projeto


O projeto do robô foi desenvolvido sob a orientaçâo do professor Wild Freitas como um projeto para a matéria de Pràticas integradas: IOT. Seu desenvolvimento foi feito em duas etapas: a etapa 4 do mòdulo da camada de redes e a etapa 1 do mòdulo da camada de serviço.  
Na camada de redes, o projeto o projeto tinha como foco o monitoramento das variàveis do ambiente, usando um LDR para medir luminosidade, um DHT para medir temperatura e umidade e um PIR para detectar presença. Em conjunto, esses 3 sensores determinavam a probabilidade de existência de vida no planeta hipotètico. Além do cálculo de probabilidade de vida, tambèm foi implementado o controle remoto usando MQTT e o uso de uma API para envio de mensagem via whatsapp caso houvesse altas chances de existência de vida.  
Na camada de serviço, foi incluido o armazenamento dos dados lidos pelo robô em um banco de dados, o MongoDB, foi desenvolvida uma API em python para integrar a programaçâo do microcontrolador ao banco de dados e registrar as leituras com a data e horàrio em que ela foi obtida

<img width="360" height="360" alt="image" src="https://github.com/user-attachments/assets/61e0f7eb-2d99-407b-8814-3cb5da0578e4" />

---

## ✨ Funcionalidades Principais

- [ ] Mediçâo de temperatura, umidade e luminosidade.
- [ ] Detecção de presença em tempo real.
- [ ] Controle de motores DC de forma remota (movimento para frente, ré, curvas).
- [ ] Envio de mensagem de alerta via Whatsapp.
- [ ] Armazenamento das leituras em um banco de dados

---

## 🛠️ Tecnologias e Componentes


### Hardware
* **Microcontrolador:** ESP32 
* **Sensores:**  
  -Fotoresistor LDR  
  -Sensor PIR  
  -DHT11 
* **Atuadores:** 2x Motor DC 3-6V com Caixa de Redução e Eixo Duplo 
* **Driver de Motor:** Ponte H L298N
* **Sinalizadores:**  
  -1x LED PTH Vermelho  
  -1x LED PTH Verde  
* **Alimentação:** Bateria 9V ou fonte de bancada
* **Circuito**  
  <img width="806" height="339" alt="image" src="https://github.com/user-attachments/assets/9898fcb4-e59a-4b0a-a682-0c7585292790" />
  **Obs:** O circuito representado na imagem está incompleto, o Wokwi não possui os componentes motor DC e ponte H L298N 


### Software
* **Linguagem:** C++ (Arduino) e Python
* **IDE/Editor:** VS Code com PlatformIO
* **Bibliotecas Principais:** WIFI.h, HTTPClient.h, UrlEncode.h, PubSubClient.h, DHT.h, ArduinoJson.h, time.h

---

## ⚙️ Configuração do Ambiente

Instruções para configurar o projeto para desenvolvimento ou upload.

1.  Faça o download e instale o VSCode (https://code.visualstudio.com/Download)).  
2.  Clone este repositório:  
   ```bash
    git clone [https://github.com/gustavo-gbarreto/Robo-explorador-.git]
   ```
3.  Abra o arquivo principal `main.cpp` no VSCode usando o PlatformIO.  
4.  Instale as bibliotecas necessárias:

## ⚙️ Configurando as conexões 

1.  Altere as credenciais do Wifi para a sua rede:  
   ``` C++
    const char* ssid = "rede_exemplo"; // nome da sua rede Wi-Fi
    const char* password = "12345678"; // Senha da sua rede
  ```
2. Configure seu broker mqtt e a porta usada:
  ``` C++
    const char* mqtt_server = "broker.hivemq.com"; 
    const int mqtt_port = 1883;
  ```
3. Configure o tòpico mqtt a ser utilizado:
  ```C++
    const char* mqtt_topic_command = "senai/cimatec/robo/comandos/gradin"; 
  ```
4. Configure o CallmeBot
  ```C++
   String phoneNumber = "5571999992222"; // insira o telefone que irà receber as mensagens via Whatsapp
   String apiKey = "3813015"; // Para saber qual sua key da API, seguir o passo a passo em: https://www.callmebot.com/blog/free-api-whatsapp-messages/
  ```
5. Substitua o IP da API para o IP da sua máquina.  
   - Pressione Win + R e digite cmd.  
   - use o comando ipconfig, copie o endereço IPV4 da sua máquina e substitua na seguinte linha
```C++
   const char* api_url = "http://10.183.253.145:5000/leituras";
```
     
---

## ▶️ Como Usar

#Gravando o firmware no seu microcontrolador  
1.  Conecte o microcontrolador (ESP32) ao seu computador via USB.  
2.  Configure a placa no seu projeto
3.  Vá em **Tools > Port** e selecione a porta COM correspondente.
4.  Clique no botão **Upload** (seta para a direita) para compilar e enviar o código para o robô.

#Executando o script  
1. Abra o terminal(Ctrl + Shift + ")
2.  Execute o script principal para iniciar a simulação:
```bash
python api_robo.py
```

## Autores

-[Gustavo Barreto](https://github.com/gustavo-gbarreto) - gustavo.barreto@ba.estudante.senai.br  
-[Guilherme Gradin](https://github.com/gradinguilherme/gradinguilherme) - guilherme.c@aln.senaicimatec.edu.br  
-[Juan Victor Vieira](https://github.com/juanvvieira) - juan.nascimento@aln.senaicimatec.edu.br  
-[Uriel Henrique Oliveira](https://github.com/UrielHRO) -uriel.oliveira@ba.estudante.senai.br  




