# CentOS install

1. Download a ISO do [CentOs], recomendado versão everything
2. Instalar o CentOs, seguindo o wizard, recomendado versão Server Infrastructure.
3. Configurar a rede:
    - Verificar o nome da placa de rede (coluna DEVICE):
    ``` nmcli d ```
    - Editar o arquivo de configuração referente a placa de rede
    ``` vi /etc/sysconfig/network-scripts/ifcfg-NOME_DA_PLACA ```
    - Para IP dinâmico, editar as linhas BOOTPROTO e ONBOOT para
        ```
        BOOTPROTO=dhcp
        ONBOOT=yes
        ```
    - Para IP estático, editar as linhas BOOTPROTO e ONBOOT e as configurações para:
        ```
        BOOTPROTO=static
        ONBOOT=yes
        
        IPADDR=ENDEREÇO_IP
        NETMASK=MASCARA
        GATEWAY=GATEWAY
        DNS1=DNS Principal
        DNS2-DNS Secundario
        ```
    - Reiniciar o service de rede:
    ``` systemctl restart network ```

4. Configurar o SSH:
    - Instalar o OpenSSH e suas dependências:
    ``` yum install openssh openssh-server openssh-clients openssl-libs```
    - Criar uma cópia do arquivo de configuração padrão, por questões de segurança
    ``` cp /etc/ssh/sshd_config /etc/ssh/sshd_config.orig ```
    - Agora podemos editar o arquivo de configuração
    ``` vi /etc/ssh/sshd_config ```
    - Para aplicar as novas configurações é só reiniciar o serviço de ssh
    ``` systemctl restart sshd.service ```
5. Instalar o Docker:
    - Para esse passo podemos seguir a [documentação do Docker]


   [CentOs]: https://www.centos.org/download/
   [documentação do Docker]: https://docs.docker.com/engine/installation/linux/docker-ce/centos/#install-using-the-repository
