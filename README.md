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

5. https://dl.k8s.io/release/v1.26.0/bin/windows/amd64/kubectl.exe adresinden indirdiğimiz dosyayı 4. adımda olıuşturduğumuz bin dizinine kaydediyoruz.

6. https://get.helm.sh/helm-v3.10.3-windows-amd64.zip adresinden indirdiğimiz dosyanın içerisinde bulunan helm.exe'yi 4. adımda oluşturduğumuz bin dizinine kaydediyoruz.

