# Capítulo: Manipulando Containers

Este capítulo aborda os comandos fundamentais para criação, execução, gerenciamento e inspeção de containers Docker.

---

## 📋 Sumário
1. [Executando o Primeiro Container](#1-executando-o-primeiro-container)
2. [Configurações de Execução (Nomes, Background e Portas)](#2-configurações-de-execução)
3. [Ciclo de Vida do Container (Stop, Start, Remove)](#3-ciclo-de-vida-do-container)
4. [Attach e Detach](#4-attach-e-detach)
5. [Execução de Comandos e Auto-remoção](#5-execução-de-comandos-e-auto-remoção)
6. [Remoção em Massa](#6-remoção-em-massa)
7. [Publicação de Portas e Acesso Externo](#7-publicação-de-portas-e-acesso-externo)
8. [Execução Interativa e Shell Access](#8-execução-interativa-e-shell-access)
9. [Resumo de Comandos](#-resumo-de-comandos)

---

## 1. Executando o Primeiro Container
Para validar a instalação e o funcionamento básico:
```bash
docker run hello-world
```
*Baixa a imagem (se necessário), cria o container, exibe a mensagem e encerra.*

## 2. Configurações de Execução

### Nomeando Containers
```bash
docker run --name meu-nginx nginx
```

### Modo Detached (Segundo Plano)
```bash
docker run -d nginx
```

### Mapeamento de Portas
```bash
docker run -p 8080:80 nginx
```

## 3. Ciclo de Vida do Container

| Ação | Comando |
| :--- | :--- |
| **Parar** | `docker stop <nome_ou_id>` |
| **Iniciar** | `docker start <nome_ou_id>` |
| **Remover** | `docker rm <nome_ou_id>` |
| **Remover Forçado** | `docker rm -f <nome_ou_id>` |

## 4. Attach e Detach

- **Anexar Terminal:** `docker attach <nome>` (conecta ao processo principal).
- **Sair sem Parar:** Pressione `CTRL + P` seguido de `CTRL + Q`.

## 5. Execução de Comandos e Auto-remoção

### Executar Comando e Sair
```bash
docker run nginx ls -la
```

### Diferença entre Run e Exec
- **docker run:** Cria um **novo** container.
- **docker exec:** Roda um comando em um container **já existente**.

### Auto-remoção (--rm)
Remove o container automaticamente após ele ser encerrado:
```bash
docker run --rm nginx ls -la
```

## 6. Remoção em Massa
Utilizando subcomandos para limpar o ambiente:

```bash
# Remover todos os containers parados
docker rm $(docker ps -aq)

# Remover todos (incluindo os ativos)
docker rm -f $(docker ps -aq)
```

## 7. Publicação de Portas e Acesso Externo
A regra é sempre `HOST : CONTAINER`.
```bash
docker run -d -p 8080:80 nginx
```
Acesso em: `http://localhost:8080`

## 8. Execução Interativa e Shell Access
Para "entrar" no container e usar o terminal:

```bash
# Em um container novo
docker run -it nginx bash

# Em um container já rodando
docker exec -it mynginx bash
```

---

## 🚀 Resumo de Comandos

| Comando | Descrição |
| :--- | :--- |
| `docker ps` | Lista containers ativos |
| `docker ps -a` | Lista todos os containers (ativos e parados) |
| `docker run -d -p 80:80 --name n1 nginx` | Exemplo completo de criação |
| `docker exec -it n1 bash` | Acessa o shell do container |
| `docker logs n1` | Visualiza os logs do container |
| `docker inspect n1` | Detalhes técnicos do container |

---