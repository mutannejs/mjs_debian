# Instalação

## Baixando o arquivo ISO

Primeiramente deve ser baixado a ISO do Debian 11, neste caso será baixado a ISO com firmware não livre para instalar em um computador com acesso à internet, assim, durante e após a instalação o sistema já reconhecerá e terá os drivers necessários da placa wifi (efeito do firmware não-livre), e os programas serão baixados durante a instalação, não vindo junto à ISO (por isso a ISO é menor, mas só posso usar ela porque terei acesso à internet durante a instalação).

A partir do site oficial do Debian, deve-se clicar em `Baixar`, em `imagens não-livres não oficiais, incluindo pacotes de firmware`, e seguir o caminho `11.6.0+nonfree`/`amd64`/`iso-cd` para baixar o arquivo `firmware-11.6.0-amd64-netinst.iso`. Após baixar o arquivo é aconselhado verificar a integridade dele, comparando a saída do comando:

```
sha512sum firmware-11.6.0-amd64-netinst.iso
```

Com o conteúdo do arquivo `SHA512SUMS` presente na mesma página da ISO. Outras formas de verificar a integridade da ISO podem ser usadas.

A imagem ISO a ser baixada depende do ambiente que ela será usada:

- **CD**
Irá baixar os pacotes durante a instalação. Pode ser usada se possuir acesso à internet. Possui menos de 700MB.
- **DVD**
Os pacotes já vem dentro da ISO. Deve ser usada quando não há acesso à internet. Possui cerca de 4GB.
- **live**
Há a opção de experimentar o sistema sem a necessidade de instalá-lo.
- **edu**
Uma ISO do Debian feita para o ambiente educacional.
- **firmware**
Imagem (não oficial) com firmwares não livres, necessários para algumas placas de vídeo e de rede.

## Gravando uma mídia

