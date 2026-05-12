# 🏆 Desafios Práticos: Manipulando Containers

Estes desafios foram criados para você testar seus conhecimentos técnicos sobre o ciclo de vida, conectividade e interatividade com containers Docker.

---

## 🛠️ Missão 1: O Arquiteto de Redes
**Conceitos:** `docker run`, `--name`, `-d`, `-p`.

1. Suba um container de **Nginx** chamado `servidor-desafio` em modo **detached**.
2. Mapeie a porta `80` do container para a porta **`9000`** do seu computador.
3. Acesse `http://localhost:9000` no navegador.
4. Pare o container usando o comando `stop`.
5. Inicie o mesmo container novamente usando `start` e verifique se o acesso voltou ao normal.

## 🔍 Missão 2: O Infiltrado
**Conceitos:** `docker exec`, `-it`, `bash`.

1. Com o container `servidor-desafio` rodando, acesse o shell interativo dele (`bash`).
2. Dentro dele, execute o comando `cat /etc/os-release` para descobrir qual distribuição Linux ele utiliza.
3. Saia do container (`exit`).
4. Agora, execute o comando `nginx -v` (para ver a versão do Nginx) dentro do container, mas **sem entrar nele** (usando `exec` direto do seu terminal).

## 🧹 Missão 3: O Faxineiro Digital
**Conceitos:** `--rm`, `docker ps -aq`, subcomandos.

1. Execute o comando `docker run hello-world` 5 vezes seguidas.
2. Use o subcomando `docker rm $(docker ps -aq)` para limpar todos os containers parados da sua máquina.
3. Agora, execute um container de `alpine` (uma imagem Linux super leve) usando a flag `--rm` para listar o conteúdo da raiz (`ls /`).
4. Verifique com `docker ps -a` se sobrou algum rastro desse container do Alpine.

## ⚠️ Missão 4: O Teste de Efemeridade
**Conceitos:** Persistência de estado e remoção.

1. Acesse o container `servidor-desafio` via bash.
2. Crie um arquivo de texto em `/tmp/segredo.txt` com o conteúdo "Docker é incrível!".
3. Saia e remova o container forçadamente (`docker rm -f servidor-desafio`).
4. Suba um novo container com o **mesmo nome** e **mesma imagem**.
5. Tente ler o arquivo `/tmp/segredo.txt`. 
   - *Spoiler: O arquivo sumiu. Isso prova que o container é efêmero!*

---
## 🚀 Bônus: "Dockerfile" de Estudos
Embora não tenhamos chegado em "Build", você pode criar seu próprio ambiente de testes. Salve o conteúdo abaixo como `Dockerfile` e rode `docker build -t meu-ambiente .` (veremos isso em detalhes no próximo capítulo!).

```dockerfile
FROM ubuntu:latest
RUN apt-get update && apt-get install -y curl vim
WORKDIR /app
CMD ["bash"]
```

---
*Boa sorte! Se travar em algum comando, consulte o [README.md](./readme.md) deste capítulo.*
