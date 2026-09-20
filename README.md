<div align="center">

# ⚡ EV Smart Charge Monitor

  **Sistema Inteligente de Controle de Recarga de Veículos Elétricos em MicroPython**

  [![MicroPython](https://img.shields.io/badge/MicroPython-1.20%2B-blue.svg?logo=python&logoColor=white)](https://micropython.org/)
  [![Hardware](https://img.shields.io/badge/Hardware-Raspberry%20Pi%20Pico%20%7C%20ESP32-red.svg?logo=raspberrypi&logoColor=white)](#-hardware-necessário)
  [![Display](https://img.shields.io/badge/Display-LCD%201602%20I2C-green.svg)](#-esquema-de-ligação)
  [![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

  <p align="center">
    <a href="#-sobre-o-projeto">Sobre</a> •
    <a href="#-funcionalidades">Funcionalidades</a> •
    <a href="#-esquema-de-ligação">Hardware</a> •
    <a href="#-regras-de-negócio">Regras de Negócio</a> •
    <a href="#-como-executar">Como Executar</a>
  </p>

---

</div>

## 📌 Sobre o Projeto

O **EV Smart Charge Monitor** é um sistema embarcado para gerenciamento e tomada de decisão sobre recargas elétricas baseado no **saldo energético em tempo real** ($\text{Geração} - \text{Consumo}$). 

Desenvolvido em **MicroPython**, o projeto é ideal para sistemas fotovoltaicos (energia solar) e microredes residenciais, garantindo que a recarga só ocorra quando houver disponibilidade de energia de fonte limpa/gerada localmente.

---

## 🚀 Funcionalidades

- 🔋 **Cálculo de Balanço Energético:** Analisa dinamicamente o saldo entre a geração solar e o consumo da rede.
- 🚥 **Sinalização Visual Inteligente:** Três níveis de status via LEDs (Verde, Amarelo e Vermelho).
- 📟 **Driver LCD I2C Nativo:** Controle direto do display LCD 1602 embutido no próprio código, sem necessidade de bibliotecas externas adicionais.
- 🔄 **Modo de Simulação em Cenários:** Processa múltiplos perfis de geração e consumo sequencialmente.

---

## 🛠️ Hardware Necessário

| Componente | Especificação | Quantidade |
| :--- | :--- | :---: |
| **Microcontrolador** | Raspberry Pi Pico / ESP32 | 1 |
| **Display** | LCD 1602 com Módulo I2C (`0x27`) | 1 |
| **LEDs** | 5mm (Verde, Amarelo, Vermelho) | 3 |
| **Resistores** | 220 $\Omega$ | 3 |
| **Protoboard & Jumpers** | Conexões padrão | 1 |

---

## 🔌 Esquema de Ligação

> [!NOTE]
> Os pinos abaixo são configurados no código para a **Raspberry Pi Pico**. Caso utilize ESP32, basta ajustar as atribuições dos pinos no início do script.

```text
               +-----------------------+
               |  Raspberry Pi Pico    |
               +-----------------------+
               |                       |
   LCD (SDA) <-| GP0               GP9 |-> LED Verde (Anodo)
   LCD (SCL) <-| GP1               GP5 |-> LED Amarelo (Anodo)
               |                   GP2 |-> LED Vermelho (Anodo)
               |                       |
               +-----------------------+
