
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

**Şimdi yeni bir infinit projesi için son olarak bu komutu yazıyoruz ve ok tuşları ile holesky , uniswap seçip Y diyerek işlemi onaylıyoruz**
```
bunx infinit init
```

![image](https://github.com/user-attachments/assets/d1b66e46-9dc4-4e4e-9155-21e37ea68420)

## 3. Adım Hesap oluşturma

**Şimdi burada yeni bir hesap oluşturuacağız**

```
bunx infinit account generate
```
**Ekranda bir hesap oluşturuyoruz kullanıcı adı ve şifre giriyoruz kaybetmeyin.**
![image](https://github.com/user-attachments/assets/706d7639-9b3e-413b-9325-f25bc896b4b5)

**Hesap oluşturduktan sonra hesap bilgilerinizi vericek bunları kaydedin kaybetmeyin. Buraya Test token göndereceğiz.**

![image](https://github.com/user-attachments/assets/03ca534e-d2af-4ea3-91cf-0643cac42bdc)


## 4. adım Scritpleri çalıştırmak

**Önce script klasörüne gireceğiz sonrasında Uniswap kodlarını çalıştırıcağız. Cüzdanınınıza holesky test ağında token göndermeyi unutmayın.**

```
cd src
cd scripts
```

# Uniswap V3 

```typescript
import { DeployUniswapV3Action, type actions } from '@infinit-xyz/uniswap-v3/actions';
import type { z } from 'zod';

type Param = z.infer<typeof actions['init']['paramSchema']>;

// Gerçek parametrelerle değiştirin
const params: Param = {
  // Yerel para birimi etiketi (örn: ETH)
  "nativeCurrencyLabel": 'ETH', // Tırnak içinde

  // Proxy yöneticisinin sahibi adresi
  "proxyAdminOwner": '0xc5709e9ec34e654fcbee62fc618d7cc96043bc69', // Tırnak içinde

  // Fabrikanın sahibi adresi
  "factoryOwner": '0xc5709e9ec34e654fcbee62fc618d7cc96043bc69', // Tırnak içinde

  // Sarılmış yerel token adresi (örn: '0x123...abc')
  "wrappedNativeToken": '0x6B5817E7091BC0C747741E96820b0199388245EA' // Tırnak içinde
}

// Gerçek hesap ID'si ile değiştirin
const accounts = {
  "deployer": "hitasyurek"
}

export default { params, signer: accounts, Action: DeployUniswapV3Action };


```
**Bilgileri verdiğim örnek kodda ki gibi değiştirin ve resimde ki kodları silip kendi değiştirdiğiniz kodu yapışitırın. Ben kendi cüzdan adresimi girdin siz terminal içinde ki kendi cüzdan adresinizi girikcesiniz.**

![image](https://github.com/user-attachments/assets/513a0b65-874a-48e8-98e4-807786afd9fc)

**Script'i çalıştırmak için kodu giriyoruz.**
```
bunx infinit script execute deployUniswapV3Action.script.ts
```

**Şifremizi girip işlemleri onaylıyoruz** 

![image](https://github.com/user-attachments/assets/1b2f78e6-209d-4639-b30a-7ed8d9e2f57c)

**Bu ekran geldiğinde bu adımda tamamlanmıştır**

![image](https://github.com/user-attachments/assets/2664b50b-0a17-4705-b83c-15fe638d9130)

## 5. Adım Early Rolunu almak ve her şeyi bitirmek.

**Kodu çalıştırarak scriptleri sıralıyoruz**

```
bunx infinit script generate
```
![image](https://github.com/user-attachments/assets/08d0038a-2760-41fd-b1f7-8026a1ebce30)

**Şimdi örnek bir script oluşturuyoruz içine girip düzenleyeceğiz**
```
bunx infinit script generate setFactoryOwnerAction
```

**Şimdi bilgileri kendi bilgilerinize göre düzenleyin.**

```typescript
import { SetFactoryOwnerAction, type actions } from '@infinit-xyz/uniswap-v3/actions'
import type { z } from 'zod'
 
type Param = z.infer<typeof actions['setFactoryOwnerAction']['paramSchema']>
 
// TODO: Gerçek parametrelerle değiştirin
const params: Param = {
 
  // TODO: Uniswap V3 fabrikasının adresini girin
  "uniswapV3Factory": undefined,
 
  // TODO: Yeni sahibi belirtin
  "newOwner": undefined
}
 
// TODO: Gerçek imzacı kimliğini belirtin
const signer = {
  "factoryOwner": ""
}
 
export default { params, signer, Action: SetFactoryOwnerAction }
```

**Bu işlemden sonra scriptson kodumuzu çalıştırarak işlemleri bitiriyoruz**

```
bunx infinit script execute setFactoryOwnerAction.script.ts
```

**Çıktı bu şekilde olduysa işlem tamamlanmıştır. , yapmanız gereken tek şey altta vereceğim şablonda bu SS'i alarak tweet atmak ve discord'a link bırakmak rolunuz ve gelecek #Airdrop hayırlı olsun.

![image](https://github.com/user-attachments/assets/367f9393-59d8-4a48-9c5f-87412a90d794)


