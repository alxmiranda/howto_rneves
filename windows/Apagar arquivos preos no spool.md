##Como limpar o spool do windows

Voc� mandou uma impress�o errada, cancelou, mas o Windows continua a imprimir aqueles caracteres malucos? 

Voc� reiniciou o computador, desligou a impressora e isso n�o resolveu ? 

Tudo bem, todos n�s passamos por isso, vez ou outra. 

Para limpar a fila de impress�o desses arquivos e voltar a opera��o normal siga os passos abaixo:

Abra uma janela do MS-Dos, como administrador e execute os comandos abaixo:

```
net stop spooler <Enter>
cd c:\windows\system32\spool\PRINTERS <Enter>
del /f /s *.shd <Enter>
del /f /s *.spl<Enter>
net start spooler <Enter>
exit <Enter>
```

Voc� tamb�m pode montar esse comandos em um arquivo .BAT e automatizar o processo.


