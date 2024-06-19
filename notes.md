criar arquivo .ignore:
ignore -n python node

como gerar assinatura pra commits

iniciar o gpg-agent caso não esteja rodando:
gpgconf --launch gpg-agent

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

instalando ferramenta para commit:
npm install -g commitizen

novos comandos de repo:

iniciar repo:
git init
repoinit (commitizen init cz-conventional-changelog --save-dev --save-exact)
git add .
git cz
git push origin main
