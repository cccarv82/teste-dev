criar arquivo .ignore:
ignore -n python node

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

verificação para commits:

docker run --rm --name="commitsar" -w /src -v "$(pwd)":/src aevea/commitsar commitsar .

instalando o lint de commit no repo:
npm init
npm install --save-dev @commitlint/{cli,config-conventional}

echo "export default { extends: ['@commitlint/config-conventional'] };" > commitlint.config.js

npm install --save-dev husky
npx husky init

# Add commit message linting to commit-msg hook

echo "npx --no -- commitlint --edit \$1" > .husky/commit-msg

adcionar no começo do package.json isso: "type": "module"

exemplo:
{
"type": "module",
"devDependencies": {
"@commitlint/cli": "^19.3.0",
"@commitlint/config-conventional": "^19.2.2",
"husky": "^9.0.11"
},
"scripts": {
"prepare": "husky"
}
}
