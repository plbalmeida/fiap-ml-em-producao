Para realizar o hands-on desse curso, é necessário o seguinte set up:

1) Ter uma IDE (Integrated Development Environment) instalada

Para instalar o VSCode no Linux com distribuição Ubuntu/Debian, executar:

```bash
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
sudo apt update
sudo apt install code
```

2) Ter o python instalado

Para a instalação no Linux com distribuição Ubuntu/Debian executar no terminal:

```bash
sudo apt update
sudo apt install python3
```

Após verificar a instalação, no terminal execute para checar a versão do python instalada:

```bash
python3 --version
```

3) Configuração de ambiente virtual


Primeiro crie o diretório do projeto e entre nele:

```bash
mkdir <NOME-DO-PROJETO>
cd <NOME-DO-PROJETO>/
```

Abra o VSCode:

```bash
code .
```

Para criar o ambiente virtual, vamos usar o venv:

```bash
python3 -m venv venv
source venv/bin/activate
```

Isso garante que as dependências dos projetos não conflitem entre si.

4) Ter arquivo de dependências

Criar o arquivo `requirements.txt`:

```bash
echo > requirements.txt
```

Colocar as seguintes bibliotecas do python no arquivo.

```txt
altair==5.3.0
ipeadatapy==0.1.9
matplotlib==3.9.0
numpy==1.26.0
pandas==2.2.2
plotly==5.22.0
python-dotenv==1.0.1
scikit-learn==1.5.1
streamlit==1.34.0
```

Execute o comando para instalar as bibliotecas no ambiente virtual criado:

```bash
pip install -r requirements.txt  
```

5) Notebook para fazer o case

Para fazer o case dessa parte do hands-on, crie um diretório e crie o notebook chamado `case.ipynb`:

```bash
mkdir notebooks
echo > case.ipynb
```

6) Ter o git instalado no sua máquina local

- [https://git-scm.com/](https://git-scm.com/)

- [https://www.alura.com.br/artigos/o-que-e-git-github#:~:text=Abra%20o%20Terminal%20e%20digite,instru%C3%A7%C3%B5es%20para%20instalar%20o%20Git.](https://www.alura.com.br/artigos/o-que-e-git-github#:~:text=Abra%20o%20Terminal%20e%20digite,instru%C3%A7%C3%B5es%20para%20instalar%20o%20Git.)

7) Ter conta no GitHub

- [https://git-scm.com/](https://git-scm.com/)

- [https://docs.github.com/pt/get-started/start-your-journey/creating-an-account-on-github](https://docs.github.com/pt/get-started/start-your-journey/creating-an-account-on-github)

8) Ter o Docker Desktop instalado

- [https://docs.docker.com/get-docker/](https://docs.docker.com/get-docker/)

9) Criar repo no GitHub

Iniciar o repositório localmente:

```bash
git init
```

dicione alguns arquivos ao seu repositório e faça um commit inicial:

```bash
echo "<NOME-DO-PROJETO>" >> README.md
git add README.md
git commit -m "First commit"
```

Criar arquivo `.gitignore` para não subir para o GitHub arquivos indesejáveis:

```bash 
echo .gitignore
```

Coloque o conteúdo nesse arquivo:

```
# ignora o diretório de ambiente virtual
venv/

# ignora todos os diretórios de __pycache__
**/__pycache__/

# ignora todos os arquivos .csv
*.csv
```

Para criar um repositório remoto no GitHub (supondo que você já tenha o GitHub CLI (gh) instalado):

```sh
gh repo create <NOME-DO-PROJETO> --public
```

Agora, adicione a URL do repositório remoto ao seu repositório local:

```sh
git remote add origin https://github.com/<SEU-USUARIO>/<NOME-DO-PROJETO>.git
```

Finalmente, envie seus commits locais para o repositório remoto:

```sh
git push -u origin master
```

Como boa prática de commits no git, vamos usar o Conventional Commits ([https://www.conventionalcommits.org/en/v1.0.0/](https://www.conventionalcommits.org/en/v1.0.0/)).

Conventional Commits é uma convenção simples para formatar mensagens de commit no Git, que fornece um conjunto de regras que facilitam a criação de um histórico de commits explícito e legível. As mensagens de commit no formato Conventional Commits seguem uma estrutura específica que inclui um tipo, um escopo opcional, e uma descrição.

Estrutura de um commit convencional:

```
<tipo>(<escopo opcional>): <DESCRIÇÃO>

[CORPO OPCIONAL]
[RODAPÉ OPCIONAL]
```

Tipos comuns:

- **feat**: Uma nova funcionalidade para o usuário.
- **fix**: Uma correção de bug.
- **docs**: Alterações na documentação.
- **style**: Alterações que não afetam o significado do código (espaços em branco, formatação, etc.).
- **refactor**: Uma alteração no código que não corrige um bug nem adiciona uma funcionalidade.
- **perf**: Uma mudança no código que melhora o desempenho.
- **test**: Adição de testes ausentes ou correção de testes existentes.
- **chore**: Alterações em tarefas de build, ferramentas auxiliares, dependências, etc.

Exemplo de commit

```bash
feat(src/main.py): inclusão de egenharia de features 
```

Benefícios:

1. **Histórico Claro**: Facilita a leitura e compreensão do histórico de commits.
2. **Automação**: Permite a automação de processos, como geração de changelogs e versionamento semântico.
3. **Comunicação**: Melhora a comunicação entre os membros da equipe ao fornecer uma descrição clara das mudanças.