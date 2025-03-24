# PalmSync
Mão Robótica com Reconhecimento de Gestos e Controle por Visão Computacional

# Para rodar em Raspberry Pi

1 - Instalar as Dependencias

sudo apt update && sudo apt upgrade -y
sudo apt install python3-opencv -y

pip3 install mediapipe
# or
pip3 install opencv-python-headless

2 - Testar a Webcam

fswebcam test.jpg
# or
python3 -c "import cv2; cap=cv2.VideoCapture(0); ret,frame=cap.read(); cv2.imwrite('test.jpg', frame); cap.release()"

3 - Criar o Script

nano hand_tracking.py
Cole o código que você já tem e salve (CTRL+X, Y, ENTER).

Se precisar otimizar o desempenho, podemos reduzir a resolução da captura:

cap = cv2.VideoCapture(0)
cap.set(3, 640)  # Largura
cap.set(4, 480)  # Altura

4 - Rodar o código

python3 hand_tracking.py

nice -n -10 python3 hand_tracking.py

5 - Executar Automaticamente no Boot

Se quiser que o código rode ao ligar o Raspberry:
crontab -e

Adicione a linha:
@reboot /usr/bin/python3 /home/pi/hand_tracking.py

Se precisar rodar em uma interface gráfica, pode usar o autostart:
nano ~/.config/lxsession/LXDE-pi/autostart

Adicione:
@lxterminal -e python3 /home/pi/hand_tracking.py