# mjs_debian
Este é um passo a passo da instalação e da pós-instalação do Debian 11 que
 fiz em minha máquina. Para cada escolha (ou a maioria), vou dar uma explicação
 do porquê fiz ela, além de tentar dar uma explicação para os comandos usados,
 configurações e apresentar sobre os programas instalados. É importante
 ressaltar que estou passando a diante o que eu aprendi, talvez algo não
 esteja correto ou tão bem explicado, e caso identificado alguma informação
 errada ou que possa ser melhorada, gostaria de receber seu feedback e saber
 o que melhorar. Desde já agradeço.

## [Instalação](https://github.com/mutannejs/mjs_debian/tree/master/instalacao)
Possui os passos feitos para instalar o Debian em minha máquina.

É discutido:

- [**Baixando o arquivo ISO**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#baixando-o-arquivo-iso) : qual iso baixar;
- [**Gravando uma mídia**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#gravando-uma-m%C3%ADdia) : como usar o BalenaEtcher para gravar um pendrive bootável;
- [**Mudando a ordem de boot**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#mudando-a-ordem-de-boot) : como fazer o computador ligar no istalador do debian;
- [**Instalando**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#instalando) : instalação do Debian usando modo gráfico;
- [**Exemplos de particionamento**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#exemplos-de-particionamento) : exemplos de particionamento feito usando o instalador do Debian, manual e guiado.

## [Configuração](https://github.com/mutannejs/mjs_debian/tree/master/configuracao)
Possui algumas configurações feitas no sistema antes de instalar novos programas.

É discutido:

- [**GRUB**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#grub) : como aumentar o tempo de espera da tela de escolha do sistema operacional a ser inicializado;
- [**Lightdm**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#lightdm) : como exibir uma lista e usuários na tela de login;
- [**Sudo**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#sudo) : como permitir o usuário usar o comando sudo;
- [**Fstab**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#fstab) : como montar uma partição automaticamente no boot do sistema;
- [**Alias**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#alias) : como criar atalhos para comandos usados no terminal.

## [Aplicativos](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos)
Mostra os primeiros programas e pacotes instalados.

É discutido:

- [**Apt e netselect**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#apt-e-netselect) : como usar o gerenciador de pacotes do Debian e escolher o espelho mais adequado para sua máquina;
- [**Tlp**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#tlp) : usado para economizar bateria no notebook;
- [**Transmission**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#transmission) : leve e simples cliente de BitTorrent;
- [**Blueman**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#blueman) : gerenciador de Bluetooth com interface gráfica;
- [**Conky**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#conky) : monitor de sistema na área de trabalho;
- [**Desenvolvimento**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#desenvolvimento) : ferramentas usadas para programar
	- [**Build-essential**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#build-essential) : necessário para compilar códigos feitos em C e executar arquivos makefile;
	- [**Openjdk-17-jdk**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#opnjdk-17-jdk) : necessário para programar usando Java e executar programas feitos usando essa linguagem;
	- [**Git**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#git) : programa de versionamento muito utilizado por desenvolvedores;
	- [**Geany**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#geany) : IDE leve e simples;
- [**Mpv**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#mpv) : instalar o mpv Media Player no lugar do Parole;
- [**Firefox**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#firefox) : instalando a versão padrão no lugar da ESR;
- [**LibreOffice**](https://github.com/mutannejs/mjs_debian/tree/master/aplicativos#libreoffice) : desinstalar ou adicionar suporte a pt-BR;

## Ferramentas Usadas
**Notion** - para escrever esse documento:

[https://www.notion.so/](https://www.notion.so/)

**Balena Etcher**: para criar uma pendrive bootável com a ISO do Debian:

[https://www.balena.io/etcher](https://www.balena.io/etcher)

**Virtual Box** - para criar uma máquina virtual com o Debian:

[https://www.virtualbox.org/](https://www.virtualbox.org/)

## Referências

**Debian - mais um pouco sobre root, sudo, sudoers, etc.**

[https://www.youtube.com/watch?v=IRHnAsDp9xM](https://www.youtube.com/watch?v=IRHnAsDp9xM)

**Debian - Lista de usuários no login (LightDM)**

[https://www.youtube.com/watch?v=kV3Jywmznko](https://www.youtube.com/watch?v=kV3Jywmznko)

**Como configurar discos e partições no Linux usando FSTAB**

[https://diolinux.com.br/sistemas-operacionais/discos-particoes-linux-fstab.html](https://diolinux.com.br/sistemas-operacionais/discos-particoes-linux-fstab.html)

**Debian - fstab**

[https://wiki.debian.org/fstab](https://wiki.debian.org/fstab)

**Como usar o APT**

[https://www.debian.org/doc/manuals/apt-howto/index.pt-br.html](https://www.debian.org/doc/manuals/apt-howto/index.pt-br.html)

**[Tutorial] Instalando, configurando e inicializando o Git no Linux**

[https://dev.to/womakerscode/instalando-configurando-e-inicializando-o-git-no-linux-2m96](https://dev.to/womakerscode/instalando-configurando-e-inicializando-o-git-no-linux-2m96)

**Instale o Firefox no Linux**

[https://support.mozilla.org/pt-BR/kb/instale-o-firefox-no-linux#w_instale-o-firefox-usando-um-pacote-da-mozilla-para-usuarios-mais-avancados](https://support.mozilla.org/pt-BR/kb/instale-o-firefox-no-linux#w_instale-o-firefox-usando-um-pacote-da-mozilla-para-usuarios-mais-avancados)

**Comandos Linux para instalar programas .tar.gz, tar.bz2, tar.xz no Linux**

[https://sempreupdate.com.br/como-instalar-programas-tar-gz-bz2-xz-no-linux/](https://sempreupdate.com.br/como-instalar-programas-tar-gz-bz2-xz-no-linux/)

**Comando tar no Linux (arquivamento de arquivos) [Guia Básico]**

[https://www.certificacaolinux.com.br/comando-linux-tar/](https://www.certificacaolinux.com.br/comando-linux-tar/)

**Hierarquia de Diretórios no Linux [Guia Básico]**

[https://www.certificacaolinux.com.br/diretorios-e-arquivos/](https://www.certificacaolinux.com.br/diretorios-e-arquivos/)
