#########################################################CASE 1###########################


CentOS-7-x86_64-DVD-2009.iso dosyasını kullanarak VMware Workstation 16 Player bir sanal makine kurdum.

**sudo yum update -y**

Güncellemeleri yaptım.

**adduser omerfaruk.cinar**

**passwd omerfaruk.cinar**

**usermod -aG wheel omerfaruk.cinar**

**su – omerfaruk.cinar**


Kullanıcı oluşturdum, parola belirledim ve sudo erişimi sağladım.

Sonrasında sanal makinayı kapatıp manuel olarak, kurmuş olduğum sanal makinaya VMware ayarları üzerinden 10gb ekstra depolama alanı verdim ve sanal makinayı tekrar başlattım.

**lsblk**

Yeni eklediğim diski(sdb)doğruladım. 

**mkdir bootcamp**

**sudo mkfs.ext4 /dev/sdb**

**sudo mount /dev/sdb /bootcamp**

Yeni eklediğim diski bootcamp olarak mount ettim.

**lsblk**

Mount işleminin başarıyla tamamlandığını doğruladım.

**cd /opt**

İlgili dizine gittim.

**sudo mkdir -p /opt/bootcamp/ && sudo touch /opt/bootcamp/bootcamp.txt**

Bootcamp directory oluşturup içerisine bootcamp metin belgesi ekledim.

**sudo nano /opt/bootcamp/bootcamp.txt**

"nano" metin düzenleyicisini kullanarak bootcamp.txt dosyasına "merhaba trendyol" yazıp kaydettim.

**sudo find /home -type f -name "bootcamp.txt" -exec mv {} /opt/bootcamp**

Son olarak tek bir komut ile bootcamp.txt dosyasını home dizini üzerinden bulup bootcamp diskine taşıdım.


#########################################################CASE 2###########################



CentOS-7-x86_64-DVD-2009.iso dosyasını kullanarak VMware Workstation 16 Player bir sanal makine kurdum.

**sudo yum update -y**

Güncellemeleri yaptım.

**sudo yum install epel-release**

Epel reposunu ekledim.

**sudo yum install ansible**

Ansible kurulumunu yaptım.

**mkdir myplaybooks**

Playbook'ları barındıracak bir dizin oluşturdum.

**cd myplaybooks/** , komutu ile oluşturduğum dizine gittim.

**vim install_docker.yml**

Docker kurulumunu yapacağım playbook'u oluşturdum.

**vim dockerize_wordpress.yml**

Database kullanan uygulama olarak seçmiş olduğum Wordpress'in dockerize işlemi için playbook oluşturdum.

**vim install_nginx.yml**

Nginx kurulumu ve serve işlemini gerçekleştirmek için bir playbook oluşturdum.

**vim index.html**

"Hosgeldin DevOps" yazısını içeren bir index.html sayfası oluşturdum.

**ansible-playbook install_docker.yml**

Docker kurulumunu ansible ile başlattım.

**systemctl status docker**

Docker kurulumunun gerçekleştiğini doğruladım.

**ansible-playbook dockerize_wordpress.yml**

Wordpress uygulamasını dockerize ettim ve localhost üzerinden doğruladım.

**ansible-playbook install_nginx.yml**

Nginx kurulumunu gerçekleştirdim ve index.html sayfasını serve ettim.

