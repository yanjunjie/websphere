��װҪ��:
��װWAS 

C1G35ML/WAS/responsefile.nd.txt


./install -options responsefile.nd.txt -silent
  responsefile.nd.txt �ļ����ڰ�װ�ļ�Ŀ¼�£��ĸľͿ����ã�
 -OPT silentInstallLicenseAcceptance="true"   //����licenseЭ�飬���������ܣ�true
 -OPT disableOSPrereqChecking="true"    //����ϵͳ������
 -OPT checkFilePermissions="true"       //�ļ���ɼ��
 -OPT installType="installNew"     //��װ����
 -OPT profileType="none"          //������profile
 -OPT feature="languagepack.console.all"     //��װ���԰�
 -OPT feature="languagepack.server.all"
 -OPT PROF_enableAdminSecurity="true"        //���ð�ȫ�ԣ������û���������
 -OPT PROF_adminUserName=wasadmin
 -OPT PROF_adminPassword=kengdiede2013
 -OPT installLocation="/opt/IBM/WebSphere/AppServer"   //��Ʒ��װĿ¼������ǹؼ���������

��־��
/root/waslogs/trace.txt
/root/waslogs/log.txt

��װ��������װ���� UpdateInstaller
/C1G36ML/UpdateInstaller/responsefile.updiinstaller.txt


ע�⣺Ҫ��windows������ص����ò���ע�͵�
./install -options responsefile.updiinstaller.txt -silent
responsefile.updiinstaller.txt ��Ҫ���ã�
-OPT silentInstallLicenseAcceptance="true"    //����licenseЭ�飬���������ܣ�true
-OPT installLocation="/opt/IBM/WebSphere/UpdateInstaller"    //��Ʒ��װĿ¼������ǹؼ���������

logs:  
/data/IBM/WebSphere/UpdateInstaller/logs/install


��װ������
/opt/IBM/WebSphere/UpdateInstaller/responsefiles/install.txt

./update.sh -silent -options "responsefiles/install.txt"
responsefiles/install.txt �ļ���Ҫ������
-W maintenance.package=/home/software
-W product.location="/opt/IBM/WebSphere/AppServer"
-W update.type="install
�鿴��װ���ȣ�/opt/IBM/WebSphere/UpdateInstaller/logs/install/log.txt

����dmgr Profile
DMGR
./manageprofiles.sh  -create -profileName Dmgr01 -profilePath /opt/IBM/WebSphere/AppServer/profiles/Dmgr01 -templatePath /opt/IBM/WebSphere/AppServer/profileTemplates/dmgr -enableAdminSecurity true -adminUserName wasadmin -adminPassword zone2013 -cellName gxCell01 -hostName uniflow-gx -nodeName gxCellManager01 -isDefault

Custom
./manageprofiles.sh -create -profileName Custom01 -profilePath  /opt/IBM/WebSphere/AppServer/profiles/Custom01 -templatePath /opt/IBM/WebSphere/AppServer/profileTemplates/managed

