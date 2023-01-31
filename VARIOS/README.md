# Remediaciones
• Intentos de autenticación exitosos y fallidos, con prioridad en los servicios de red los cuales pueden
◦ /var/log/faillog Log deprecado
◦ /var/log/auth.log Para servidores Debian y derivados
◦ /var/log/secure Para servidores Redhat y derivados
• Uso de cualquier invocación de cuenta "root" o privilegiada, como el comando "su" (ej. Registro de "sudoers")
◦ /var/log/auth.log Para servidores Debian y derivados
◦ /var/log/secure Para servidores Redhat y derivados
• Conexiones entrantes denegadas (ej. aquellas bloqueadas por iptables)
◦ /var/log/kern.log Para servidores Debian y derivados
◦ /var/log/messages Para servidores Redhat y derivados
• Historial de comandos (ej. bitácoras del historial de bash shell), incluidos los registros de fechas
◦ Install  auditd, psacct, o acct.
◦ Instalar y configurar psacct, o acct dependiendo el sistema operativo RHEL CentOS Debian, Ubuntu y derivados
• Iniciar servicios
◦ Configurar auditd, editar el archivo /etc/audit/auditd.conf
• Gestión de Reglas audit.rules
• Configurar en rsyslog
  •/var/log/audit/audit.log
  •/var/log/auth.log
  •/var/log/cron
  •/var/log/dpkg.log
  •/var/log/messages
  •/var/log/secure
  •/var/log/sudo
  •/var/log/syslog
  •/var/log/wtmp
  •/var/log/yum.log
  •/var/log/httpd/access_log
  •/var/log/apache2/access.log

# Files
Archivos utilizados para la remedicacion 
/Debian.yaml                 
/RedHat.yaml                 
/main.yaml                   
/hosts                       
/README.md                   
/Debian                      
/Debian/50-default.conf      
/Debian/listen.conf          
/Debian/rsyslog.conf         
/Debian/kernel.yml           
/Debian/fecha.yml            
/Debian/uuid.yml             
/Debian/pkgother.yml         
/Debian/pkgaudit.yml         
/Debian/rules.yml            
/Debian/audit.yml            
/Debian/logrotatedebian.yml  
/Debian/rsyslogdebian.conf   
/Debian/copy.yml             
/inventario.tux              
/Ubuntu                      
/Ubuntu/50-default.conf      
/Ubuntu/audit.yml            
/Ubuntu/fecha.yml            
/Ubuntu/kernel.yml           
/Ubuntu/listen.conf          
/Ubuntu/logrotateother.yml   
/Ubuntu/pkgaudit.yml         
/Ubuntu/pkgother.yml         
/Ubuntu/rsyslog.conf         
/Ubuntu/rsyslogother.conf    
/Ubuntu/rsyslogrhel.conf     
/Ubuntu/rules.yml            
/Ubuntu/uuid.yml             
/Ubuntu/copy.yml             
/Ubuntu/rsyslogdebian.conf   
/CentOS                      
/CentOS/50-default.conf      
/CentOS/audit.yml            
/CentOS/cfgedit.yml          
/CentOS/copy.yml             
/CentOS/fecha.yml            
/CentOS/kernel.yml           
/CentOS/listen.conf          
/CentOS/logrotateother.yml   
/CentOS/logrotaterhel.yml    
/CentOS/logrotate.yml        
/CentOS/rhelyum.yml          
/CentOS/rsyslog.conf         
/CentOS/rsyslogother.conf    
/CentOS/rsyslogrhel.conf     
/CentOS/rules.yml            
/CentOS/uuid.yml             
/RedHat                      
/RedHat/50-default.conf      
/RedHat/listen.conf          
/RedHat/logrotateother.yml   
/RedHat/rsyslog.conf         
/RedHat/rsyslogother.conf    
/RedHat/rsyslogrhel.conf     
/RedHat/logrotaterhel.yml    
/RedHat/kernel.yml           
/RedHat/uuid.yml             
/RedHat/audit.yml            
/RedHat/fecha.yml            
/RedHat/rhelyum.yml          
/RedHat/rules.yml            
/RedHat/logrotate.yml        
/RedHat/cfgedit.yml          
/RedHat/copy.yml             
/Ubuntu.yaml                 
/CentOS.yaml                 

## Folders
Ubuntu
CentOS
Debian
RedHat


## Otros Archivos
/Debian/50-default.conf    
/Debian/listen.conf        
/Debian/rsyslog.conf       
/Debian/rsyslogdebian.conf 
/Ubuntu/50-default.conf    
/Ubuntu/listen.conf        
/Ubuntu/rsyslog.conf       
/Ubuntu/rsyslogother.conf  
/Ubuntu/rsyslogrhel.conf   
/CentOS/50-default.conf    
/CentOS/listen.conf        
/CentOS/rsyslog.conf       
/CentOS/rsyslogother.conf  
/CentOS/rsyslogrhel.conf   
/RedHat/50-default.conf    
/RedHat/listen.conf        
/RedHat/rsyslog.conf       
/RedHat/rsyslogother.conf  
/RedHat/rsyslogrhel.conf   

## DECLARAR ARCHIVO HOST 
se debe declarar en el archivo hosts las ip y los nombres de los server 
ejemplo:

[root@ss os_detector]# cat /etc/hosts
127.0.0.1   localhost localhost.localdomain localhost4 localhost4.localdomain4
::1         localhost localhost.localdomain localhost6 localhost6.localdomain6

10.92.192.10            ubuntu.lab
10.92.192.250           rhel.lab

[root@ss os_detector]# 


## INVENTARIO inventario.tux
 Se debe declarar usuario que va a ejecutar las tareas
 ejemplo 
 [all:vars]
ansible_become=yes
ansible_become_user=root
ansible_become_password=07cf04cv
ansible_become_method=su
ansible_python_interpreter=auto_silent
 
Luego declarar por SO los servers 
ejemplo 
[DebianHosts]
ubuntu.lab

[UbuntuHosts]
ubuntu.lab

[CentOSHost]
rhel.lab

[RedHatHost]
rhel.lab


## EJECUTAR
Este Playbook diferenciara el so y ejecutara la tarea para cada una de las distribuciones.

ansible-playbook -i inventario.tux main.yaml -v



#VERSION 0.1
 
  
##  Copyright 
**Aviso de Copyright**  
  


Copyright 2020  xxxxxx 
  
  
El poseedor del Copyright tiene los siguientes derechos:

Derecho a hacer copias.  
Derecho a distribuir copias.  
Derecho a hacer trabajos derivados (traducciones, adaptaciones...)  
Derecho a exposición pública.  
Estos derechos existen desde que el trabajo es creado y pertenecen al autor, este los puede vender, alquilar, transferir o donarlos individualmente o en conjunto.
  
La duración del Copyright es desde la creación de la obra hasta los 50 años posteriores de la muerte del autor.

Cuando la obra pertenece a varios autores el Copyright prevalece hasta los 50 años posteriores de la muerte del último autor.

