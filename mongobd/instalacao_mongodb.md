mongodb - instala��o windows

1) Pr� requisitos: Windows Server 2008 R2, Windows 7 ou superior, vers�es de 32 ou 64bits, sempre que poss�vel utilize a vers�o 64.  Apesar de eventualmente funcionar no server 2003, consulte a documenta��o, � desaconselh�vel na medidade que que este SO n�o tem mais suporte ou atualiza��o.

2) Para determinar a vers�o SO onde ser� instalado o servidor execute os seguintes comandos no prompt do DOS ou no powershell

wmic os get caption
wmic os get osarchitecture

3) Fa�a o download da vers�o adequada do mongodb para o seu caso no endere�o: https://www.mongodb.org/downloads?_ga=1.37022885.48052022.1445543724#production

   Voc� pode fazer o download do vers�o compactada ou instalador windows, n�o faz diferen�a qual delas vai utilizar na medida em que o mongodb � autocontido, ou seja tudo ser� instalado em uma �nica pasta sem depend�ncias externas do Sistema Operacional.
   
4) O padr�o de instala��o assume que o software e a pasta de dados ficam no disco principal do seu computador: o drive c:, como esse tipo de instala��o pode n�o ser interessante, seja por quest�es de tempo de acesso ou espa�o dispon�vel. 

   c:\mongodb\bin  - programas
   c:\data\db      - dados
   
   A t�tulo de exec�cio vamos documentar a instala��o de programa e dados num disco secund�rio D:, para a instala��o padr�o basta substituir a drive de d: para c: ou omitir a informa��o.
   
   d:\mongodb\bin       - programas
   d:\mongodb\data\db   - dados
   d:\mongodb\data\log  - arquivos de log
   
5) Crie a estrutura de pastas no local escolhido e execute o instalador:

   msiexec.exe /q /i mongodb-win32-x86_64-2008plus-ssl-3.0.7-signed.msi INSTALLLOCATION="D:\mongodb" ADDLOCAL="all"
   
   caso tenha feito o download compactado descompacte e mova os arquivos para a pasta d:\mongodb

   Para maiores iforma��es das op��es de instala��o consulte: https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows
   
   Programs isntalados na pasta bin:
   
   Server	        mongod.exe
   Router	        mongos.exe
   Client	        mongo.exe
   Monitoramento        mongostat.exe, mongotop.exe
   ImportExporta��o	mongodump.exe, mongorestore.exe, mongoexport.exe, mongoimport.exe
   Miscellanea  	bsondump.exe, mongofiles.exe, mongooplog.exe, mongoperf.exe

6) Voce pode subir o servidor como um servi�o do windows ou no prompt do cmd ou no powershell e neste caso a janela o prompt dever� ficar aberta durante a utiliza��o.


Crie um arquivo mongodb.cfg em d:\mongodb\bin, com o seguinte conteudo:

systemLog:
    destination: file
    path:        d:\mongodb\data\log\mongod.log

storage:
    dbPath:      d:\data\db

net:
   bindIp:       127.0.0.1
   port:         27017
   
ATEN��O: N�o utilize tab e sim espa�o para identa��o. Este s�o par�metros b�sicos do mongodb que voc� pode querer alterar por segunran�a ou comodidade em sua rede local.

Esta configura��o diz ao servidor para aceitar conex�es apenas no localhost e na porta padr�o, para permitir acesso a partir de outras esta��es de trabalho altere o bind, caso utilize outra porta n�o esquec�a de libera-la no firewall e infoma-la ao carregar o client.

 
6A) Executando o servidor no terminal, abra o powersell e digite:

d:\mongodb\bin\mongod -f d:\mongodb\bin\mongo.cfg

lembre-se que voc� ode economizar digita��o colocando o caminho dos execut�veis na vari�vel de ambinete PATH do windows, isso n�o se aplica para o arquvio de configura��o, ent�o voce pode optar se posicionar na pasta d:\mongodb\bin antes de subir o servidor.

6B) Executando o servidro como servi�o no windows

para instalar o servico execute o terminal ( cmd ou powershell como administrador e execute o seguinte comando:

"D:\mongodb\bin\mongod.exe" --config "D:\mongodb\mongod.cfg" --install

Iniciar o servidor:

net start MongoDB

Para o servidor

net stop MongoDB

Desinstalar o servi�o no windows

"D:\mongodb\bin\mongod.exe" --remove

fonte: https://docs.mongodb.org/manual/tutorial/install-mongodb-on-windows/