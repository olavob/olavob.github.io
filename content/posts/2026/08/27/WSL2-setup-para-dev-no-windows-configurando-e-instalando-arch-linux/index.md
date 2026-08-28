---
date: 2026-08-27T02:53:01-03:00
draft: false
title: "WSL2: Setup para Dev no Windows, Configurando e Instalando Arch Linux"
comments: true
---

## Introdução

Muitas pessoas escolhem ficar no Windows pela conveniência e familiaridade, já que todos os usuários o utilizam, gerando compatibilidade, para que assim, as empresas projetarem softwares e games apenas para Windows e alcançar o máximo de pessoas. A consequência disso é que o Windows é o padrão e o mais difundido, mesmo tendo alternativas Open Source superiores. 

>Para o usuário normal o Sistema Operacional Windows é o próprio computador...

Porém para desenvolvedores, a família de sistemas operacionais que utilizam o núcleo Linux, não é apenas um sistema operacional desconhecido e secundário, mas uma ferramenta essencial que todo profissional deve ter no seu arsenal. 

Entretanto, todo esse aconchego, dificultou para que os desenvolvedores abandonassem de vez o Windows, mesmo o Linux possuindo um ambiente perfeito para desenvolvimento. 

>Então, como superar essa discriminação? 

O WSL (Windows Subsystem for Linux ou, em português, Subsistema do Windows para Linux) é a resolução desse dilema, o caminho pra quem quer virtualizar somente o essencial do Linux e ainda assim manter a versatilidade do Windows.

Nesse post irei abordar a instalação do WSL 2 usando Arch Linux, e configurar um ambiente para desenvolvedor mais versátil e organizado para Windows 10 ou superior.

#### Nota
>Antes de explorar o WSL, eu recomendo primeiro passar pelo processo de instalação e primeiras impressões de qualquer distribuição Linux nativo ou emulado por um tempo pra se familiarizar e praticar o POSIX, que são todos os comandos que um terminal suporta, pois não iremos ter ambiente gráfico e faremos tudo pelo terminal

## Porque Arch Linux?

O Arch Linux ou outras distros baseado nele como Manjaro e EndevourOS, contém um gerenciador de pacotes distribuído pela comunidade que se chama AUR, e outro mais restrito e seguro que se chama Pacman, com esses dois gerenciadores o Arch Linux possui um grande número de Softwares a mais que seus pares, como os baseados em Debian e Redhat 

Por exemplo, o sistema Ubuntu baseado em Debian, conhecido por ser mais amigável para iniciante, utiliza como gerenciador de pacotes o APT, propriedade da Canonical e mais restrito por não ser livre, tendo um número limitado de alternativas de software. 

