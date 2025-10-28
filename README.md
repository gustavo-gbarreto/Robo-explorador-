# 🤖 Robô Explorador

![Status do Projeto](https://img.shields.io/badge/status-em_desenvolvimento-blueviolet)
Este repositório contém o projeto de um Robô Explorador que calcula a probabilidade de existência de vida com base nas seguintes variáveis ambientais: luminosidade, umidade, temperatura e utiliza um sensor PIR para verificar a presença. O robô é controlado atravès de um outro circuito simulado remotamente e os comandos sâo enviados via MQTT e sua conexâo é feita através de uma rede WI-Fi
---

## 📖 Índice

- [Sobre o Projeto](#-sobre-o-projeto)
- [Funcionalidades Principais](#-funcionalidades-principais)
- [Tecnologias e Componentes](#-tecnologias-e-componentes)
- [Configuração do Ambiente](#-configuração-do-ambiente)
- [Como Usar](#-como-usar)
- [Autor](#-autor)

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

Liste os principais componentes de hardware e software utilizados:

### Hardware
* **Microcontrolador:** ESP32 
* **Sensores:**
  [-Fotoresistor LDR]
  [-Sensor PIR]
  [-DHT11] 
* **Atuadores:** 2x Motor DC 3-6V com Caixa de Redução e Eixo Duplo 
* **Driver de Motor:** Ponte H L298N
* **Sinalizadores:**
  -1x LED PTH Vermelho
  -1x LED PTH Verde 
* **Alimentação:** Bateria 9V ou fonte de bancada

### Software
* **Linguagem:** C++ (Arduino) e Python
* **IDE/Editor:** VS Code com PlatformIO
* **Bibliotecas Principais:** WIFI.h, HTTPClient.h, UrlEncode.h, PubSubClient.h, DHT.h, ArduinoJson.h, time.h

---

## ⚙️ Configuração do Ambiente

Instruções para configurar o projeto para desenvolvimento ou upload.

[**Exemplo para projeto Arduino:**]
1.  Faça o download e instale a [Arduino IDE](https://www.arduino.cc/en/software).
2.  Clone este repositório:
    ```bash
    git clone [https://github.com/gustavo-gbarreto/Robo-explorador-.git](https://github.com/gustavo-gbarreto/Robo-explorador-.git)
    ```
3.  Abra o arquivo principal `.ino` na Arduino IDE.
4.  Instale as bibliotecas necessárias através do "Library Manager":
    * `[Nome da Biblioteca 1 (ex: NewPing)]`
    * `[Nome da Biblioteca 2 (ex: AFMotor)]`

[**Exemplo para projeto Python (Simulação/Raspberry Pi):**]
1.  Clone o repositório:
    ```bash
    git clone [https://github.com/gustavo-gbarreto/Robo-explorador-.git](https://github.com/gustavo-gbarreto/Robo-explorador-.git)
    cd Robo-explorador-
    ```
2.  (Opcional) Crie e ative um ambiente virtual:
    ```bash
    python -m venv venv
    source venv/bin/activate  # No Windows: venv\Scripts\activate
    ```
3.  Instale as dependências:
    ```bash
    pip install -r requirements.txt
    ```

---

## ▶️ Como Usar

[**Exemplo para projeto Arduino:**]
1.  Conecte o microcontrolador (Arduino) ao seu computador via USB.
2.  Na Arduino IDE, vá em **Tools > Board** e selecione o modelo da sua placa (ex: "Arduino Uno").
3.  Vá em **Tools > Port** e selecione a porta COM correspondente.
4.  Clique no botão **Upload** (seta para a direita) para compilar e enviar o código para o robô.
5.  Desconecte o USB e ligue a alimentação externa do robô.

[**Exemplo para projeto Python (Simulação):**]
Execute o script principal para iniciar a simulação:
```bash
python main.py
