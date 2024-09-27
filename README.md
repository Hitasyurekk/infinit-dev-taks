# infinit-dev-taks

# TR Rehber

**Hali hazırda boş bir vps varsa üzerinde çalışabilirsiniz. Tavsiyem workspace kullanmanız ücretsiz ve işinizi görecektir.**

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