Uma das outras vantagens do Arch é a leveza, nada é instalado por padrão, tendo mais economia. E controle maior no seu próprio sistema, por te forçar a fazer tudo "na mão", nada é configurado automaticamente.
#### Nota
>A imagem oficial do [Arch Linux](https://gitlab.archlinux.org/archlinux/archlinux-wsl) foi oficialmente lançada para WSL2 em abril de 2025. Ela é mantida e atualizada mensalmente pela equipe do Arch Linux
 
>Antes de termos a imagem oficial, era usado a imagem não oficial chamado [ArchWSL de yuk7](https://github.com/yuk7/archWSL) **mas essa opção agora é mais instável e não recomendado**  

## Instalando o WSL 2 e Configurações Iniciais
### Dependências

Antes de começarmos a Instalar o WSL2, iremos fazer algumas etapas no Windows primeiro, ativando alguns recursos que são suportados e mantidos oficialmente pela Microsoft e que integra o Windows no WSL.

#### Verificando o Recursos

No seu Windows 10 ou 11:

pressione as teclas ```Windows + R```

Na pequena janela que aparecer, digite: `optionalfeatures`

Clique em Ok.

A lista de recursos será exibida e marque a opção: `Plataforma de Máquina Virtual`

Clique em Ok para confirmar.

e reinicie o PC.

#### Nota
>Nesta nova versão da Store do WSL2, não iremos habilitar a opção de recurso: `Subsistema do Windows para Linux`, ~~pois ela não é mais necessária.~~(para usuários que possuem build do Windows 10 muito antigas ou exóticas, vale ler a [documentação oficial](https://learn.microsoft.com/pt-br/windows/wsl/install-manual) para a instalação, aconselho que se deite em posição fetal e chore um pouco e boa sorte)

#### Instalando o Emulador de Terminal

O Emulador de Terminal é uma interface que emula o ambiente de terminal do kernel do sistema.

Depois de anos de espera, finalmente temos um emulador de terminal oficial decente para o Windows, no mesmo nível de opções boas e customizáveis para Linux como o Alacritty e o iterm2 para MacOS.

Acesse a Microsoft Store e instale o [Windows Terminal](https://apps.microsoft.com/detail/9N0DX20HK701?hl=pt-br&gl=BR&ocid=pdpshare), se já tiver instalado, ótimo, essa é a nossa interface de acesso para o WSL.

### Instalando o WSL2 e Verificando Atualizações

Para Instalar tudo que precisa para executar o WSL, abra o PowerShell no modo *`administrador`* clicando com o botão direito do mouse e selecionando "Executar como administrador".

Agora que estamos no PowerShell com permissões elevadas, vamos verificar a versão estável mas recente do WSL executando:

```powershell
wsl --update
```

Para verificar e exibir a lista de todos as distribuições Linux disponíveis, execute:

```powershell
wsl.exe --list --online
```

E finalmente vamos instalar o WSL2 com:

```powershell
wsl --install archlinux
```

Para finalizar, após a instalação, reinicie o PC.

>Se tiver algum problema com a instalação, vide [seção de instalação do guia de solução de problemas](https://learn.microsoft.com/pt-br/windows/wsl/troubleshooting#installation-issues)

### Configurações do Sistema

Para acessar o Arch linux, abra o Windows Terminal, e no PowerShell:

```powershell
wsl -d archlinux
```

Iniciamos pelo Usuário `Root` como qualquer Arch recém instalado, para ir na raiz do sistema que acabamos de instalar, apenas execute o comando `cd` no terminal, assim sairemos do diretório ``System32`` e iremos para o diretório `/home`.

Faremos os seguintes comandos para criar usuário: 

```
[root@PC-NAME]# mkdir /etc/sudoers.d/wheel
(criar o diretório do grupo de usuários wheel.)

[root@PC-NAME]# echo "%wheel ALL=(ALL) ALL" > /etc/sudoers.d/wheel
(setar "all User" no grupo wheel.)

[root@PC-NAME]# useradd -m -G wheel -s /bin/bash {SEU_username}
(adicionar usuário, substitua "{SEU_username}" pelo SEU username.)

[root@PC-NAME]# passwd {SEU_username}
(setar uma senha para o usuário que você criou, use uma senha forte.)
```

```
[root@PC-NAME]# passwd
(setar uma senha para o usuário root, use uma senha forte.)
```

>Se você estiver "bloqueado" execute no PowerShell elevado: `wsl -u root

Com essa serie de comando, adicionamos uma conta com senha no nosso Arch e uma senha forte para o usuário ``root``. 

Antes de mudarmos para a nosso usuário recém criado, vamos atualizar o sistema:

```
[root@PC-NAME]# pacman -Syyuu
(atualizar os Pacotes do sistema.)
```

E instalar dois comandos, o ``sudo`` para a senha setada ser utilizada para nosso usuário usar comandos com privilégios altos e o ``nvim`` para termos um editor de arquivo funcional.

```
[root@PC-NAME]# pacman -S sudo nvim
(instalar o sudo e nvim.)
```

Antes de fecharmos o terminal, definiremos o usuário como padrão diferente do ``root``,  nessa etapa da situação acho que não preciso explicar porque criamos um usuário inferior e não utilizamos o root direto.

editaremos o arquivo `/etc/wsl.conf`:

```bash
nvim /etc/wsl.conf

# (No nvim pressione "a" para escrever)

[user]
default={SEU_username}
```

para salvar e sair `:wq` no nvim.

Para finalizar a sessão, no PowerShell elevado:

```bash
wsl --terminate archlinux
```

Assim, quando abrirmos o Arch, o usuário que você criou vai estar logado como padrão e para testar o sudo, abra o PowerShell elevado, digite novamente `wsl -d archlinux`, e execute:

```bash
sudo pacman -Syyuu
```

Um campo para a verificação da senha aparecerá.

## Configurando o Setup para Dev

Agora que estamos com o nosso sistema instalado e as configurações iniciais prontas, vamos começar a deixar o WSL mais bonito e útil, instalando temas para o Windows Terminal e varias ferramentas de desenvolvimento para o nosso Linux quentinho, saído direto do forno.

### No Emulador de Terminal

#### Definindo Perfil Padrão

Primeiramente trocaremos o perfil padrão dentro do menu de inicialização nas configurações, é inconveniente sempre executar o comando `wsl -d archlinux` para entrar no nosso WSL, faremos isso se tornar automático.

Pressione as teclas `ctrl + ,` no terminal para abrir as configurações, e em "inicialização" encontre "perfil padrão" e troque para `archlinux`. Assim sempre que o terminal é inicializado o Arch carregará automaticamente.

![800](https://i.ibb.co/C3XPtPh5/perfil-padr-o.png)

#### Alterando Tema do Terminal

Vamos agora alterar o tema do nosso terminal, o tema padrão é terrível de feio, e eu apenas consigo trabalhar em ambientes bonitos. 

Dentro do menu de configurações, localize a opção `Abrir o arquivo JSON` e clique, abra o arquivo no bloco de notas.

No navegador, abra o site [windowsterminalthemes.dev](https://windowsterminalthemes.dev/) e escolha o tema de sua preferência. Recomendo o tema "coolnight" ou qualquer outro tema escuro com fontes marcantes. 

Assim que clicar em `Get theme` para copiar o tema para sua área de Transferência, abra o bloco de notas e **cole** no final do arquivo, **respeitando a virgula.**

```
[...]

            "cursorColor": "#38FF9D",
            "cyan": "#FF5ED4",
            "foreground": "#ECDEF4",
            "green": "#52FFD0",
            "name": "coolnight",
            "purple": "#C792EA",
            "red": "#FF3A3A",
            "selectionBackground": "#38FF9C",
            "white": "#16FDA2",
            "yellow": "#FFF383"

        },      ---->       Coloque uma Virgula
    
    <<COLE AQUI>>
    
    ],     ---->      Mantenha dentro do Colchete

[...]
```

Depois de colar o tema, dentro do **Bloco de notas** vá em `Arquivos` no canto superior esquerdo e clica em "Salvar", e feche o bloco de notas.

Agora dentro das configurações do terminal, localize  `esquema de cores`, e clique no tema que foi salvo, vá em ``definir como padrão`` e salve.

![](https://i.ibb.co/tPxfrCZY/terminal-meslolgsnf.png)

Agora quando reiniciarmos o terminal, o Linux irá ser iniciado e o tema será aplicado.

### No Arch Linux

Agora que deixamos nosso terminal bonito. Vamos montar o setup de fato, instalando ferramentas para desenvolvimento e componentes visuais para deixar o terminal mais moderno, útil e confortável.

#### Instalando Yay

Para começar, iremos instalar o `yay` que é o gerenciador do AUR, e por ele vamos acessar o gerenciador de pacotes e instalar os softwares que são disponibilizados pela comunidade. 

Mas antes, vamos instalar algumas dependências como `git` e o conjunto de ferramentas de C e compilação que se chama `base-devel` para podermos utilizar na compilação.

```bash
sudo pacman -S --needed git base-devel
```

Note que usamos a flag `-S` para sempre fazer uma instalação e o comando `sudo` para confirmar o privilégio alto.

Seguindo a instalação, vamos pro diretório `/tmp` onde fica os arquivos temporários, nele vamos clonar o repositório do Yay, com se fosse uma cópia do código fonte.

```bash
cd /tmp
```

```bash
git clone https://aur.archlinux.org/yay.git && cd yay
```

Nos mudamos para o diretório temporário para não gastar espaço e também não poluir o sistema já que, depois que fazermos a compilação do código fonte, ele não será mais necessário.

Estamos dentro do diretório do projeto Yay, em `/tmp/yay/`. 

Na raiz mesmo do projeto, vamos compilar o projeto descrito no `PKGBUILD`.

```bash
pwd
# (Confirme localização)

makepkg -si
# (Compile o projeto com MAKE)
```

Usamos `makepkg -si`para instalar as dependências do projeto e transforma-lo em binário pra podermos executar em qualquer lugar do sistema.

Com isso, temos o `yay`instalado em `/usr/bin/yay`, onde fica outros binários como o comando `pacman`, `sudo` entre outros.

>Dê `cd` para voltar pro seu `/home`. Os arquivos presentes no diretório temporário vão desaparecer depois da próxima reinicialização

#### Instalando ZSH

O ZSH ou Z SHELL é um Shell moderno e também um linguagem de script, honestamente, a escolha de qual Shell entre outros como o Korn Shell e C Shell é pessoal, porém tenha em mente de que cada um deles tem suas próprias limitações. São ferramentas antigas, e algumas já não são mais recomendadas.

O Shell que vem como padrão é o Bash, que se originou do Bourne Shell como uma alternativa aprimorada, como eu disse, não tem nenhum problema você ficar nele, entretanto, recomendo a utilização do ZSH como uma forma de compatibilidade pra esse post, já que usar outro Shell pode resultar em erros inesperados e não terá a mesma modificação visual com PowerLevel10k que veremos logo a seguir.

>Para confirmar seu Shell utiliza-se o comando `echo $SHELL`

Vamos Instalar o ZSH pelo `yay`, e aproveitar e apresentar um pouco dele com forma de complemento pra o `pacman`.

```bash
yay -S zsh
```

Super simples e rápido, usamos a mesma flag `-S`, porém sem o comando `sudo` para verificação de privilégios, mas simples, rápido e fácil.

Para atualização de pacotes no `pacman` se usa a flag `-Syu` e no `yay` é simplesmente `yay` e pronto.

```bash
yay
```

![](https://i.ibb.co/JFKFfynS/yay.png)

Mesmo com o ZSH instalado se dermos `echo $SHELL` ainda aparecerá que estamos usando o Bash, isso porque ainda não trocamos de fato de Shell.

Para trocarmos de Shell fazermos:

```bash
chsh -s /usr/bin/zsh
```

O `chsh` vem de Change Shell, e depois de confirmar a senha, a variável de ambiente $SHELL ainda não vai apontar para o binário certo, para ocorrer a modificação, temos que recarregar o arquivo de configuração do terminal, o arquivo `.zshrc` com o comando `source`.

```bash
source .zshrc
```

>Agora confirme com `echo $SHELL` e verá que alteramos o Shell com sucesso

#### Power Level 10k e Nerd Fonts

##### Instalando Power Level 10k

![800](https://i.ibb.co/gZ1LT49T/prompt-styles-high-contrast.png)

Essa parte é completamente opcional, porém recomendo bastante instalar o tema Powerlv10k para ter uma melhor experiência ao usar o terminal, e acredite, é insuportável usar aquele terminal simples com cor única, não dá pra trabalhar assim, eu mesmo quando comecei a usar temas nunca mais voltei atrás.

A instalação dele é super simples, vamos usar `yay` pra baixar o código fonte direto do Git: 

```bash
yay -S --noconfirm zsh-theme-powerlevel10k-git
```

e depois adiciona-lo no arquivo `.zshrc` com o símbolo ''>>'':

```bash
echo 'source /usr/share/zsh-theme-powerlevel10k/powerlevel10k.zsh-theme' >>~/.zshrc
```

##### Instalando Nerd Fonts

Antes de recarregar o arquivo `.zshrc` novamente, vamos baixar o conjunto de fontes e ícones do MesloLGS.

Para explicar melhor esse conjunto de fontes, precisamos ver primeiro a tabela Unicode de Emoji.

![433](https://i.ibb.co/vCt4XzkK/printing-emoji-characters-unicode-codepoint-lucee5.png)

Cada caractere Unicode corresponde a um emoji, ou seja, quando utilizamos um emoji, ele não é um PNG salvo no seu celular, mas sim um ícone representado por códigos, é só, por exemplo digitar: `U+1F60E`, para o dispositivo que tem as fontes instalado, aparecerá o emoji. 

Para o servidor ou pagina web, são apenas caracteres, zero custo.

A mesma coisa representa para ícones no Nerd Fonts:

![336](https://i.ibb.co/svNNdQtB/nerd-fonts-icons-in-terminal.png)

>Porque usar caracteres únicos para catalogar ícones?

A resposta é simples, Nerd Fontes é muito usado em páginas web por variados locais diferentes, imagina um arquivo PNG de **kilobyte** para cada um deles? Com certeza isso custaria **gigabytes** e até mesmo **terabytes** se dezenas de ícones em milhões de páginas abertas pra cada usuário fossem exibidas, não teria escalabilidade vertical para tanto consumo.

Então para resolver esse problema, a tabela Unicode para ícones foi criado.

A instalação das fontes é feito no **Windows**, já que vai ser o **Windows Terminal** que exibirá ele.

Acesse esse [LINK](https://github.com/romkatv/powerlevel10k#manual-font-installation) e instale cada uma das 4 fontes listadas no Github.

![538](https://i.ibb.co/BKrCW5jt/Captura-de-tela-2026-08-26-215526.png)

Vá para a pasta de Downloads, **Selecione Tudo** e clique em **Instalar**.

Agora vamos voltar para as configurações do terminal em `ctrl + ,`, no menu esquerdo, vá até "Perfis", selecione "archlinux".

Na configuração do perfil, scrolla pra baixo e achará "Aparência" em "Configurações Adicionais".

Uma vez lá dentro, na categoria "Texto", tire "Consolas" e selecione "MesloLGS NF".

![800](https://i.ibb.co/tPxfrCZY/terminal-meslolgsnf.png)

Concluirmos a instalação das fontes, mas para ser aplicado no terminal, vamos recarregar o arquivo de configuração do Shell para realizar o wizard de configuração do P10k.

```bash
source .zshrc
```

O wizard de configuração vai ser iniciado, e não tem segredo, vai ser apenas uma interface onde você vai escolhendo como seu tema vai ficar, fica a critério do seu gosto.

Observe o exemplo a seguir:

![511](https://raw.githubusercontent.com/romkatv/powerlevel10k-media/master/configuration-wizard.gif)

Como você vai perceber, no inicio do wizard tem um teste pra se certificar que o usuário possui o Nerd Fonts Instalado. Como perguntar se vimos um símbolo de diamante.

Como fizemos os todos os passos, concluirmos todas as etapas, e seu tema foi configurado com sucesso e agora verá esse ícone.

#### Alternativas Visuais em Rust

Atualmente, alguns comandos de linha de comando, como o `ls` e `cat` possuem alternativas modernas e mais rápidas escritas em Rust, que é uma uma linguagem de Programação com velocidade equivalente e moderna a C puro.

Observe as mudanças visuais no comando `ls`, que lista todos os arquivos e diretórios que estão presentes no sistema:

![647](https://i.ibb.co/JRNPKYTS/exa-ls.png)

Veja que o seu substituto, o `exa` utiliza esquema de cores e também ícones NF.

outro comando modificado foi o comando c que exibi o conteúdo de um arquivo diretamente no terminal, sem a necessidade de abri-lo:

![746](https://i.ibb.co/dJmrXjkc/bat-cat.png)

Dá pra observar claramente que o texto foi estilizado pelo substituto `bat`, e está mais coerente, com formatações que simulam um editor de arquivo mais moderno.

Consegui te convencer a instala-los? então vamos lá.

```bash
yay -S exa bat
```

Simples, graças ao `yay` é somente colocar cada um dos comandos e instala-los.

E agora é só testar

```bash
exa -ls --icons
```

Eu particularmente não me adaptei em usar `exa` ao invés de `ls`, por costume mesmo, já que esses comando é sempre usado, por isso, eu utilizo "aliases" no arquivo `.zshrc` que vai trocar automaticamente o comando pelo outro.

>Ou seja, quando eu digitar `ls`, ele vai ser um pseudônimo para `exa`

**E estou deixando claro que essa configuração inutiliza o `ls` padrão do sistema.**

Editaremos o arquivo `.zshrc` utilizando o comando `nvim .zshrc` e adicione o seguinte código na ultima linha:

```bash
alias ls="exa --icons"
alias cat="bat --style=auto"
```

Depois salve o arquivo com  `:wq` no nvim e recarregue o arquivo com `source .zshrc` e teste.

#### Mise en Place

Mise en Place é definitivamente a ferramenta mais importante pra ser instalado em qualquer distribuição Linux, ele vai gerenciar todas as linguagens de programação que você estiver instalado e vai especificar cada umas das versões especificas delas pra cada projeto.

Essa ferramenta é um triunfo para todo o desenvolvedor.

##### Rant: Mesmo Ambiente, Linguagem Global

Muitos desenvolvedores utilizam Windows puro, instalando cada linguagem como arquivo `.EXE`  e usando ela **Globalmente** na mesma versão para toda a máquina, mas isso é **ERRADO**.

Mesmo se você for um iniciante, lidar com muitas versões é o básico que não é ensinado, e isso é um erro.

Todo o programador seja iniciante ou não, precisa saber duas coisas: aprender a pesquisar e controlar seu próprio ambiente e sistema operacional.

Até mesmo existem usuários de Linux que não utiliza essa ferramenta e simplesmente instala tudo globalmente, como:

```bash
# arch
yay -S ruby python3

# Ubuntu
apt install ruby python3
```

Todas essas opções estão erradas e não condizem com a realidade de um programador.

No mundo real, você tem projetos diferentes, linguagens diferentes, versões diferentes e até mesmo, a mesma linguagem só que num projeto, se usa a versão 3.13.0 e no outro 2.0.0 nesse cenário, você tem ambientes de desenvolvimento diferentes e uma mudança pequena pode quebrar tudo e dar prejuízo.

##### Instalando o Mise

Para instalar o Mise en Place é simples, basta usar `yay` e seu comando é `mise` , logo após vamos, como sempre modificar o `.zshrc`.

```bash
yay -S mise
```

```bash
echo 'eval "$(mise activate zsh)"' >> "${ZDOTDIR-$HOME}/.zshrc"
```

Depois recarregue o `.zshrc` com `source .zshrc` e pronto, o `mise` foi instalado com sucesso, agora vamos para um breve tutorial de como usá-lo.

##### Usando o Mise

Para desenvolvedores novatos, ter um projeto no Linux pode ser bem desafiador e diferente por ser tudo via terminal, então essa parte pode ficar confusa, porém esse é o fluxo normal de trabalho em um projeto.

```bash
cd ~/Projects/MeuProjeto
```

Geralmente os projetos ficam em pastas únicas, e cada uma delas são gerenciadas pelo `git`.

```bash
mise use ruby@3.2.3
```

 Uma vez dentro do projeto recém criado, utilizaremos o comando `use` do `mise` para especificar a linguagem e sua versão.

Quando adicionamos a versão e a linguagem em específica, o Mise en Place cria de forma automática um arquivo `.tool-versions` ou `mise.toml` e isso ficará no seu projeto para caso algum desenvolvedor de fora precisar trabalhar no seu projeto, apenas instalar as versões presentes nesses arquivos.

```bash
cat .tool-versions
ruby 3.2.3


git add .tool-versions
```

Para confirmar a instalação de alguma linguagem, usaremos a flag `-v` e se houver resposta significa que a linguagem foi instalada com sucesso.

```bash
MeuProjeto [ master][$!?⇡][ v24.7.0][💎 v3.2.3]
ruby -v
ruby 3.2.3 (2024-01-18 revision 52bb2ac0a6) [x86_64-linux]
```

Toda linguagem instalada ficará em `/$HOME/user/.local/share/mise/installs` onde fica separado do sistema global e apenas os projetos que especificam o `.tool-versions` ou `mise.toml` usam essas determinadas linguagens e suas versões.

```
MeuProjeto [ master][$!?⇡][ v24.7.0][💎 v3.2.3]
which ruby
/home/user/.local/share/mise/installs/ruby/3.2.3/bin/ruby
```

## VScode

Por ultimo e menos importante, utilizaremos o VScode do próprio sistema Windows, ele está disponível no [site oficial](https://code.visualstudio.com/) para download e na [Microsoft Store](https://apps.microsoft.com/detail/XP9KHM4BK9FZ7Q?hl=pt-BR&gl=BR&ocid=pdpshare). 

Após instala-lo, use o comando  `code` pelo WSL2:

```bash
code Meuarquivo
```

E ele iniciará automaticamente a compatibilidade Windows - WSL2.

## Finalizando

Após esse longo post, não aguento mais ficar digitando e olhando pra frente, finalizamos nossa instalação e configuração de um setup pra dev, usando Arch Linux no WSL2.

Daqui pra frente você, desenvolvedor, pode adicionar mais ferramentas, colocar DB, Git, e docker, o que precisar para montar um ambiente de desenvolvimento perfeito e em 1 só lugar.
