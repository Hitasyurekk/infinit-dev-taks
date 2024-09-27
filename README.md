![image](https://github.com/user-attachments/assets/8150f4b4-5fd6-4254-884b-92ae1a8fba2a)# infinit-dev-taks

# TR Rehber

**Hali hazırda boş bir vps varsa üzerinde çalışabilirsiniz. Tavsiyem workspace kullanmanız ücretsiz ve işinizi görecektir.**


## 1. Adım sistem değişkenlerini kurma
WorkSpace'e giriş yaptıktan sonra başlangıçta ihtiyacımız olan yazılımları kuruyoruz.

```
curl https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.0/install.sh | bash
 
export NVM_DIR="$HOME/.nvm"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh"  # This loads nvm
[ -s "$NVM_DIR/bash_completion" ] && \. "$NVM_DIR/bash_completion"  # This loads nvm bash_completion
 
nvm install 22
nvm alias default 22
nvm use default
```

**Kodları girdikten sonra ekranınız böyle olacaktır.**

![image](https://github.com/user-attachments/assets/c40f97f7-5aa7-403d-9e9e-3728749e0a82)

**Bu kodumuz ile Foundry kuracağız.**

```
foundryup
curl -L https://foundry.paradigm.xyz | bash
source /root/.bashrc
foundryup
```
![image](https://github.com/user-attachments/assets/ede789f0-c1a6-4abc-afee-eecbdd8f79f2)

**Bu kodumumuz ile Bun kuracağız.**

```
curl -fsSL https://bun.sh/install | bash
source /root/.bashrc
```
![image](https://github.com/user-attachments/assets/368f80a9-578e-4e0a-a322-8520f284ded9)


**Kurulum İşlemlerini tamamladık sıra 2. adımda.**

## 2. Adım Proje oluşturma

**İlk adım olark bir proje dosyası oluşturacağız.**

```
mkdir my-first-project
cd my-first-project
```

![image](https://github.com/user-attachments/assets/b256281b-759a-4a3f-be77-198eea507540)

**Şimdi yeni bir proje başlatmak için altta ki komutu giriyoruz önce source komutunu çalıştırın path'i güncelleyin**

```
source ~/.bashrc
bun init -y
```
![image](https://github.com/user-attachments/assets/6979a82d-75d5-46b1-ab09-19e2af466120)

**İnfinit cli paketini indiriyoruz**
```
bun add @infinit-xyz/cli
```

![image](https://github.com/user-attachments/assets/56a03577-6267-44b8-89a8-40a481dad1f3)



