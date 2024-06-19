como gerar assinatura pra commits

verificar se existe chave criada:
gpg --list-secret-key --keyid-form LONG

criar chave
gpg --full-generate-key
RSA and RSA
4096
1y

após criar a chave:
gpg --armor --export IDDACHAVE

copiar todo o conteúdo mostrado e ir no github
settings -> SSH and GPG keys
new gpg key
colar o conteúdo e adicionar

no terminal:
git config --global user.name "Carlos Carvalho"
git config --global user.email "cccarv82@gmail.com"
git config --global user.signingkey IDDACHAVE
git config --global init.defaultBranch main

echo 'export GPG_TTY=$(tty)' >> ~/.bashrc

git config --global commit.gpgsign true
git config --global tag.gpgsign true

para verificar qual a assinatura do commit:
git log --show-signature -1

lint para commits:

npm install --save-dev @commitlint/{cli,config-conventional}
echo "export default { extends: ['@commitlint/config-conventional'] };" > commitlint.config.js

para a proxima parte, o repositorio git deve ter sido já criado
npm install --save-dev husky
npx husky init

# Add commit message linting to commit-msg hook

echo "npx --no -- commitlint --edit \$1" > .husky/commit-msg
