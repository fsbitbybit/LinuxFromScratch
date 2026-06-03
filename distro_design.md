# Distro Explicação

## Conceitos

### Sistema Operacional
É um software que gerencia todos os recursos do computador (processador, memória, disco rígido, impressoras, etc.) e funciona como intermediário entre o usuário e o hardware. Ele permite que você execute programas, acesse arquivos e controle o computador. Exemplos: Windows, macOS, Linux.

### Kernel
O Kernel é o núcleo do sistema operacional — a parte mais importante e privilegiada. Ele gerencia diretamente o hardware, controlando o acesso ao processador, memória, dispositivos periféricos e gerenciando processos. O kernel executa em modo privilegiado (modo kernel) e protege o sistema de acessos não autorizados.

### Shell
O Shell é um interpretador de comandos que funciona como interface entre você e o kernel. Ele recebe comandos digitados (ou scripts) e os traduz para instruções que o kernel possa entender. Exemplos: Bash (Linux), PowerShell (Windows), Zsh (macOS). O shell permite controlar o SO através de linhas de comando.

### firmware
O Firmware é um software de baixo nível armazenado permanentemente em um chip (ROM ou memória flash) do dispositivo. Ele controla operações básicas do hardware antes mesmo do SO iniciar. É responsável por tarefas como testes de memória no boot e gerenciamento de componentes. Exemplo: BIOS em computadores antigos.

### bootloader
O Bootloader é um pequeno programa que executa quando você liga o computador, antes do SO carregar. Sua função é inicializar o hardware básico, localizar o kernel do SO no disco e carregá-lo na memória. Ele funciona como uma ponte entre o firmware e o SO. Exemplo: GRUB (Linux) ou Windows Boot Manager.

## Comandos realizados no terminal e suas explições
```bash
sudo apt update --> Comando busca por atualizações e deixa pronta para a realização do upgrade de versão atual
sudo apt upgrade --> Atualiza os repositórios, aplicações que foram achadas com novas versões pelo sudo apt update

A execução desses comandos é recomendada sempre, mas especialmente antes da instalação de alguma aplicação ou utilidade ou dependencias

sudo apt install -y build essentials instala o compilador de c(boa parte do kernel foi escrita em c), o make, utilizado para automação de builds para tirar de código fonte para binario, e o binutils, uma coleção de ferramentas para operar em arquivos de objeto, inclui o GNU assembler e linker em conjução com o GNU compiler collection(GCC)

sudo apt install -y libncurses-dev instala a tela azul do menuconfig

sudo apt install -y bison

sudo apt install -y flex Lexer generator exigido pelo build do kernel

sudo apt install -y libssl-dev Criptografia para assinatura de módulos do kernel

sudo apt install -y libelf-dev Manipulação de binários ELF

sudo apt install -y bc Calculadora usada pelo Makefile do kernel

sudo apt install -y cpio Empacota o initramfs no formato do kernel

sudo apt install -y wget Baixa arquivos da internet (código-fonte, BusyBox)

sudo apt install -y xorriso Gera a imagem ISO bootável

sudo apt install -y grub-pc-bin Binários do GRUB para boot BIOS (Legacy/MBR)

sudo apt install -y grub-efi-amd64-bin Binários do GRUB para boot UEFI

sudo apt install -y grub-common Ferramentas compartilhadas do GRUB (grub-mkrescue)

sudo apt install -y mtools Manipula imagens FAT (necessário para ISO UEFI)

sudo apt install -y squashfs-tools Cria o filesystem compactado SquashFS (mksquashfs)

sudo apt install -y qemu-system-x86 Emulador de PC completo para testar a ISO sem reiniciar

sudo apt install -y tar 

wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.1.160.tar.xz baixa o kernel linux comprimido em um arquivo tar

sudo tar  -xvf linux-6.160.tar.xz descomprime o kernel baixado via wget
```

## Minha Distro

### Objetivos
O meu objetivo é criar uma distro leve para rodar em qualquer computador, dado o cenário atual da disponibilidade de hardware e, por sua vez, a alta nos preços.
O visual gráfico provavelmente utilizara o hyprland que utiliza o wayland
A segurança vai ser a melhor possível enquanto tento manter a distro leve com login e senha, firewall e criptografia
