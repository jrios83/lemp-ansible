lemp-tutorial
================

Source: https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-centos-7


software factory
================
1. The ansible installation was done inside a virtualized workspace with python3, but it can run in a non-virtualized environment

2. For my tests I used an Amazon EC2 instance. The requirements.txt file is included in case you want to perform the tests in aws; however, this was only with penalties of having an evidence objective. The execution can be done on the localhost as requested. The command to run the requirements is: pip install -r requirements.txt

3. Centos version used for testing was Centos7 (x86_64) ami-0a531e5afd4d5f3ad

4. Nano editor is installed as suggested in the tutorial, but it is not used to modify the configuration files, in this case regexp and replace from ansible or by transfer are used in case of creating new files.

Execution
=========
1. The myhosts file contains the ansible inventory, you can change the localhost value to any IP if necessary.

2. A role called lemp was created which has multiple tasks which are called in order from the mail.yml

3. The execution is carried out with the following command: ansible-playbook play-book.yml -i myhosts, if it is required to execute it in an aws instance the command would be: ansible-playbook play-book.yml -i aws_ec2.yaml -u centos --private-key ~/Downloads/challenge.pem (replace challenge.pem with the name of your key)

4. During the execution of the play-book, the ip of eth0 will be displayed on the screen. If the network interface is different from eth0, the data must be adjusted in the nginx.yml file in the debug section.

5. The ip data is important because it will be placed in the default.conf file inside the files folder according to the tutorial.

6. The main.yml file in vars stores the mariadb root password; the tutorial does not specify the use of the vault for password encryption, so it is not included in this development.

test and close
=============
1. To verify the operation, according to the tutorial, you must enter the ip/info.php

2. step 9, which removes the info.php for security reasons according to the tutorial, is commented out; it can be uncommented after verifying the operation so that it can proceed with its elimination as suggested.


######################## Spanish section ############################

Tutorial de lemp
================

Fuente: https://www.digitalocean.com/community/tutorials/how-to-install-linux-nginx-mysql-php-lemp-stack-on-centos-7


Software Factory
================
1. La instalación de ansible se realizó dentro de un espacio de trabajo virtualizado con python3, pero puede ejecutarse en un entorno no virtualizado

2. Para mis pruebas utilicé una instancia EC2 de amazon. Se incluye el archivo requirements.txt en caso se desee realizar las pruebas en aws; sin embargo, esto solo fue con fines de tener un target de pruebas. La ejecución puede realizarse en el localhost como fue solicitado. El comando para ejecutar los requisitos es: pip install -r requirements.txt

3. La versión de Centos utilizada para las pruebas fue Centos7 (x86_64) ami-0a531e5afd4d5f3ad

4. Se instala nano editor como se sugiere en el tutorial, pero no es utilizado para modificar los archivos de configuración, para ese caso se utiliza regexp y replace de ansible o por transferencia en caso de crear archivos nuevos.

Ejecución
=========
1. El archivo myhosts contiene el inventario de ansible, se puede cambiar el valor localhost por alguna IP de ser el caso.

2. Se creó un rol llamado lemp el cual tiene múltiples tasks los cuales son llamados en orden desde el mail.yml

3. La ejecución se realiza con el siguiente comando: ansible-playbook play-book.yml -i myhosts, en caso se requiera ejecutarlo en una instancia aws el comando sería: ansible-playbook play-book.yml -i aws_ec2.yaml -u centos --private-key ~/Descargas/challenge.pem (reemplazar challenge.pem por el nombre de su key)

4. Durante la ejecución del play-book se pintará en pantalla la ip del eth0, si la interface de red es diferente a eth0, se debe ajustar el dato en el archivo nginx.yml en la sección debug.

5. El dato de la ip es importante porque se colocará en el archivo default.conf dentro de la carpeta files de acuerdo con el tutorial. 

6. El archivo main.yml en vars guarda la contraseña del root de mariadb; el tutorial no especifica el uso de vault para encriptamiento de contraseñas, por eso no se incluyó en el presente desarrollo.

Test y cierre
=============
1. Para verificar el funcionamiento, de acuerdo con el tutorial, se debe ingresar la ip/info.php

2. el paso 9, el cual elimina el info.php por motivos de seguridad de acuerdo con el tutorial, se encuentra comentado; puede descomentarse luego de verificar el funcionamiento para que se proceda con su eliminación como es sugerido.
