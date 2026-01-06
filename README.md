# Klipper-na-BiquBX
Repositório ensinando a instalar o Klipper na BiquBX V3 em português. Me aventurei ao instalar o klipper em minha BiquBX e não encontrei muito conteúdo em português, então decidi fazer o meu próprio.

Muitas referências foram tiradas daqui: 
https://gist.github.com/varazir/f8994b0ebbe4ce2d1e1cdf88fb65621d

Pré-Requisitos:

1- Raspberry Pi 3B ou versões superiores (acredito que suporte até o Pi 4)
2- Cartão SD com 8GB de memória ou mais (na minha impressora utilizo um kingston 32GB e nunca tive problemas)

Perfeito, agora tendo tudo isso em mãos, podemos começar a instalação do nosso klipper!

# Primeiro passo - Instalar o OS no cartão SD

Primeiro, precisamos baixar a seguinte imagem no nosso Pi "2023-05-03-raspios-bullseye-armhf-lite.img.xz", que se encontra dentro deste link:
https://downloads.raspberrypi.com/raspios_lite_armhf/images/raspios_lite_armhf-2023-05-03/
Ou deste link se você quiser uma interface utilizável estilo windows:
https://downloads.raspberrypi.com/raspios_armhf/images/raspios_armhf-2023-05-03/

-"Ai, mas por quê tenho que instalar essa versão velha?"

Muito simples!
Os drivers da tela da BiquBX foram projetados para suportar no máximo essa versão, porém depois de nós instalarmos eles, podemos atualizar sem problemas o nosso OS!

Perfeito, agora depois de baixarmos a imagem pelo site fornecido, agora vamos baixar o RaspberryPi Imager, recomendo baixar a versão que está aqui no repositório para podermos configurar a instalação nessa versão mais antiga.

Após baixar o Imager, conecte seu cartão SD no computador utilizando o adaptador USB que veio com a impressora e abra o programa.

## Ao abrir, você será perguntado se quer atualizar o programa, selecione que não.

<img width="848" height="557" alt="image" src="https://github.com/user-attachments/assets/f4c35015-ab1e-4e76-8233-a2230c7d9836" />

## Aqui vamos escolher nosso dispositivo

<img width="840" height="553" alt="image" src="https://github.com/user-attachments/assets/6efd16a4-8df0-4c7e-aa65-f11c396bf81b" />

## No meu caso, Raspiberry Pi 3 

<img width="843" height="557" alt="image" src="https://github.com/user-attachments/assets/66105d1c-4b2d-4e20-873d-9906c34c7bb2" />

## Agora escolhemos nosso SO personalizado, descendo a página até o final

<img width="847" height="561" alt="image" src="https://github.com/user-attachments/assets/e0511833-0dd4-4ced-b9b1-03e7c4d9b486" />

## Escolhemos nosso armazenamento e formatamos ele se solicitado

<img width="845" height="559" alt="image" src="https://github.com/user-attachments/assets/c789bf3e-0452-47d7-8d7c-5be8657d36f1" />

## Após isso, clicamos em seguinte e editamos as definições de personalização do SO

<img width="845" height="555" alt="image" src="https://github.com/user-attachments/assets/3c8b83dd-ab41-45ac-bc53-459e91b7b52e" />

## Definimos um host local, nome de usuário e senha, SSID e senha da rede

<img width="842" height="561" alt="image" src="https://github.com/user-attachments/assets/35203767-c13f-4a23-80a6-d05f0b348c6e" />

## Descemos e definimos país da rede e fuso horário

<img width="847" height="561" alt="image" src="https://github.com/user-attachments/assets/7c2af8cd-3c65-4233-9ce8-03a73067b089" />

## Vamos para a aba serviços e habilitamos o SSH

<img width="843" height="557" alt="image" src="https://github.com/user-attachments/assets/4e95c2a6-fc00-40d0-a94f-12100756b87c" />

Agora salve e aplique as definições do SO

Após isso, espere terminar e pronto!
Você agora tem um cartão SD com o SO instalado.

# Segundo Passo - Instalar o driver da tela da Biqu BX

## Antes de ligar sua Raspberry Pi, digite o seguinte comando no terminal do seu computador "arp -a", isso nos dará uma lista de IPs da nossa rede local:

<img width="704" height="570" alt="image" src="https://github.com/user-attachments/assets/95650c2a-58e0-4133-93f7-0f92dacc2d29" />

Coloque o cartão SD na sua Raspberry Pi, conecte ela ao usb do seu computador ou de um carregador de celular e espere alguns minutos para instalar tudo.
Após alguns minutos, feche e abra o terminal e então digite o comando "arp -a" novamente no terminal
Provavelmente terá um IP novo na sua lista, no meu caso 192.168.1.171

<img width="1472" height="705" alt="image" src="https://github.com/user-attachments/assets/b889224e-0806-4bb2-942d-a74374400329" />

Agora vamos acessar nossa Raspberry via SSH, ainda no seu terminal, digite ssh "SEU NOME DE USUARIO DEFINIDO NA INSTALAÇÃO DO SO"@IP-DA-IMPRESSORA
Ele vai solicitar uma senha, digite e dê um enter e você estará conectado no sistema da sua impressora:

<img width="1470" height="693" alt="image" src="https://github.com/user-attachments/assets/a8912642-4884-4158-81bd-f2e3dc526e5c" />

Digite o seguinte comando no terminal:

git clone --depth=1 -b RPI-DSI-BXV3 https://github.com/bigtreetech/BIQU-BX.git RPI-DSI-BXV3

Após concluído, digite:

cd RPI-DSI-BXV3
sudo ./install.sh

Se tudo der certo, seu Raspberry irá reiniciar.