Qualquer programa pode ser usado para gravar a ISO em uma mídia, cd, dvd, ou como em meu caso, um pendrive. O programa escolhido foi o [BalenaEtcher](https://www.balena.io/etcher), por possuir uma interface simples e fácil, além de ter se saído bem na maioria das vezes em que o usei. No linux é necessário dar permissão de execução para o programa:

```
chmod +x balenaEtcher-*-x64.AppImage
```

O caractere `*` está sendo usado para substituir o número da versão, assim o comando pode ser usado para qualquer versão do programa, porém pode-se usar o nome completo sem problemas.

Ao abrir o programa, o que precisamos fazer é selecionar a ISO a ser gravada em `Flash from file` e depois a mídia que será usada em `Select Target`, por fim basta clicar em `Flash`.

![gravando_uma_midia.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/gravando_uma_midia.png)

## Mudando a ordem de boot

Com a mídia gravada, deve-se rebootar a máquina e fazer o boot pelo pendrive. Para fazer boot pelo pendrive (e não pelo disco, como de costume) deve-se clicar em uma certa tecla na hora que o computador estiver ligando para acessar o SETUP do firmware UEFI, normalmente é uma das teclas a seguir:

**Del**, **Esc**, **F2**, **F6**, **F8**, **F12**, ou uma combinação com **Ctrl**+**Alt**+**(outra tecla)**

Como para cada computador essa tecla pode mudar, o importante é pesquisar na internet ou prestar atenção na primeira tela que aparecer ao ligar o pc (algumas telas mostram informações sobre o hardware, e como acessar o SETUP) para descobrir a tecla ou combinação que deve ser usada. *Em minha máquina a tecla é **F2**.*

Acessado o SETUP, deve-se procurar a seção de BOOT, e em `Boot Priority Order` colocar o dispositivo de pendrive em primeira opção. Por fim basta salvar e sair.

## Instalando

Antes, é importante ressaltar que os prints nessa seção foram feitos usando uma máquina virtual no [VirtualBox](https://www.virtualbox.org/), portanto alguns detalhes podem ser diferentes de uma instalação real, tanto nos prints, quanto na descrição geral dos passos. Porém foi tentado replicar e explicar os passos de uma instalação real o mais fidedigno possível.

Reiniciado a máquina cairemos nessa tela:

![instalando_01.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_01.png)

Em seguida:

1. Escolha a opção `Grafical install`.
2. Escolha o idioma para usar no sistema, caso escolha `Português` deve-se escolher `Brasil` em seguida. *Na instalação foi escolhido `English`*.
3. Escolha o local (seu país), as opções que aparecerão são com base no idioma escolhido, então caso ele tenha sido `English`, para selecionar `Brasil`, primeiro é necessário selecionar `other`, depois `South America`, e por fim `Brazil`.
4. Escolha o padrão de codificação para o idioma escolhido, para português escolha `pt_BR.UTF-8`, para inglês escolha `en_US.UTF-8`.
5. Escolha o tipo de teclado que deve ser usado pelo seu sistema, normalmente é brasileiro.
6. A internet será configurada, sendo necessário escolher a interface de rede que será usada durante a instalação (wifi ou cabeada), a interface wifi normalmente tem seu nome iniciado por `w` e a cabeada por `e`.
7. Escolha o nome do Computador, como sugestão o instalador já coloca o próprio nome da distribuição, ou seja `debian`, porém pode-se escolher o nome que preferir. Depois escolha o nome do domínio usado na rede, caso vc não vá usar um domínio específico pode-se escolher qualquer nome. *Na instalação o nome do computador foi setado como `debian`, e o domínio como `debian.dom`*.
8. Escolha a senha que será usada para o usuário `root`.
9. É necessário criar um usuário padrão, primeiro deve-se informar seu nome completo, e em seguida seu apelido. Por fim, informe a senha que será usada por ele.
10. Escolha o Estado que você mora para configurar a zona horária do sistema.
11. Será necessário escolher as partições do disco que serão usadas pelo sistema usando o particionamento do instalador. Existe dois principais modos, o guiado e o manual. É importante notar que o instalador não executará nenhuma das escolhas do usuário caso ele não as confirme (depois de particionar o disco será perguntado se o usuário concorda com as modificações feitas), o particionamento do disco pode intimidar o usuário, mas se feito com atenção e lendo as mensagens não haverá nenhum problema:

Caso use o modo de **particionamento guiado**:
Caso o disco esteja totalmente vazio, o sistema será instalado usando todo ele (`Guided - use entire disk`), caso não esteja, será usado a maior parte livre do disco (`Guided - use the largest continuous free space`). Dev-se escolher se o sistema usará apenas uma partição para tudo (o padrão), se usará a `/home` separada, ou se usará a `/home`, a `/var` e a `/tmp` separadas. Em todos os casos será criado também uma partição de SWAP. Após escolher deve-se clicar em `Finish partitioning and write changes to disk`, e na próxima tela selecionar `Yes` e depois clicar em `Continue`.

Caso use o modo de **particionamento manual**:
É necessário escolher qual é a partição de sistema EFI (onde está guardado os dados necessários para iniciar os sistemas operacionais instalados máquina) do disco, e qual partição será usada como raiz do novo SO. Opcionalmente pode-se escolher uma partição para usar como SWAP, e uma partição para usar a /home separada (o mesmo pode ser feito para outros diretórios).
Se as partições forem criadas a partir de um espaço livre do disco (se já existir um SO instalado na máquina, a partição de sistema EFI já existirá, sendo a primeira partição do disco), para cada uma deve-se escolher o tamanho dela, se ela vai ser criada no início ou no fim da parte livre do disco escolhida, qual o seu tipo (`EFI`, `ext4`, `swap area`, ou outro tipo) e setar onde ela será montada (`/`, `/home`, ou outra de sua escolha).
Em `Use as` deve ser escolhido o tipo da partição, recomendado usar `ext4 journaling file system` para a raiz e para a `/home`, para a partição SWAP usar `swap area`, e para a partição de sistema `EFI` usar `EFI System Partition`.
Para setar onde a partição será montada deve-se alterar a informação em `Mount point`. A partição principal do sistema deve ser setada como `/`, a partição de sistema EFI e a SWAP não possuem essa opção. Pode-se setar uma partição como `/home` caso queira usar a /home separada da raiz, e para usar também outras pastas separadas basta fazer o mesmo em outra partição.

No fim dessa seção (**Instalando**), há exemplos tanto do particionamento guiado, quanto manual.

12. Terminando o particionamento a instalação da base do sistema base é iniciada.
13. Ao terminar de instalar a base do sistema é necessário configurar o gerenciador de pacotes. Para isso deve-se informar o país em que você mora e o espelho que deseja usar, ao escolher `Brasil` por padrão é recomendado usar o espelho `deb.debian.org`.
14. Informe o proxy usado, caso não use apenas deixe em branco e prossiga.
15. É iniciado a instalação dos pacotes além da base do sistema.
16. Após a instalação de alguns pacotes deve-se informar se é desejado enviar estatísticas dos pacotes mais utilizados no sistema. Essa escolha como a maioria feita durante a instalação podem ser modificadas após a conclusão dela. *Na instalação foi escolhido enviar*.
17. Logo em seguida é necessário informar quais coleções de pacotes deseja-se instalar. Por padrão é instalado `Debian desktop environment`, `Gnome` e `standard system utilities`, porém pode-se desmarcar qualquer uma delas, e/ou marcar outras. *Na instalação foi desmarcado `Gnome` e marcado `Xfce` (essas duas se referem principalmente ao visual da interface gráfica do sistema, sendo o `Xfce` mais simples e mais leve)*.
18. É baixado e instalado o restante dos pacotes. O `GRUB boot loader` é instalado e configurado e a instalação do sistema é finalizada.
19. Pronto, seu Debian foi instalado.
20. Para usar seu novo sistema, basta clicar em `Continue` e retirar o pendrive (ou alterar a ordem de boot para iniciar primeiro o HD) antes da máquina ligar.

## Exemplos de particionamento

Nos exemplos vamos considerar um disco de aproximadamente 20 GB, onde já existe duas partições, uma com 500 MB (a partição de sistema EFI), e outra com 4.5 GB (que não queremos mexer). Esse é um ambiente semelhante a quando já temos um sistema operacional instalado na máquina e queremos fazer um dual boot. Após escolhermos a zona horária cairemos na seguinte tela:

![instalando_02.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_02.png)

Se o disco estivesse totalmente vazio não teríamos a opção `Guided - use the largest continuous free space`, o recomendado seria usar então `Guided - use entire disk` ou o modo `Manual`.
Após escolher a opção que queremos é necessário escolher o disco:

![instalando_03.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_03.png)

**guiado**:

Deve-se escolher se todo o sistema será instalado em apenas um partição, se a `/home` usará uma partição separada, ou se a `/home`, a `/var` e a `/tmp` usarão uma partição separada. Em todos os casos também será criada uma partição para a SWAP.

![instalando_04.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_04.png)

Depois será mostrado como as partições ficaram:

![instalando_05.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_05.png)

Na imagem a cima temos 4 partições, sendo as duas últimas as partições criadas pelo sistema de particionamento para instalar o Debian, há também dois espaços livres no disco de `1 MB` que são criados automaticamente. Cada linha possui a ordem da partição no disco, o tamanho dela, se ela é bootável, se ela foi formatada, o tipo dela, e onde ela será montada:

- A primeira (demarcada por `#1`) é a partição de sistema EFI que já estava criada, porém ela vai ser modificada para ao reiniciar a máquina termos acesso ao nosso novo sistema. Após o tamanho da partição temos a letra `B`, indicando que ela é bootável, depois a letra `f`, indicando que ela será formatada, e depois a abreviação `ESP` (abreviação para EFI System Partition).
Em uma instalação real, em vez de `f` teríamos `K`, e após `ESP` poderia existir um comentário sobre o objetivo da partição.
- A segunda (demarcada por `#2`) é a partição de `4.5 GB` que não queríamos modificar (podemos ver que ela não foi modificada, porque diferentemente da partição de sistema EFI, após o tamanho da partição não temos a indicação de que ela foi formatada);
- A terceira partição (demarcada por `#3`) é a raiz do sistema (após o tipo do sistema temos o caractere `/` que nos indica onde ela será montada, ou seja, na raiz);
- A quarta partição é a SWAP.

Caso queira você pode fazer alguma modificação manualmente nesse estado do particionamento, como redimensionar alguma partição. Para confirmar devemos clicar em `Finish partitioning and write changes to disk`, mas as modificações ainda não foram feitas. Será mostrado as partições que de fato foram modificas, e para confirmar se tudo está certo deve-se selecionar `Yes` e depois clicar em `Continue`.

![instalando_06.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_06.png)

Até está tela nenhuma modificação no disco tinha sido feita de verdade, porém ao clicar em Continue elas serão executadas e não haverá mais volta.

**manual**:

Cairemos em uma tela para criar ou modificar as partições no disco:

![instalando_07.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_07.png)

Na imagem a cima temos 2 partições já criadas, que não modificaremos, há também um espaço livre no disco de `1 MB` que é criado automaticamente, e um espaço livre de `16.5 GB` onde criaremos as partições para usar com o Debian. Cada linha possui a ordem da partição no disco, o tamanho dela, se ela é bootável, se ela foi formatada, o tipo dela, e onde ela será montada:

- A primeira (demarcada por `#1`) é a partição de sistema EFI que já estava criada, porém ela vai ser modificada para ao reiniciar a máquina termos acesso ao nosso novo sistema. Após o tamanho da partição temos a letra `B`, indicando que ela é bootável, depois a letra `f`, indicando que ela será formatada, e depois a abreviação `ESP` (abreviação para EFI System Partition).
Em uma instalação real, em vez de `f` teríamos `K`, e após `ESP` poderia existir um comentário sobre o objetivo da partição.
- A segunda (demarcada por `#2`) é a partição de `4.5 GB` que não queríamos modificar (podemos ver que ela não foi modificada, porque diferentemente da partição de sistema EFI, após o tamanho da partição não temos a indicação de que ela foi formatada);

Neste exemplo criaremos uma partição para a raiz do sistema de `12.5 GB`, e uma partição SWAP de `4 GB`.

Primeiramente deve-se clicar na linha com `16.5 GB` de espaço livre, depois em `create a new partition`, escolher o tamanho da partição (`12.5 GB`), escolher criar a partição no início do espaço livre (`Beginning`) e setar os dados como raiz do sistema:

![instalando_08.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_08.png)

![instalando_09.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_09.png)

![instalando_10.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_10.png)

Para setar a partição como raiz do sistema, devemos em `Use as` escolher `ext4 journaling file system` (esse é o tipo que será usado na partição), ele já vem selecionado por padrão, não sendo necessário alterar; e em `Mount point` escolher `/` (the root file system), que também já vem selecionado por padrão. Se essas opções já estiverem selecionadas basta clicar em `Done setting up the partition` para criar a próxima partição. A partição raiz deve ficar desse jeito:

![instalando_11.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_11.png)

![instalando_12.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_12.png)

Para criar a partição SWAP basta clicar na última partição livre e fazer os mesmos passos feitos para setar a raiz, porém em `Use as` escolher `swap area`:

![instalando_13.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_13.png)

![instalando_14.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_14.png)

Para confirmar devemos clicar em `Finish partitioning and write changes to disk`, mas as modificações ainda não foram feitas. Será mostrado as partições que de fato foram modificas, e para confirmar se tudo está certo deve-se selecionar `Yes` e depois clicar em `Continue`.

![instalando_15.png](https://github.com/mutannejs/mjs_debian/blob/master/imagens/instalando_15.png)

Até está tela nenhuma modificação no disco tinha sido feita de verdade, porém ao clicar em `Continue` elas serão executadas e não haverá mais volta.
