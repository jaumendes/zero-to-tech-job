# Exercícios Iniciais do Workshop: Do Zero ao Primeiro Emprego Tech

## 1. Primeiro Contato com o PowerShell
### Objetivo
Aprender a abrir o terminal, rodar comandos essenciais e criar o primeiro script.

### Passos
1. Abra o PowerShell como administrador.
2. Comandos básicos:
```
pwd
ls
mkdir teste
cd teste
```
3. Criar arquivo:
```
New-Item hello.txt
```
4. Criar script:
```
echo "Olá, este é meu primeiro script!" > script.ps1
```
5. Executar:
```
./script.ps1
```

---

## 2. Primeiro Programa em Python
### Objetivo
Aprender a imprimir texto e ler entrada do usuário.

### Código (hello.py)
```
print("Olá! Bem-vindo ao seu primeiro programa Python.")
nome = input("Qual é o seu nome? ")
print("Prazer em te conhecer, " + nome + "!")
```

### Executar
```
python hello.py
```

---

## 3. Instalar Chocolatey
### Comando
```
Set-ExecutionPolicy Bypass -Scope Process -Force; \
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072; \
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

### Testar
```
choco --version
```

---

## 4. Instalar Python 3 via Chocolatey
```
choco install python -y
```
Testar:
```
python --version
```

---

## 5. Instalar Jenkins via Chocolatey
```
choco install jenkins -y
```

Verificar serviço:
```
Get-Service jenkins
```

Abrir no navegador:
```
http://localhost:8080
```

---

## 6. Criar Primeiro Job no Jenkins
1. Acessar Jenkins em `http://localhost:8080`
2. Clicar **New Item**
3. Nome do projeto: `job-inicial`
4. Selecionar **Freestyle project**
5. Em **Build Steps** → **Execute Windows batch command**
6. Inserir:
```
echo "Rodando meu primeiro job no Jenkins!"
python --version
```
7. Salvar e clicar **Build Now**
8. Abrir **Console Output** para ver o resultado

