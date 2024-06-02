---
tags:
  - "#ai"
  - "#gpt-4"
  - "#image-generation"
  - "#tts"
  - "#python"

  - "#visual-question-answering"
  - "#voice-recognition"
  - "#voice-synthesis"
---
<h1 align="center">Real Gemini</h1>

<p align="center">
  <strong>Google's Gemini implemented with GPT-4 Vision, Whisper and Resemble AI</strong>
  </p>
<p align="center">
  This project leverages the power of AI to answer questions based on visual inputs -- like Google's Gemini demo. It integrates GPT-4 Vision for image understanding, Whisper for voice recognition, and Resemble AI for voice synthesis, creating a comprehensive system capable of interpreting visual data and responding verbally.  
  
  
  Bu proje, Google'ın Gemini demosunda olduğu gibi görsel girdilere dayalı soruları yanıtlamak için yapay zekanın gücünden yararlanıyor. Görüntü anlama için GPT-4 Vision, ses tanıma için Whisper ve ses sentezi için Resemble AI'yı entegre ederek görsel verileri yorumlayabilen ve sözlü olarak yanıt verebilen kapsamlı bir sistem oluşturuyor.

</p>


https://github.com/ZohaibAhmed/real-gemini/assets/660224/9ab3bd22-4c26-4947-9646-d2085b22725f



## Features
- **Visual Question Answering**: Uses GPT-4 Vision to interpret images from a camera feed and answer questions related to the visual content.
- **Görsel Soru Yanıtlama**: Kamera görüntülerini yorumlamak ve görsel içerikle ilgili soruları yanıtlamak için GPT-4 Vision kullanır.
- **Voice Recognition**: Employs Whisper for accurate speech-to-text conversion, allowing users to ask questions verbally.
- **Ses Tanıma**: Doğru konuşmayı metne dönüştürmek için Whisper'ı kullanır ve kullanıcıların soruları sözlü olarak sormasına olanak tanır.
- **Voice Synthesis**: Utilizes Resemble AI for generating realistic voice responses, enhancing the interactive experience.
- **Ses Sentezi**: Gerçekçi sesli yanıtlar oluşturmak için Resemble AI kullanır ve interaktif deneyimi geliştirir.


## Prerequisites
- Python 3.x
- Camera hardware compatible with your system (Sisteminizle uyumlu kamera donanımı)
- Microphone and speaker setup for voice input and output (Ses girişi ve çıkışı için mikrofon ve hoparlör kurulumu)

## Installation
1. **Clone the Repository**
   ```bash
   git clone git@github.com:ZohaibAhmed/real-gemini.git
   cd real-gemini
   ```

2. **Install Dependencies**
   Install the required Python packages:
   ```bash
   pip install -r requirements.txt
   ```

3. **Environment Setup**
   - Create a `.env` file in the project root.
   - Add your Resemble AI and OpenAI credentials to the `.env` file:


## Usage
Run the application using the following command:
Aşağıdaki komutu kullanarak uygulamayı çalıştırın:
```bash
python run.py
```
Place the camera in view of the subject and use a microphone to ask questions. The system will process the visual and audio inputs to provide a spoken answer.
Kamerayı konunun görüş alanına yerleştirin ve soru sormak için bir mikrofon kullanın. Sistem, sözlü bir cevap sağlamak için görsel ve işitsel girdileri işleyecektir.


## Contributions
Bu projeye katkılarınızı bekliyoruz. Lütfen önerdiğiniz değişikliklerle birlikte bir çekme isteği oluşturun.

## Acknowledgements
GPT-4 ve Whisper API'leri için OpenAI'ye ve ses sentezleme teknolojileri için Resemble AI'ye özel teşekkürler.

