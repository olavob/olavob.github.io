---
date: 2025-06-12T01:11:42-03:00
draft: false
title: Resolvendo O Erro **Missing X Server or Display** Do WSL2.
type: "post"
tags: ['linux', 'windows', 'wsl', 'xserver', 'debugging']
layout: default
comments: true
---

## Contexto do Problema

Essa documentação foi criada porque estou mexendo com a parte de redes de sockets, IP, portas e Servidores HTTP. Que coincidentemente bateu com a resolução desse problema. Porém vamos deixar de lado a parte dos servidores HTTP e vamos falar de outro servidor, o X.

Graças ao sistema limitado da microsoft, o Windows, tive que reconfigurar meu linux pela milésima vez, mais especificamente o ArchWSL no WSL 2. Antes disso eu usava uma Distro Linux(distribuição Linux) dentro de uma máquina virtual apenas para escrever código, entretanto minha RAM que já é pouca, apenas 8gb, utilizando uma VM reduzindo esse valor pela metade, e quando falamos de ambientes gráficos(ainda mais do Gnome) estamos falando da maior parte da minha preciosa RAM sendo desperdiçada com janelas e área de trabalho.

Meu Vscode, com legs terríveis, acabei optando por voltar obrigatoriamente para o Windows, porém não totalmente. Por isso optei pela opção do WSL que é rodado via emulador de terminal sem um ambiente gráfico. Aproveitando o máximo de RAM e programas como Vscode e outros no Windows, sendo executado via PATH pelo WSL. 

E claro, pensando no melhor dos dois mundos, configurar ambientes gráficos rodando nativamente no linux pelo terminal não seria uma ideia tão ruim. E graças a isso, tive que lidar com um erro que passei a tarde toda para resolver, tentativa e erro, diagnosticando com toda a calma ou pelo menos quase toda a calma.

**Uma dica**, se você tem algum problema que não consegue resolver, a última coisa que deve fazer é dar um "power off". Mudar de sistema ou de ferramenta é a pior maneira de resolver um problema, é um canhão para matar uma mosca, e no final a mosca pode até mesmo ter sobrevivido e pousar em cima do seu nariz de novo. Normalmente, a culpa disso tudo é apenas sua e da sua ignorância o que pode resultar no problema poder ser resolvido de uma forma super fácil e simples. Mas não se preocupe com isso, sempre vai ocorrer, porém nem todos têm a coragem e muito menos a vontade de pensar e colocar a mão na massa. Cruzar os braços e reclamar com certeza não é a solução, mas é o jeito mais fácil de lidar com a situação, e isso sim, é o que todos fazem.

