<!DOCTYPE html>
<html>
<body>
<h1 style="color: #5e9ca0; text-align: center;">Procedimento Instala&ccedil;&atilde;o Zabbix Agent em Massa</h1>
<h2 style="color: #2e6c80;">Sistema Windows</h2>
<p>O objetivo &eacute; instalar o agent zabbix em todos os servidores windows criando uma policy dentro do Active Directory. <br /> <br /> Para executar a instala&ccedil;&atilde;o em massa, deve-se seguir os passos abaixo.</p>
<h3 style="color: #2e6c80;">Step 1</h3>
<p>Para criar&nbsp;policy no Active Directory:</p>
<ol>
<li>Ir em&nbsp;Group policy management;</li>
<li>Group Policy Objects;</li>
<li>Clicar com bot&atilde;o direito (new);</li>
<li>Name da policy = Instalacao Zabbix Agent;</li>
<li>Clicar em ok;</li>
<li>Editar a policy criada em Windows Settings -&nbsp;Scripts -&nbsp;Startup -&nbsp;Show Files;</li>
<li>Dentro da pasta deve-se criar o script InstallZabbixAgent.bat;</li>
<li>Clicar em Add em Startup Properties;</li>
<li>Selecionar o script name;</li>
<li>Aplicar - Ok.</li>
</ol>
<p>###################################################</p>
<h3 style="color: #2e6c80;">Step 2</h3>
<p>Para que o script rode nos servidores ao reiniciar:</p>
<ol>
<li>Ir em Administrative Templates Policy Definitions;</li>
<li>System - Logon;</li>
<li>Enabled Always wait for the network at computer startup and logon;</li>
<li>Linkar a GPO diretamente no AD (Clicando com bot&atilde;o direito Link an existing GPO);</li>
<li>Selecionar o script - OK;</li>
<li>Enforce policy.</li>
</ol>
<p>&nbsp;##################################################</p>
<h3 style="color: #2e6c80;">Step 3</h3>
<p>Script (<span style="text-decoration: underline;">Alterar os campos em vermelho</span>):</p>
<p>msiexec /l*v log.txt /i "<span style="color: #ff0000;">caminho do arquivo+nome do arquivo.msi</span>" /qn LOGTYPE=file LOGFILE="C:\zabbix\zabbix_agent.log" ENABLEREMOTECOMMANDS=1 SERVER=<span style="color: #ff0000;">IP SERVER OU PROXY_ZABBIX</span> SERVERACTIVE=<span style="color: #ff0000;">IP SERVER OU PROXY_ZABBIX</span> ENABLEPATH=1 INSTALLFOLDER="C:\zabbix"</p>
<p>Ao reiniciar os servidores windows come&ccedil;a a instala&ccedil;&atilde;o, verificar na pasta C: se existe a pasta zabbix e em services.msc verificar se h&aacute; o servi&ccedil;o zabbix agent rodando.</p>
<p>&nbsp;<strong>**Obs: Colocar o arquivo instalador do zabbix agent na pasta compartilhada do Active Directory.&nbsp;</strong></p>
<p>##################################################</p>
</body>
</html>
