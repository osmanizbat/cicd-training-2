Bu eğitimde [cicd-training-1](https://github.com/osmanizbat/cicd-training-1) ve [cihanca-devopz](https://github.com/osmanizbat/cihanca-devopz) eğitimlerinde Virtualbox üzerinde hazırlamış olduğumuz __jenkins__ sunucusunu bu eğitimde de kullanacağız.

# Minikube kurulumu

1. Bilgisayarınızın BIOS ayarlarında Virtualization ile ilgili özelliklerin seçili olduğundan ve Windows "Control Panel\Programs\Programs and Features -> Turn Windows Features on or off" ekranında Hyper-V özelliğinin aktif olmadığından emin olun. 

2. Windows Terminal ya da Command Prompt ekranında __winget__ komutuyla kurulumu başlatıyoruz. 
    ~~~
    winget install minikube
    ~~~
    
3. __minikube__ kurulumu sonrası terminali kapatıp yeniden açtıktan sonra aşağıdaki komutla lokal kubernetes clusterı başlatıyoruz.
    ~~~
    minikube start --no-vtx-check
    ~~~

4. kubectl, helm vs. bazı araçları kopyalacağımız dizini ve PATH ortam değişkenin hazırlıyoruz. Administrator olarak çalıştırdığımız Windows Command Prompt'ta:
    ~~~
    md %HOME%\bin
    setx PATH "%PATH%;%HOME%\bin"
    exit
    ~~~    


# app-server sunucusuna Minikube kurulumu

1. __app-server__ makinesi kapalıyken Virtualbox makine ayarlarında CPU 2'ye, Memory 4096 MB'a çıkarılarak makine başlatılır. 

2. Paket kurulumu yapılarak minikube başlatılır:
    ~~~
    curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube_latest_amd64.deb
    sudo dpkg -i minikube_latest_amd64.deb
    minikube start
    ~~~
    
3. kubectl komutuyla local clusterımızda çalışan podları listeliyoruz: 
    ~~~
    minikube kubectl -- get pods -A
    ~~~

4. kubectl komutunu daha pratik kullanabilmek için alias tanımlıyoruz:
    ~~~
    echo 'alias kubectl="minikube kubectl --"' >>  ~/.bash_aliases
    source ~/.bash_aliases
    ~~~
