# Programação - Semana 2 - Módulo 10
## Relatório: Deploying backstage on docker

### Aluna: Livia Coutinho

</br>

# Resumo da tecnologia:
O Backstage é uma plataforma de desenvolvimento de software de código aberto criada pela Spotify. </br>
Essa plataforna oferece uma maneira unificada de visualizar, gerenciar e colaborar em todos os aspectos do ciclo de vida do desenvolvimento de software. </br>
Com o Backstage, as equipes podem criar seus próprios aplicativos personalizados para fornecer uma visão holística de seus projetos, incluindo informações sobre serviços, documentação, integrações, pipelines de CI/CD etc.

# Conceitos aprendidos:

**1. Instalação de um servidor independente:**
- Como configurar um ambiente de desenvolvimento local do Backstage usando o comando npx @backstage/create-app@latest.
- Os pré-requisitos incluem sistemas operacionais baseados em Linux, comandos de terminal e a instalação de ferramentas como Node.js, Yarn, Docker e Git, que eu já tinha.
- O Backstage é instalado em um diretório local com uma estrutura de pasta específica, que vai conter arquivos de configuração principais, informações de catálogo e diretórios tanto para front quanto para back.

**2. Execução do app Backstage:**

- Considerando feita a instalação, o aplicativo Backstage pode ser iniciado (comando yarn dev).
- O frontend e o backend são executados como processos separados, e quando o frontend for compilado com sucesso, o navegador vai automaticamente abrir a interface do Backstage em http://localhost:3000.

**3. Construção de imagem Docker:**
- COnstrução da imagem Docker para o Backstage, que vai poder contar com dois métodos de construção: uma abordagem de build no host e uma build de vários estágios.
- Ambos os métodos vão envolver a instalação de dependências, a compilação do código e a configuração do ambiente para servir o aplicativo Backstage.
- A construção da imagem Docker pode ser feita em um único contêiner ou em vários estágios (essa escolha vai variar de acordo as necessidades do usuário).

## Próximos passos:
O tutorial fornece informações sobre os próximos passos, dependendo do papel do usuário, seja administrador ou desenvolvedor. Para administradores, os próximos passos incluem explorar a seção de administração, enquanto para os desenvolvedores, é sugerido explorar a seção de desenvolvimento.

# Passo a passo

### Instalando o backstage:

- 1.  Rodar o comando npx @backstage/create-app@latest --skip-install
![alt text](image.png)

- 2. Atribuir um nome para a aplicação
![alt text](image-1.png)

- 3. Navegar até a pasta e rodar o yarn install
![alt text](image-2.png)

- 4. Corrigir o yarn (npm install --global yarn)
![alt text](image-4.png)

- 5. yarn install novamente
![alt text](image-5.png)

## Preparação do build do backstage:

- 1. **Rodar o comando yarn install --frozen-lockfile**
![alt text](image-6.png)

- 2. **Preparação dos types com o comando yarn tsc**
![alt text](image-7.png)

- 3. **Rodar o comando yarn build:backend**
![alt text](image-8.png)
O erro está ocorrendo porque o ambiente em que o comando está sendo executado tem uma versão do Node.js que não é compatível com as especificações do projeto. 
O projeto espera uma versão do Node.js que seja 18 ou 20, mas a versão atual do Node.js instalada no ambiente é 21.7.1.

- 4. **Para gerenciar o erro acima, precisarei usar o NVM**
![alt text](image-9.png)
![alt text](image-10.png)
-- Rodar novamente o yarn install
![alt text](image-11.png)
-- Erros de conexão. Trocar a rede wi-fi.
![alt text](image-12.png)
-- Rede wi-fi trocada. Yarn install novamente.
![alt text](image-13.png)
-- Rodar novamente o yarn install --frozen-lockfile
-- Rodar novamente o yarn tsc
![alt text](image-14.png)
Para resolver o erro acima:
-- npm install -g typescript
-- yarn global add typescript
![alt text](image-15.png)
-- Rodar novamente o yarn tsc
-- Rodar o yarn build:backend

## Ajustes do dockerfile do backstage
- Abrir o liviasemana2\packages\backend\Dockerfile
- Substituir esse código pelo o que o Saadi enviou no grupo
![alt text](image-16.png)
![alt text](image-17.png)
- docker image build . -f packages/backend/Dockerfile --tag backstage --no-cache
![alt text](image-18.png)
![alt text](image-19.png)
- docker run -it -p 7007:7007 backstage
#### - http://localhost:7007/