E esse é o motivo de toda a documentação da resolução do erro ``Missing X server or $DISPLAY```.

## Configurações e Detalhes do Servidor X

O X é um servidor remoto que gerencia e implementa ambientes gráficos para os monitores. Em em sistema operacional temos dispositivos como teclado, mouse e a tela. Uma tela é gerenciada por um programa de servidor, que exibe recursos para outros programas que se conectam a ele.

O servidor sabe onde redimensionar o tráfego da rede através da definição da variável de ambiente $DISPLAY, que aponta para o servidor X localizado no seu sistema.

O servidor X já vem de graça pré-configurado de forma dinâmica em qualquer distro Linux, porém já que estou com o WSL, o buraco é mais embaixo. Teremos que instalar e configurar manualmente o servidor no windows.

Umas das opções mais recomendadas é o "X410 - X Server for Windows", encontrado na Microsoft Store, outra opção é o "VcXsrv - Open-Source X Server for Windows", por ser totalmente gratuito é ele mesmo que vamos utilizar.

Baixe o [VcXsrv](https://sourceforge.net/projects/vcxsrv/).

Depois de instalar o servidor vamos executá-lo e definir algumas configurações de portas do endereço IP que vai ser o host, para definir o número de display e telas. a ordem é:

 - Selecione "Multiple windows"
 - Display number: **0**
 - Marque "Start no Client"
 - Marque "Disable access control" (para permitir coneções do WSL)
 - Salve as configurações e inicie o servidor

Dentro do terminal de uma distro linux quando executamos ```echo $DISPLAY``` normalmente a saída será em nome: ```:0.0```, ou seja hostname:D.S(hostname:displaynumber.screennumber). Que significa tela S no display D do hostname. Pode parecer confuso mas para esclarecer, essas informações são usadas pelos aplicativos para determinar como ele deve se conectar ao servidor e qual tela será usado por padrão, no caso em "displays" com vários monitores, ou em "telas" com várias janelas, comumente em estações de trabalho de multiusuários.

O "display" da frase displaynumber é usado para a consulta de uma coleção de monitores que compartilham um teclado comum e ponteiro(mouse, tablet, etc). 

O número de exibição deve ser sempre dado em exibição.screennumber. Alguns monitores compartilham um único teclado e ponteiro, entre dois ou mais monitores. Cada monitor tem seu conjunto de janelas.

```:0.0``` significa que estamos falando da primeira tela anexada à seu primeiro display no seu host local.

## Soluções Tentadas

Primeiramente fui pesquisar em fóruns a causa do problema, e as respostas sempre foram em CentOS ou Ubuntu, nada relacionado ao servidor X no WSL/Archlinux. Sem outra medida, e com a pressa de resolver o problema, perguntei para IAs como Deepseek e ChatGPT, mais especificamente o Deepseek, que me mandou prompts para mudar a versão do WSL, e ficou me gerando respostas em loop para fazer export do localhost no $DISPLAY, o que é totalmente inútil para resolução e como disse, se eu tivesse feito isso, com certeza eu não teria resolvido no mesmo dia. 

Já o ChatGPT me ajudou com os comandos de Powershell, que me poupou horas de google e documentação.

Para rodar um programa dentro do terminal é só instalá-lo usando o gerenciadores de pacotes ```yay```(se instalado) ou o ```pacman``` e executá-lo, algo como ```chromium```.

Quando fui executar deu o erro, ```Missing X server or $DISPLAY```, tentei dar o export do seguinte comando seguindo as instruções do Deepseek:

```bash
export DISPLAY=$(grep nameserver /etc/resolv.conf | awk '{print $2}'):0.0
```

Ou até mesmo executar o Chromium com algumas Flags:

```bash
chromium --no-sandbox --disable-dev-shm-usage --use-gl=angle --disable-gpu
```

E mesmo assim o erro se repetia, me forçando a pensar mais a fundo. 

## Resolução do Erro

Esse comando ```export``` pega o valor da variável nameserver dentro de ```/etc/resolv.conf``` e coloca como valor da nossa variável de ambiente
$DISPLAY. Então, vamos começar a destrinchar para entendermos o erro bobo que não vemos.

Primeiro vamos entender o arquivo do diretório ```/etc/resolv.conf```

Dentro do seu navegador quando se acessa https://www.google.com vai certamente abrir magicamente a página do mecanismo de pesquisa google. Porém, se falamos mais tecnicamente, porque não acessar o google com seu endereço IP direto? algo como http://142.250.79.4:80 Já que todos os sites têm endereços IP que podem se comunicar via WebSockets com um cliente(navegador) ou com os próprios servidores internos para aí sim ter a resposta que já é esperada. Então, porque usar o DNS, a resposta é simples: é mais fácil e memorável, porém os benefícios de um DNS(Domain Name System) não acabam aí.

Endereços IPs variam de acordo com o dispositivo e da região geográfica, já que depende do balanceador de carga do Google para selecionar o servidor. Por isso google.com é uma forma padrão que calibra automaticamente o IP da sua região ou do seu dispositivo no DNS.

A função principal do ```resolv.conf``` é configurar parâmetros e listar IPs remotos de servidores DNS do sistema ou um serviço local que aponta para um intermediário.

O WSL não possui um canal de rede própria já que é integrado com o Windows. então quando vemos o resolv.conf, o valor de nameserver é o endereço do gateway local do roteador que funciona como um proxy do DNS, que é o que o windows usa para encaminhar as consultas nos servidores DNS.

Ou seja, precisaremos de um IP do seu host Hyper-v para colocar no $DISPLAY. Não o IP do proxy do fuc** roteador TP-LINK da banda larga sei lá das quantas que tem na sua cidade.

Bem, esse é o ponto crítico, a parte fácil que não sabemos. Agora vamos colocar o servidor X para funcionar.

O comando Export é a pior forma de resolver esse problema no WSL, porém deu a mim a pista mais importante da resolução já que o $DISPLAY precisava de um IP para que o meu WSL pudesse se comunicar com o VcXsrv. Vamos dividir a resoluição em passos para facilitar.

#### Passo 1: Identificar o IP do Host Windows  

Vamos pegar o endereço IP do Windows para a comunicação com o WSL2 que usa a tecnologia de virtualização Hyper-v. Dentro de um powerShell execute:

```PowerShell
Get-NetIPAddress -InterfaceAlias "vEthernet (WSL (Hyper-V firewall))"
```

vamos confirmar a saida:

```PowerShell
InterfaceAlias    : vEthernet (WSL (Hyper-V firewall))
```

e pegar o endereço IP:

```PowerShell
IPAddress         : 172.23.112.1
```

#### Passo 2: Configurar o $DISPLAY no Shell  

Para a insistência já que o resolv.conf é modificado automaticamente após a incialização, no seu ```.bashrc``` ou ```.zshrc``` adicione no final:

```bash
echo 'export DISPLAY=172.23.112.1:0.0' >> ~/.bashrc
source ~/.bashrc  
```

#### Passo 3: Testar o Ambiente Gráfico 

Não se esqueça de estar com o servidor X ligado no Windows sempre que for usar o ambiente gráfico. execute o chromium ou seu aplicativo grafico:

```bash
chromium  
```

![Imagem do servidor funcionando](https://i.ibb.co/5gpX7HLK/Resolved-xserver-error.png)

E lá está... funcionando perfeitamente. Resolver um problema após horas de tentantiva e erro é muito aliviante, é como receber uma notícia boa.

A sequir um extra, um problema que topei no meio do caminho, mas é mais falta de atenção mesmo, já que basta apenas marca a opção correta da configuração do servidor:

## Problemas Comuns e Soluções

#### Erro: "Authorization required, but no authorization protocol specified"
- Cause: Controle de acesso do X Server ativo.  
- Solução: Marque **Disable access control** no VcXsrv.