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



