安装要点:
安装WAS 

C1G35ML/WAS/responsefile.nd.txt


./install -options responsefile.nd.txt -silent
  responsefile.nd.txt 文件就在安装文件目录下，改改就可以用：
 -OPT silentInstallLicenseAcceptance="true"   //接受license协议，这个必须接受：true
 -OPT disableOSPrereqChecking="true"    //操作系统检查忽略
 -OPT checkFilePermissions="true"       //文件许可检查
 -OPT installType="installNew"     //安装类型
 -OPT profileType="none"          //不创建profile
 -OPT feature="languagepack.console.all"     //安装语言包
 -OPT feature="languagepack.server.all"
 -OPT PROF_enableAdminSecurity="true"        //启用安全性，配置用户名、密码
 -OPT PROF_adminUserName=wasadmin
 -OPT PROF_adminPassword=kengdiede2013
 -OPT installLocation="/opt/IBM/WebSphere/AppServer"   //产品安装目录，这个是关键，必须设

日志：
/root/waslogs/trace.txt
/root/waslogs/log.txt

安装补丁包安装程序 UpdateInstaller
/C1G36ML/UpdateInstaller/responsefile.updiinstaller.txt


注意：要把windows环境相关的配置参数注释掉
./install -options responsefile.updiinstaller.txt -silent
responsefile.updiinstaller.txt 必要配置：
-OPT silentInstallLicenseAcceptance="true"    //接受license协议，这个必须接受：true
-OPT installLocation="/opt/IBM/WebSphere/UpdateInstaller"    //产品安装目录，这个是关键，必须设

logs:  
/data/IBM/WebSphere/UpdateInstaller/logs/install


安装补丁包
/opt/IBM/WebSphere/UpdateInstaller/responsefiles/install.txt

./update.sh -silent -options "responsefiles/install.txt"
responsefiles/install.txt 文件必要配置项
-W maintenance.package=/home/software
-W product.location="/opt/IBM/WebSphere/AppServer"
-W update.type="install
查看安装进度：/opt/IBM/WebSphere/UpdateInstaller/logs/install/log.txt

创建dmgr Profile
DMGR
./manageprofiles.sh  -create -profileName Dmgr01 -profilePath /opt/IBM/WebSphere/AppServer/profiles/Dmgr01 -templatePath /opt/IBM/WebSphere/AppServer/profileTemplates/dmgr -enableAdminSecurity true -adminUserName wasadmin -adminPassword zone2013 -cellName gxCell01 -hostName uniflow-gx -nodeName gxCellManager01 -isDefault

Custom
./manageprofiles.sh -create -profileName Custom01 -profilePath  /opt/IBM/WebSphere/AppServer/profiles/Custom01 -templatePath /opt/IBM/WebSphere/AppServer/profileTemplates/managed

