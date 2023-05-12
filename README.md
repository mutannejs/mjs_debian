# mjs_debian

Este é um passo a passo da instalação e da pós-instalação do Debian 11 que
 fiz em minha máquina. Para cada escolha (ou a maioria), vou dar uma explicação
 do porquê fiz ela, além de tentar dar uma explicação para os comandos usados,
 configurações e apresentar sobre os programas instalados. É importante
 ressaltar que estou passando a diante o que eu aprendi, talvez algo não
 esteja correto ou tão bem explicado, e caso identificado alguma informação
 errada ou que possa ser melhorada, gostaria de receber seu feedback e saber
 o que melhorar. Desde já agradeço.

## Instalação

Possui os passos feitos para instalar o Debian em minha máquina. É discutido:

- [**Baixando o arquivo ISO**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#baixando-o-arquivo-iso) : qual iso baixar;
- [**Gravando uma mídia**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#gravando-uma-m%C3%ADdia) : como usar o BalenaEtcher para gravar um pendrive bootável;
- [**Mudando a ordem de boot**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#mudando-a-ordem-de-boot) : como fazer o computador ligar no istalador do debian;
- [**Instalando**](https://github.com/mutannejs/mjs_debian/tree/master/instalacao#instalando) : instalação do Debian usando modo gráfico.

## Configuração

Possui algumas configurações feitas no sistema antes de instalar novos programas. É discutido:

- [**GRUB**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#grub) : como aumentar o tempo de espera da tela de escolha do sistema operacional a ser inicializado;
- [**Lightdm**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#lightdm) : como exibir uma lista e usuários na tela de login;
- [**Sudo**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#sudo) : como permitir o usuário usar o comando sudo;
- [**Fstab**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#fstab) : como montar uma partição automaticamente no boot do sistema;
- [**Alias**](https://github.com/mutannejs/mjs_debian/tree/master/configuracao#alias) : como criar atalhos para comandos usados no terminal.

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
