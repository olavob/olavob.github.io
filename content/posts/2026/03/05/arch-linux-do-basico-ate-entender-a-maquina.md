---
date: 2026-03-05T16:08:42-03:00
draft: false
title: "Arch Linux: Do Básico Até Entender a Máquina (com todos os porquês)"
type: "post"
tags: ['archlinux', 'linux', 'aprendizado', 'rant', 'instalação', 'tutorial', 'computer-science', 'sistemas-operacionais', 'devops', 'guia']
layout: default
comments: true
---

Antes de começar o Post irei fazer dois ["Rants"](https://www.merriam-webster.com/dictionary/rant) que vejo que são necessários para complementar o ponto de vista de dois tipos de iniciantes que procuram aprender Linux, onde nesse caso obviamente vou dividir e generalizar os iniciantes em geral para simplificar a explicação do argumento, mas deixando claro que não é possível logicamente falar de todo o tipo de pessoas que existe no planeta. 

Cada indivíduo pode ter sua capacidade e dificuldade físicas e psicológicas para realizar uma determinada tarefa.

# Rant: Todo Iniciante tem a Capacidade de Aprender algo Relativamente Complexo?

Para um iniciante em [Linux](https://pt.wikipedia.org/wiki/Linux) ou qualquer outra atividade que exija prática e raciocínio, costumo pensar que existem dois grupos, o iniciante que sabe o básico de um assunto, seja ele o básico a trivial em programação ou qualquer outra atividade, e o iniciante simplesmente curioso, que acabou de sair de um sistema operacional estático como o Windows ou qualquer outro lugar confortável e seguro onde passou a vida toda e quis aprender algo que achou interessante, seja, nesse caso, aprendendo um novo sistema operacional. 

Existe uma diferença drástica entre os dois grupos.

O primeiro tem a motivação de seguir uma carreira de verdade e se esse cara pelo menos "debugou" alguma função que ele achou particularmente complexa, tendo a lógica de como um computador funciona de verdade, linha por linha, instrução por instrução, byte a byte, esse tipo de iniciante está "anos luz" à frente dos outros.

Ou seja, para o iniciante que teve uma experiência envolvendo essa atividade, ele vai estar naturalmente à frente, e isso é um fato.

Essa diferença é fundamental e não vale apenas a computação em especifico, mas para qualquer tarefa que exija raciocínio e prática. 

É o que faz um grupo desistir e o outro não, mas claro, toda regra tem uma exceção, e o fator que equilibra os dois grupos é a Curiosidade.

A simples curiosidade de fazer uma pergunta pra si mesmo ou para o outro é uma [prática de aprendizado eficaz](https://tilt.colostate.edu/the-socratic-method/), essa pessoa nem precisa ter a capacidade de resolver sua dúvida ou crise, mas ela apenas dando opinião, fortalece a sua própria visão analítica dos fatos. 

A curiosidade de procurar novas informações e de se perguntar o que está errando é o que define, quem desiste fácil mesmo tendo todo o potencial do mundo, de quem fica, aprende e persiste mesmo com toda a dor de aprender.

E é isso que significa aprender uma [distribuição](https://pt.wikipedia.org/wiki/Distribui%C3%A7%C3%A3o_Linux) como o Arch Linux, é preciso fuçar a wiki. Ser curioso.

# Rant: O Programador Realmente precisa aprender Linux?

Essa pergunta é fácil de responder, um motorista precisa aprender mecânica? a resposta é não. Mas isso tornaria ele melhor no que faz? aí a resposta muda completamente... 

No mesmo sentido em que o motorista possa ser o melhor piloto do mundo, se o carro quebrar quem ele chama? um mecânico. Agora o programador pode ser o melhor especialista em linguagem de programação X do mundo, se o sistema remoto da empresa der pau, quem ele chama? a mãe? o chefe, que vai descobrir sua incompetência? o time de produto e marketing que não faz a mínima ideia do que ele está falando? ou o outro programador que vai saber resolver esse problema, e logo vai ganhar mais destaque e aumento? Esse cenário pode parecer fictício mas pode ocorrer em empresas pequenas, que apenas contém 1 programador ou um time de 3 ou 4 no máximo, essas empresas são a base da escada, é o primeiro emprego de todo programador iniciante, Em empresas grandes existem profissionais especializados nisso, chamados de DevOps, mas essa não é a realidade de muitos ambientes de trabalho.

O verdadeiro prejuízo está na capacidade de resolver problemas e de criar soluções próprias. 

Quando digo "especialista em linguagem X" como Python, Javascript, C++ ou até Java, não quero dizer que ele seja bom especificamente por isso, até uma criança pode digitar código, uma IA consegue, sua tia consegue, uma Linguagem de Programação é útil mas é apenas uma ferramenta, é um jeito de enviar instruções a um computador e ponto. 

Um programador que fica apenas digitando código de [alto nível](https://www.dio.me/articles/linguagens-de-programacao-de-alto-e-baixo-nivel), ficando apenas no Windows e não sabe matemática, está limitando a sua carreira. Por que se limitar tão cedo estando no início dela?

Lógica de programação é necessária mas não chega nem a ser o básico do básico, é apenas o essencial, é como aprender a ler sem saber escrever. Por isso não incentivo o uso da PseudoLinguagem como o [Portugol](https://pt.wikipedia.org/wiki/Portugol) aprender lógica é trivial, e não faz sentido dar a um iniciante uma ferramenta que é apenas para isso, e que pode acostumá-lo com vícios como os de [Más Práticas de Programação](https://pt.wikipedia.org/wiki/Boas_pr%C3%A1ticas_de_programa%C3%A7%C3%A3o), já que não é uma linguagem de verdade, pode ser considerada uma perda de tempo completa.

Salvo engano apenas as pessoas que realmente têm uma Dificuldade em raciocínio e lógica, para isso o Portugol pode ser um ótimo ponto de partida.

O simples fato de estudar Linux e  [Linguagens de baixo nível](https://minutodaseguranca.blog.br/importancia-da-linguem-de-programacao-de-baixo-nivel/), é para ajudar no desenvolvimento da capacidade cognitiva e na melhoria expressiva da qualidade do código feito. Ajudar o desenvolvedor a ter um outro campo de visão a pensar fora da caixa. Um programador que fica apenas no superficial não tem segurança e otimização, não tem noção de que o Python ou o Javascript dele esteja consumindo 150% a mais do que deveria de memória e performance, coisas que em [Escalabilidade Vertical](https://aerospike.com/blog/vertical-vs-horizontal-scaling/) de um [Deploy](https://olavodotpy.github.io/posts/2024/12/17/colocando-em-producao-um-projeto-django-fazendo-deploy-no-railway/) custa dinheiro e pode dar prejuízo em dívidas.

Em um Linux ou sistemas mais complexos você é obrigado a pensar em uma coisa muito chata chamada de Escalabilidade, recurso não é infinito é finito e custa $.

Um exemplo: vamos criar um arquivo de qualquer linguagem mesmo, mas primeiro vamos para a pasta temporária do Linux para não poluir os diretórios: ```cd /tmp``` onde o comando `cd` significa: Change Directory.

Uma vez lá dentro vamos "tocar" ou criar um arquivo: `touch teste.rb` e vamos abrir e uma IDE ou um editor via CLI que significa interface em linha de comando, aqui vou utilizar o VIM, `vim teste.rb`. 

vou agora escrever uma função trivial em Ruby de "hello world".

```ruby

def teste
    puts "hello world"
end

teste
```

Para uma pessoa que apenas ficou no superficial isso basta, é realmente algo super simples, porém sua visão sobre esse código continua limitada por mais simples que ele seja.

Agora salvamos e saímos com `:wq!` uma vez fora do editor e dentro do nosso diretório, executaremos `xxd -g1 arquivo` com a saída disso, temos algo mais complexo. 

![](https://i.ibb.co/QjY4H60b/Captura-de-tela-2026-03-03-022733.png)

Uma mudança radical no campo de visão do programador, agora é o mesmo código mas representado em [Hexadecimal](https://pt.wikipedia.org/wiki/Sistema_de_numera%C3%A7%C3%A3o_hexadecimal), o mais próximo de como seria em uma [escovação de bit](https://pt.stackoverflow.com/questions/92755/de-onde-vem-a-express%C3%A3o-escovar-bits-e-qual-o-equivalente-em-ingl%C3%AAs). Na esquerda contendo o Offset em Bytes, ou seja a posição em Bytes do conteúdo do arquivo, de 0...0 até 0...10 é 16 Bytes, em exa 16 = 10.

Na direita as letras são representadas também em Hexadecimal, se observar bem, veremos o  conteúdo original do arquivo: 65 em exa é a letra "e" no meu código, tendo cada caractere 1 Byte. 

Agora executando `xxd -b arquivo` veremos tudo em Binário. 

![](https://i.ibb.co/B8k0PdW/Captura-de-tela-2026-03-03-025556.png)

Tendo cada caractere representado por um Byte, cada Byte contendo 8 Bits. 

Essa série de comandos que exemplifiquei é uma forma de enxergar o código bem simples mas com outros olhos, não em uma camada tão superficial como apenas a sintaxe funcional e o resto "mágica", mas sim que a sintaxe vira caracteres, encode, bytes e bits. porém não se empolgue, isso é apenas a Pré-introdução de Programação de baixo nível. Para saber mais recomendo assistir esse [vídeo do Fabio Akita](https://www.youtube.com/watch?v=Gp2m8ZuXoPg).

# Introdução ao Arch Linux

Depois desse longo RANT, vimos que um iniciante pode ser capaz de aprender Arch, apenas tendo a curiosidade de pesquisar e de perguntar para si mesmo o porquê de algo acontecer.

Logo após expliquei a importância para o programador conhecer sua própria máquina, o programador tem que dominar a máquina, não a máquina dominar o programador. 

E finalizando a reflexão, dei um exemplo de como o campo de visão do desenvolvedor pode aumentar apenas saindo da sua zona de conforto, o alto nível é fácil e prático, nenhum programador precisa de fato sair dele no seu dia a dia de trabalho, porém isso limita tanto sua carreira e potencial de ganho quanto sua habilidade de obter a melhor solução com mais eficiência e economia.     

Agora vamos começar o post de verdade. 

Nesse post vou mostrar passo a passo da instalação do [Arch Linux](https://archlinux.org/), levando em consideração que vou seguir o tutorial do [ArchWIKI](https://wiki.archlinux.org/title/Main_page) e explicarei algumas armadilhas que um iniciante iria facilmente cair. 

Para deixar bem claro irei fazer a instalação em uma [Máquina Virtual](https://pt.wikipedia.org/wiki/M%C3%A1quina_virtual) no meu caso usarei o [Virtual Box](https://www.virtualbox.org/), então irei pular alguns passos da instalação básicas, já que não preciso me preocupar com alguns drivers como as de rede, porque o Virtual Box transfere a rede via Ethernet do meu host no caso o meu Windows 11 para o ambiente isolado.

## Pré-Instalação - Instalando a ISO, Executando os Primeiros Comandos 

![](https://www.controle.net/novo/assets/img/faq/imagem-iso-faq-o-que-e-uma-imagem-iso-controlenet.webp)

Instalar a [ISO](https://archlinux.org/download/) é o primeiro passo para começar no Arch, mas o que é ISO? um arquivo `.iso` é uma cópia perfeita do conteúdo presente nas mídias de instalações como CD e DVD. Ou seja, é um arquivo de imagem de instalação do OS(Sistema Operacional) no caso o Arch Linux.

Na página de Download recomendo você instalar por [qBitTorrent](https://www.qbittorrent.org/download) pelo link do Magnet. Uma vez instalado é só você colocar na sua máquina virtual ou [queimar um Pendrive](https://rufus.ie/pt_BR/) para fazer o processo diretamente na sua máquina local. Porém recomendo que se o Linux for uma novidade, fique por enquanto na máquina virtual, seja você qualquer um dos dois grupos que citei antes, a chance de fazer algo errado e estragar o seu sistema é bem alta, até mesmo sendo programador já experiente. 

Todo iniciante em Linux vai quebrar o sistema. Então recomendo começar em um ambiente separado para teste e aprendizado.

### GPT vs MBR

Para quem vai queimar Pendrive, é importante saber a diferença entre esses dois e quando escolhe-los'

Para saber mais sobre [Tabela de Partição](https://wiki.archlinux.org/title/Partitioning_(Portugu%C3%AAs)#Tabela_de_parti%C3%A7%C3%A3o), pode ler o guia, porém saibam que existe apenas essas três formas, o MBR, GPT e o disco sem particionar.

MBR é bem antigo e quase nunca usado por distros novas, e você apenas vai utiliza-la em placa-mãe que usam BIOS, fora isso use GPT. 

Use GPT se você estiver usando UEFI, não use MBR.

Para saber melhor qual usar, [consulte isso](https://wiki.archlinux.org/title/Partitioning_(Portugu%C3%AAs)#Tabela_de_Parti%C3%A7%C3%A3o_GUID)

[UEFI](https://www.lenovo.com/br/pt/glossary/uefi/) que para quem não sabe é o novo firmware moderno substituto da clássica [BIOS](https://pt.wikipedia.org/wiki/BIOS)(Sistema de Entrada e Saída Básico) que carrega o kernel e os drivers. A escolha dessas tabelas é essencial e pode influenciar na sua instalação. 

Para saber se seu [disco está em GPT ou MBR](https://www.youtube.com/watch?v=vjLdwIbv4Pk) 

Assim que configurar a Máquina virtual e começar o processo de inicialização da ISO, vai aparecer a seguinte tela

![](https://i.ibb.co/3mQbMWD1/Captura-de-tela-2026-03-03-222050.png)

Selecionaremos a primeira opção pois estamos usando uma imagem ISO e não uma imagem NETBOOT.

Na primeira opção temos a palavra: x86_64 pois essa é a arquitetura do meu processador, que pode variar dependendo do seu hardware, se o seu processador for de 32 Bits que seria o i386, você deverá instalar uma ISO própria para ela na página de download.

![](https://i.ibb.co/ZzPRpdyY/Captura-de-tela-2026-03-03-203923.png)

Agora que selecionamos a primeira opção essa é a nossa próxima tela, e leia atentamente, estamos logados no usuário `root` chamado de `archiso` e seguindo temos os comandos para conexão de Wi-Fi no [terminal `iwctl`](https://wiki.archlinux.org/title/Iwd_(Portugu%C3%AAs)#iwctl) e também para Modem, e no final a mensagem pede para se conectar a internet para o guia online de instalação.

Muito bem, é aqui que muito iniciante simplesmente PARA. 

Porque é simplesmente um sistema Arch Linux em um usuário root que está com um ambiente relativamente "pronto". E para muitos é isso, mas é aqui que começa a instalação real do OS.

Agora podemos verificar o modo de inicialização com o comando: 

```
cat /sys/firmware/efi/fw_platform_size
```

Esse comando vai especificar se iniciamos com a arquitetura de UEFI de 64 ou 32 Bits, se retornar `Arquivo/Ficheiro ou diretório inexistente` quer dizer que o sistema foi iniciado no modo BIOS.

Antes de prosseguirmos para o próximo tópico, recomendo os seguintes comando para fazer nesse inicio de instalação:

Esse comando vai poupar seus olhos, ele vai acessar `/usr/share/kbd/consolefonts/` e vai trocar e aumentar a fonte do console:

```
setfont ter-132b
```

Esse comando vai mudar o layout do teclado para o padrão Brasileiro:

```
loadkeys br-abnt2
```

Esse comando é um pouco mais avançado, mas vai definir o idioma e o padrão de [codificação UTF-8](https://pt.wikipedia.org/wiki/UTF-8), vai precisar que você [descomente](https://en.wikipedia.org/wiki/Comment_(computer_programming)) `pt_BR.UTF-8 UTF-8` em `/etc/locale.gen`.

```
# Abra o arquivo .gen com VIM ou nano e remova o "#" no começo da linha "pt_BR.UTF-8 UTF-8"
vim /etc/locale.gen
# ou
nano /etc/locale.gen
```

E gere-os com:

```
locale-gen
export LANG=pt_BR.UTF-8
```

Esse conjunto de comandos estão no [Guia de instalação](https://wiki.archlinux.org/title/Installation_guide_(Portugu%C3%AAs)#Inicializar_o_ambiente_live). e serve para configurar o ambiente live, não sabe o que é esse ambiente? vamos falar dele agora.

## Comandos Básicos de um Linux

Como uma forma de guiar quem realmente nunca tocou em um terminal, aqui estão os 30 comandos mais usados e descritos um por um.

```
ls -la
# Lista arquivos e diretórios no formato longo incluindo ocultos, exibindo permissões, dono, tamanho e data.

cd /caminho
# Altera o diretório de trabalho atual para o caminho especificado (relativo ou absoluto).

pwd
# Exibe o caminho absoluto do diretório de trabalho corrente.

cp -r origem destino
# Copia arquivos ou diretórios recursivamente de origem para destino.

mv origem destino
# Move ou renomeia arquivos e diretórios.

rm -rf alvo
# Remove arquivos ou diretórios recursivamente sem confirmação (uso crítico, pode apagar todo o sistema se não usado com atenção)

mkdir -p diretorio
# Cria diretórios, incluindo diretórios pais caso não existam.

touch arquivo.txt
# Cria um arquivo vazio ou atualiza seus timestamps.

cat arquivo.txt
# Exibe o conteúdo de um arquivo no stdout.

less arquivo.txt
# Visualiza arquivos grandes de forma paginada com navegação interativa.

head -n 20 arquivo.txt
# Mostra as primeiras N linhas de um arquivo.

tail -n 50 arquivo.log
# Mostra as últimas N linhas de um arquivo (use -f para acompanhar em tempo real).

grep -R "padrao" .
# Busca recursivamente por um padrão dentro de arquivos.

find /caminho -type f -name "*.py"
# Localiza arquivos conforme critérios como nome, tipo ou extensão.

chmod 755 arquivo.sh
# Modifica permissões de acesso usando notação octal.

chown usuario:grupo arquivo
# Altera proprietário e grupo de um arquivo ou diretório.

ps aux
# Lista todos os processos em execução com detalhes.

top
# Monitor interativo de processos em tempo real.

sudo comando
# Executa um comando com privilégios administrativos.

tar -czvf arquivo.tar.gz pasta/
# Compacta e empacota arquivos/diretórios em formato .tar.gz.

echo "texto"
# Imprime texto no stdout ou redireciona saída para arquivos.

> arquivo.txt
# Redireciona saída padrão para um arquivo (sobrescreve).

>> arquivo.txt
# Redireciona saída padrão para um arquivo (append).

|
# Pipe: envia a saída de um comando como entrada para outro.

man comando
# Exibe o manual detalhado de um comando.

history
# Mostra o histórico de comandos executados no shell.

clear
# Limpa o terminal.

df -h
# Exibe uso de espaço em disco em formato legível.

du -sh pasta/
# Mostra o tamanho total de um diretório.

wget URL
# Faz download de arquivos via HTTP, HTTPS ou FTP.
```

Mas é importante dizer que toda distribuição Linux segue o padrão [POSIX](https://pt.wikipedia.org/wiki/POSIX) ou seja, todo comando é o mesmo independente de qual Linux estamos usando.

E também devemos saber que existem a [Interface Shell](https://pt.wikipedia.org/wiki/Shell_do_Unix#) que é o intermediário entre o Kernel e o usuário, ou seja é o local onde vamos executar cada [comando](https://pt.wikipedia.org/wiki/Texto_simples), como fizemos acima. Acessamos cada shelll pelo [Emulador de Terminal](https://en.wikipedia.org/wiki/Terminal_emulator) e pelo [Run Level de CLI](https://mateusmuller.me/2017/09/10/dica-de-lpic-1-o-que-e-e-como-funciona-o-runlevel-no-linux/) para executarmos os comandos.

Existem muitos shell's diferentes porque cada um deles é uma linguagem de comando e de script(Para automatização), tendo cada um mais modernidade e funcionalidades diferentes. 

Saibam também que existe o shell Gráfico que seria o [Ambiente Gráfico](https://pt.wikipedia.org/wiki/Ambiente_de_%C3%A1rea_de_trabalho) ou GUI. Um exemplo de shell GUI seria sua área de trabalho ou gerenciador de arquivos no Windows, o Windows shell. Mais tarde falaremos sobre interface gráfica e servidor de display.

O shell mais comum é o [BASH](https://pt.wikipedia.org/wiki/Bash), porém existem outros como ZSH, SH, Korn Shell, C Shell e Bourne Shell.

Para saber qual Linguagem de comando seu terminal usa, execute:

```
echo $SHELL
```

## Arch Linux: Seguindo o Coelho na Cartola e Chegando na Mulher de vermelho da Matrix

![](https://i.ibb.co/Pb3rk0F/Untitled-2026-02-27-0120.png)

Esse slide eu mesmo criei no [Excalidraw](https://excalidraw.com/) e é uma forma de representar visualmente o processo de instalação do Arch no Ambiente Live/Live CD, pode parecer complicado, mas se dividirmos em partes dá para entender, por isso vou explicar com calma cada ponto, e depois falarei do fluxo e como vamos juntar cada um deles para fazer a instalação.

### Ambientes Live ou LiveCD

É um sistema que vem pré-pronto juntamente com a imagem ISO ou com o CD de instalação, lá temos todo o suporte para fazer partições, transferir pacotes e acessar o usuário root archiso para configuração avançada do sistema. Em um Sistema Operacional como o Windows isso é feito de forma automática, não precisamos criar, formatar e montar a partição ``c:\``. Em outras distros Linux esse processo é automatizado pelo [calamares](https://en.wikipedia.org/wiki/Calamares_(software)) que é um software de instalação de Linux.

### Partição Principal

 É o espaço que dedicamos para o nosso sistema operacional, é recomendável que um OS Linux tenha 60G para cima de espaço disponível durante sua instalação. Falaremos mais sobre disco, partição e montagem com detalhe mais para frente.
 
### GRUB e Sistema UEFI/EFI

Essa é a camada um pouco superior ou seja, mais para fora do Sistema Linux, coloquei desse jeito para facilitar a explicação, mas na real cada camada é apenas mais libs e novos componentes para encorpar mais o sistema. E se observamos no slide, essa parte está mais "acima" dos outros e  

o GDM, Wayland e Gnome que estão ainda mais acima, seria a camada "mais alta" deles, que representa o ambiente gráfico, como a área e trabalho que é uma interface GUI que forra a visão do usuário para as outras camadas mais "abaixo" do sistema, faremos a instalação deles no final do post, por isso vamos ignora-los por enquanto.

Ambos esses processos ocorrem na primeira etapa do sistema, na inicialização. O UEFI é o substituto da BIOS ou seja, nela estamos inicializando os Drivers do Computador, o Secure Boot e o suporte a disco tanto o mais recente GPT quanto o mais antigo MBR, que irei detalhar eles mais tarde. 

Um [GRUB](https://wiki.archlinux.org/title/GRUB_(Portugu%C3%AAs)) é um Gerenciado de [Boot](https://linux.cosmosonline.com.br/glossario/o-que-e-boot-inicializacao-linux/) que carrega a imagem da kernel o [vmlinux](https://en.wikipedia.org/wiki/Vmlinux) e inicializa o [Systemd](https://en.wikipedia.org/wiki/Systemd), que é um sistema de inicialização que carrega todos os [daemons](https://en.wikipedia.org/wiki/Daemon_(computing)) presentes. É a partir dele que os processos iniciais do Boot serão carregados. 

Existe um suporte a um gerenciador de boot no UEFI que seria o [rEFInd](https://en.wikipedia.org/wiki/REFInd), porém o GRUB é a escolha popular padrão está presente em toda distro Linux. Alguns processos do boot será gravado no arquivo ``.efi`` no `/boot/EFI`.
 
### CHROOT

É um comando [Unix-like](https://en.wikipedia.org/wiki/Unix-like) que significa Change Root. Esse comando vai mudar o root do processo atual e seus filhos. "Perai, filhos? como assim?", isso mesmo, o "/" Root é o diretório Pai ou Raiz do nosso sistema, e os seus filhos são os Sub diretórios do pai, fica mais fácil compreender observando como uma árvore mesmo, Raiz e folhas.

![](https://blog.desdelinux.net/wp-content/uploads/2012/01/arbol-directorios1.png)

![](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEhA1yVkOMy1z4Qvi-NAb-j1JCmsnUo8xy7zx6_Dkb_Qix7nSHIKCwg3rjwn8PhaO6f7dwktwtY6LJZVRAljLScbXSZv2VU8gM2k3VOicvBS6w-7GARPeJ0DN5Opoozbe8IBjGx7UqT38Tk/s640/hierarquia_linux.png)

Com essas imagens fica mais fácil saber o porquê e onde modificar ou criar um arquivo de configuração para os diretórios padrões do Arch. A nível de curiosidade, esse padrão de árvores é uma [estrutura de dados](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*DAoQrt1ja_JMDQUxN3sboA.png) chamados de [Trees](https://pt.wikipedia.org/wiki/%C3%81rvore_(estrutura_de_dados)) e está presente em variados lugares, como em [Linguagens de programação Orientadas a Objetos](https://miro.medium.com/v2/resize:fit:640/format:webp/0*2zyGAstAusuPwlAM.gif), em todo o tipo de sistema de arquivos, como nos de Windows e no [DOM](https://miro.medium.com/v2/resize:fit:1400/1*mMmuOhNytgqP7lrU9HPTpw.jpeg) de HTML.

Geralmente quem veio do Windows enxerga o Sistema Operacional como algo Fixo, que é imutável, porém essa visão é equivocada, o root do sistema ou seja o diretório raiz de um OS é apenas uma pasta com muitos arquivos espalhados de forma recursiva.

O CHROOT vai mudar o "ponto de observação" do sistema para que o diretório filho alvo do comando passe a ser o novo root. Esse comando é fundamental para a instalação porque é nela que vamos transitar entre o ambiente live e a partição real do Sistema Operacional que está em `/dev/sda/`. Entraremos com mais detalhes mais tarde no passo a passo dos comandos ``mnt``, e para criar as novas partições do disco.

# Começando a instalação

Agora começamos oficialmente a instalação de verdade do Arch, depois de muito teoria finalmente vamos colocar tudo em prática. 

Primeiro vamos particionar nosso disco dentro do ambiente live.

## Partição de Disco

Não vou entrar muito em detalhes sobre [Dispositivos de Blocos](https://www.cs.yale.edu/homes/aspnes/pinewiki/BlockDevices.html), pois é um assunto complexo, com uma dificuldade insalubre, que dá um post 10x maior que esse. Porém pense que para um computador, dados são manipulados em Blocos de Bytes e Bits e são persistentes e de tamanho fixo (512B ou 4K). Por exemplo um HD Sata é um dispositivo de bloco.

![](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3d/WD5000AAKX_16MB_Buffer.jpg/960px-WD5000AAKX_16MB_Buffer.jpg)

![](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRFXiJMaJ6b-8hLsMUJC_CCX1Im4_o_jpJhiA&s)

Isso é o básico para se saber o que é uma [Unidade de Disco Rígido](https://pt.wikipedia.org/wiki/Unidade_de_disco_r%C3%ADgido). No começo do I/O(Input e Output) esses blocos são mantidos temporariamente na RAM para a otimização das operações do sistema operacional, esse estado temporário é chamado de Buffer.

Quando ocorre o [Shutdown](https://en.wikipedia.org/wiki/Shutdown_(computing)) durante uma atualização por exemplo, esses dados em RAM se perdem antes do flush(gravação) para o disco, deixando o sistema de arquivos inconsistente. Isso é chamado de corrupção de dados.

Não vou me alongar muito sobre nomes de dispositivos de armazenamento, porém aqui no meu sistema é `/dev/sda` que é o dispositivo ``a``, e o primeiro dispositivo descoberto.

`/dev/sda1` seria a partição `1` no dispositivo ``a``.

Como estou em uma máquina virtual, meu dispositivo de armazenamento vai ser um HD SATA, mas na prática a maioria dos computadores modernos, provavelmente vão estar equipados com um SSD, pois oferece ganho de desempenho e [durabilidade mecânica](https://recoverydata.com.br/blog/quanto-tempo-dura-um-hd-e-sua-vida-util/#:~:text=Em%20geral%2C%20a%20maioria%20dos,que%20isso%20com%20cuidados%20adequados.) pois um HD externo, por exemplo precisa de um imã e um disco para ler dados, fazendo ele ser muito sensível.  

Então apenas o nome muda, sendo [NVMe](https://wiki.archlinux.org/title/Device_file_(Portugu%C3%AAs)#NVMe), Como não vou fazer uma instalação usando o SSD, vou apenas deixar claro que provavelmente apenas o nome vai mudar junto com a ordem de reconhecimento.

Para listar o seus dispositivo:

```
fdisk -l
```

Se o disco SATA ou NVMe não aparecer consulte: [Este Guia](https://wiki.archlinux.org/title/Partitioning_(Portugu%C3%AAs)#Unidades_n%C3%A3o_ficam_vis%C3%ADveis_quando_o_RAID_do_firmware_est%C3%A1_habilitado)

Com isso vamos particionar o disco e criar um volume nessa partição. O que é volume? volume é quando a partição sai do meio físico de ser apenas um espaço do HD e passa a ter um único sistema de arquivo, contendo a interface lógica do sistema operacional, por isso volume pode ser chamado também de unidade lógica.

Então vamos particionar o nosso disco, e formatar para ser um volume. Para isso vamos usar o comando ``fdisk``. 

```
fdisk _/dev/o_disco_a_ser_particionado_
```

Deixando claro que apenas farei a partição do sistema ``EFI``, uma de ``SWAP`` e outra do diretório raiz `/`, que é apenas o necessário.

Para saber mais sobre o [fdisk](https://guialinux.uniriotec.br/fdisk/#:~:text=Algumas%20op%C3%A7%C3%B5es%20do%20comando&text=S%C3%A3o%20valores%20v%C3%A1lidos%3A%20512%2C%201024,nas%20vers%C3%B5es%20antigas%20do%20kernel.) ou 

```
pacman -S man 
man fdisk
```

``fdisk`` é um comando interativo, ou seja, o comando pelo terminal vai te dando opções e o usuário seleciona. Para facilitar a partição e formatação, vou colocar aqui o guia das opções para formatar essas três partições com esses layouts, mas deixando claro que qualquer erro é sua responsabilidade, leia atentamente:

```
EFI = 512M
SWAP = (Opcional mas no mínimo 3G)
"/" Root = o espaço que sobrou (Recomendado 60G)
```

#### ATENÇÃO: NÃO CRIE UMA PARTIÇÃO EFI SE ESTIVER FAZENDO DUAL BOOT

```
fdisk /dev/sda

Welcome to fdisk (util-linux 2.x).
Changes will remain in memory only, until you decide to write them.
Be careful before using the write command.

# Dentro do fdisk:
g                # Nova tabela GPT
n                # Nova partição (EFI)
Enter            # Número 1
Enter            # First sector default
+512M            # Tamanho EFI
t                # Mudar tipo
1                # Ou uefi/EF

n                # Nova partição SWAP
Enter            # Número 2
Enter            # First sector default
+3G              # Tamanho do SWAP
t                # Mudar tipo
2                # Numero da Partição
19               # Ou swap

n                # Nova partição (root)
Enter            # Número 3
Enter            # First sector default
Enter            # Last sector default → pega o resto (~60 GB)

p                # Verifica
w                # Salva e sai
```

Agora concluindo temos:

```
/dev/sda  # O dispositivo
/dev/sda1 # Partição de UEFI/EFI
/dev/sda2 # Partição do SWAP
/dev/sda3 # "/" partição ROOT
```

## Formatando as Partições do Novo Sistema

Vamos agora formatá-las para criar volumes, como já expliquei antes.

Formatar partição Raiz que será formatada para o sistema de arquivo simples ext4.:

```
mkfs.ext4 /dev/sda3 
```

Monte a partição de SWAP com:

```
mkswap /dev/sda2
```

Por último vamos formatar a partição de sistema EFI com o formato padrão FAT32

#### ATENÇÃO: APENAS FORMATE O SEU EFI SE O CRIOU ANTES, NÃO FORMATE A PARTIÇÃO EFI SE ESTIVER FAZENDO DUAL BOOT

```
mkfs.fat -F 32 /dev/sda1
```

## Montando as Partições no Novo Sistema

`/mnt` será o ``"/"`` root do nosso novo sistema, vamos montá-lo:

```
mount /dev/sda3 /mnt
```

Agora vamos criar o resto do nosso sistema usando ``/mnt`` como nosso novo sistema operacional. ``--mkdir`` para especificar.

```
mount --mkdir /dev/sda1 /mnt/boot
```

Habilite o SWAP:

```
swapon /dev/sda2
```

Com isso vamos ter criado o diretório ``/mnt`` dentro do ambiente live, onde vamos ter montado cada partição nele, como disse antes, quando montamos estamos criando volumes para por diretórios e arquivos, então dentro de ``/mnt`` vai ter ``/mnt/boot/``.

Temos nesse momento um sistema Linux dentro do outro. Quando instalamos de fora os pacotes e o kernel para dentro desse "novo sistema" que está dentro de ``/mnt``, ele já será um sistema operacional usável.

Os diretórios padrões como ``/tmp``, ``/dev``, ``/bin``, ``/home``, ``/etc`` serão incluídos de forma automática com o [initramfs](https://wiki.archlinux.org/title/Arch_boot_process_(Portugu%C3%AAs)#initramfs) porque vamos instalar o kernel com o [pacstrap](https://man.archlinux.org/man/pacstrap.8).  Assim quando removermos a mídia de instalação(o pendrive bootável), sairemos do ambiente live/liveCD e o sistema estará pronto, tendo ``/mnt`` como uma nova raiz `/`.

## Pré-CHROOT: Instalando o Kernel e mais pacotes "de Fora para Dentro"

Agora vamos instalar os pacotes essenciais para podermos fazer CHROOT para nosso novo sistema. Colocaremos o pacote base, kernel e firmware para termos todos os recursos do ambiente live. Adicionarei também o pacote ``sudo`` e ``vim`` manualmente e o pacote ``amd-ucode`` para correção de segurança, se estiver com o processador INTEL ao invés do AMD, instale ``intel-ucode``. 

Já que sairemos do ambiente live, também teremos que instalar o pacote daemon `NetworkManager` para quando chegarmos dentro do nosso sistema novo estivermos conexão com WI-Fi.

Para usuários como eu que instalaram pelo VirtualBox, recomendo o pacote `virtualbox-guest-utils` para evitar bugs com drivers, como os de display, teclado e mouse.

```
pacstrap -K /mnt base linux linux-firmware vim sudo amd-ucode networkmanager virtualbox-guest-utils
```

## Configurando o Sistema

Agora estamos preparados para definir com o `chroot` o  diretório filho `/mnt` como raiz. Antes vamos gerar um arquivo `fstab` para salvar o ponto de montagem e incluir no Systemd durante a inicialização para automatizar os comando de montagem.

```
genfstab -U /mnt >> /mnt/etc/fstab
```

Para confirmar abra o arquivo `/mnt/etc/fstab` e edite-o caso haja erros.

Agora mude a raiz para o novo sistema:

```
arch-chroot /mnt
```

Agora estamos Oficialmente e finalmente dentro do nosso Arch Linux.

### Defina Horário

```
ln -sf /usr/share/zoneinfo/America/Sao_Paulo /etc/localtime
```

### Execute ``hwclock`` para definir horário UTC

```
hwclock --systohc
```

Para mais informações em [Horário](https://wiki.archlinux.org/title/Installation_guide_(Portugu%C3%AAs)#Hor%C3%A1rio) no guia do ArchWiki.

### Localização

Faça o mesmo passo a passo para localização no tópico de Pré-instalação desse post.

E crie o arquivo `/etc/vconsole.conf` para manter a persistência do layout do teclado, adicione nesse arquivo:

```
KEYMAP=br-abnt2
```

### Configure a Rede

Crie o arquivo de hostname em `/etc/hostname`, adicione:

```
seuhostname
```

Agora ative o NetworkManager para termos WI-Fi disponível no novo sistema, com o comando `systemctl` ativando o daemon.

```
systemctl enable NetworkManager
```

### Defina a Senha do Usuário Root

Adicione uma senha forte mas não o suficiente para você esquecer com facilidade, pois precisamos dela para entrar no sistema recém-instalado. 

```
passwd
```

### Instalando o GRUB

Agora vamos instalar o famoso GRUB. Dentro do chroot instale os pacotes `grub` e `efibootmgr`.

```
pacman -S grub efibootmgr
```

Agora para instalar o aplicativo EFi do GRUB em `/mnt/boot/EFI/GRUB` e seus módulos para `/boot/grub/x86_64-efi/` execute o comando:

```
grub-install --target=x86_64-efi --efi-directory=/mnt/boot --bootloader-id=GRUB
```

Se por algum motivo for necessário executar esse comando no ambiente live, fora do sistema instalado, execute isso: 

```
grub-install --target=x86_64-efi --efi-directory=/mnt/boot/ --bootloader-id=GRUB --boot-directory=/mnt/boot
```

A opção `--boot-directory=` deve conter o caminho para o `/boot`

Após a instalação do GRUB o seu diretório principal estará em `/boot/grub/`.

O último passo é gerar o arquivo de configuração principal:

```
grub-mkconfig -o /boot/grub/grub.cfg
```

Caso esteja fazendo dual boot: [leia isso](https://wiki.archlinux.org/title/GRUB_(Portugu%C3%AAs)#Detectando_outros_sistemas_operacionais)

Instalação do GRUB no sistema BIOS: [leia isso](https://wiki.archlinux.org/title/GRUB_(Portugu%C3%AAs)#Sistemas_BIOS)

## Reiniciando: saindo do Ambiente Live

Saia do ambiente `chroot` digitando `exit`. Desmonte todas as partições com o comando:

```
umount -R /mnt
``` 

E finalmente reinicie a máquina digitando: 

```
reboot
```

Remova a mídia de instalação. 

E autentique-se com o seu usuário root e a senha que você definiu.

Não é recomendado por questões de [Segurança](https://wiki.archlinux.org/title/Security) permanecer no usuário root, por isso vamos criar um usuário `sudo` que vai usar os privilégios do root, porém com verificação por senha.

```
# 1. Crie o usuário (troque "seunome" pelo nome que quiser) 
useradd -m -G wheel seunome

# 2. Defina uma senha forte para o usuário 
passwd seunome
```

Agora usaremos o comando `visudo` para liberar o ``sudo`` para o [grupo ](https://wiki.archlinux.org/title/Users_and_groups_(Portugu%C3%AAs)) `wheel`.

```
visudo
```

Quando abrir o editor pelo vim, procure essa linha, se não tiver crie:

```
#%wheel ALL=(ALL:ALL) ALL
```

Remova o "#" (se tiver) para descomentar, salve e saia do vim com `:wq!`. 

É recomendado também adicionar o usuário novo em alguns grupos úteis, com esse comando:

```
usermod -aG video,audio,storage,network,lp seunome
```

Com isso, todo comando que for preciso executar com privilégios root é só colocar `sudo` no começo do comando. Vamos testar?

Vamos agora atualizar os pacotes já instalados com:

```
sudo pacman -Syu
```

Dê uma olhada na seção [Pós-instalação da wiki](https://wiki.archlinux.org/title/Installation_guide_(Portugu%C3%AAs)#P%C3%B3s-instala%C3%A7%C3%A3o) para mais detalhes sobre segurança e instalações de pacotes e programas para complementar o sistema.

# Ambiente Gráfico: Gnome + Wayland

Finalmente, esse post foi bem longo, mas ainda não chegamos no final ainda, vamos instalar agora um ambiente gráfico para fechar com chave de ouro. 

Ambiente gráfico é outro assunto que renderia um post inteiro mas não aguento mais digitar... Então falarei apenas do básico.

Como interface gráfica usaremos o [Gnome Shell](https://pt.wikipedia.org/wiki/GNOME_Shell), que vai ser o conjunto área de trabalho, painel de controle e barra de notificação. Existem outros como KDE Plasma e XFCE.

E como servidor de display, que será o [Wayland](https://pt.wikipedia.org/wiki/Wayland_(protocolo_de_servidor_gr%C3%A1fico)), uma alternativa seria o i3 como WM ou Xorg. Ele carregará os drivers de exibição que estarão no meu pacote `virtualbox-guest-utils` e configurará variáveis de ambientes como o $DISPLAY que serve para indexar a quantidade de monitor e configurar desktops remotos via endereço IP. Além disso ele vai compor o Gnome Shell para nós. 

Vamos primeiro instalar o pacote ``gnome`` que contém o ambiente e um subconjunto de aplicativos integrados.

```
sudo pacman -S gnome gdm
```

O GDM é o gerenciador de exibição do Gnome e um programa que gerencia servidores gráficos, além de lidar com login que vai iniciar de forma automática o Gnome Shell. 

Depois da instalação vamos ativar o GDM com systemctl usando:

```
sudo systemctl enable gdm
```

Para confirmar se foi ativado:

```
sudo systemctl status gdm
```

Agora finalizando apenas execute `sudo reboot`. O GDM é identificado, carregando a interface de login. 

Com isso entramos no ambiente do Gnome. 

![](https://i.ibb.co/ccPjKpd8/Captura-de-tela-2026-03-05-011156.png)

# Finalizando

Fizemos a instalação completa do Arch Linux, do kernel e as partições até o ambiente gráfico. Existem muitas coisas para fazer dentro do sistema já pronto, como a personalização para deixar as coisas ainda mais bonitas, colocar ``themes`` e ``icons`` no Gnome e o pacote de configuração do [Power Level 10k](https://hashir.blog/assets/final-starship-catppuccin.zPCjMxUN_2c1PrT.webp) no emulador de terminal. 

Além de um ecossistema de trabalho para programador com ferramenta como Git, ``asdf``, Docker, LazyVim, Banco de dados e ZSH, tudo integrado via terminal, mas isso é assunto para outro post.

---------------------------------------------------------------------------------------