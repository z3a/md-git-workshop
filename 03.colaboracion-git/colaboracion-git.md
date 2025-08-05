---
marp: true
theme: uncover
class: invert
paginate: false
---

# Colaboración en Git

---

<style scoped>section{font-size:25px;}</style>

# Repaso

* ``git init``: Crea un repo
* ``git status``: Revisa el estado del repo
* ``git add``: Agrega cambios al ``staging area``
* ``git commit -m 'mensaje'``: Registra cambios en el historial
* ``git checkout [commit id] [archivo]``: Regresa el archivo a un estado anterior
* ``git branch [nombre]``: Crea una nueva rama
* ``git checkout [nombre]``: Cambiamos a la rama
* ``git merge [nombre]``: Une cambios de la rama especificada en la actual

---

# Git es un sistema distribuido

Permite tener múltiples copias sincronizadas

---
# Github

Servicio de alojamiento de repositorios

1. Crear una cuenta
2. Configurar llaves de acceso ``ssh``

---
<style scoped>section{font-size:30px;}</style>

# Crear llaves ``ssh``

[Guía para crear una nueva llave](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent)

``ssh-keygen -t ed25519 -C "your_email@example.com"``

---
<style scoped>section{font-size:30px;}</style>

# Agregar la llave a nuestra cuenta

``pbcopy < ~/.ssh/id_ed25519.pub``
o
``cat ~/.ssh/id_ed25519.pub``

---
<style scoped>section{font-size:30px;}</style>

# En Github

1. Ir a los ``settings`` de la cuenta
2. Entrar a ``SSH and GPG keys``
3. Click en ``Add SSH key``
4. En el campo ``Title`` agregar un identificador de la llave ej ``mi compu``
5. En el campo ``Key`` pegar el contenido de la llave pública
6. Click en ``Add SSH Key``

---
<style scoped>section{font-size:25px;}</style>

![bg right:60% fit](./img/github-newrepo.png)
crear un nuevo repo

---

<style scoped>section{font-size:25px;}</style>

![bg right:60% fit](./img/github-newrepo-2.png)
El nuevo repo vacío

---

<style scoped>section{font-size:25px;}</style>

![bg right:50% fit](./img/vscode-sign-in.png)
Sign in con ``github`` en VS Code

---
<style scoped>section{font-size:25px;}</style>

# Conectar nuestro repo local con Github en 4 pasos

``git remote add origin git@github.com:z3a/md-git-workshop.git``

---

<style scoped>section{font-size:25px;}</style>

![bg right:50% fit](./img/add-remote-1.png)
1. **Add remote**

---

<style scoped>section{font-size:25px;}</style>

![bg right:50% fit](./img/add-remote-2.png)
2. **Click en Add remote from Github**

---

<style scoped>section{font-size:25px;}</style>

![bg right:50% fit](./img/add-remote-3.png)
3. **Seleccionar de la lista el repo**

---

<style scoped>section{font-size:25px;}</style>

![bg right:50% fit](./img/add-remote-4.png)
4. **Dar un nombre a la conexión remota**

---

```
[remote "github"]
        url = https://github.com/z3a/md-git-workshop.git
        fetch = +refs/heads/*:refs/remotes/github/*
```
Cambios en la configuración de nuestra copia local

---

<style scoped>section{font-size:25px;}</style>

![bg right:50% fit](./img/git-push.png)
**Sincronizar con Github**

---

<style scoped>section{font-size:25px;}</style>

![bg right:60% fit](./img/github-after-push.png)
El repo en GH actualizado

---

# Flujo de trabajo

1. Hacer cambios
2. ``git add`` + ``git commit``
3. ``git push``

---

<style scoped>section{font-size:25px;}</style>

![bg right:50% fit](./img/push-to-gh.png)
``git push``
Sincronizar los cambios con GH

---

# Clonar un repo

Clonar (*clone*) un repositorio es tener hacer una copia idéntica en otro lugar

``git clone [repo-inicial] [ubicación-copia]``

---
<style scoped>section{font-size:25px;}</style>

Hacer una copia local

![bg right:40% fit](./img/git-clone.png)

``git clone md-git-workshop nueva-copia``

---

# Remote

Define una conexión con un repo remoto

```
[remote "origin"]
        url = /Users/zea/iCloud/Documents/2025/md-git-workshop
        fetch = +refs/heads/*:refs/remotes/origin/*
[branch "main"]
        remote = origin
        merge = refs/heads/main
```
---

# Flujo de trabajo con repo remoto

1. ``git clone``: obtenemos la copia de trabajo
2. Hacemos cambios
3. ``git add`` + ``git commit``
4. ``git push``: *subimos* nuestros cambios al repositorio
5. ``git pull``: sincronizamos nuestra copia de trabajo
6. Repetimos 2-5