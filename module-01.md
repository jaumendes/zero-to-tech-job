# Exercícios Iniciais 

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
'echo "Olá, este é meu primeiro script!"' > script.ps1
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

## 5. Instalar Java (Obrigatório para Jenkins)

O Jenkins requer Java para funcionar. Vamos instalar o Temurin OpenJDK 17, versão recomendada.

Instalar Java 17
```
choco install temurin17 -y
```
Testar:
```
java -version
```

## 5.1. Corrigir Erro de JAVA_HOME ao Instalar o Jenkins

Se durante a instalação do Jenkins via Chocolatey aparecer o erro:

```
JAVA_HOME is not set and no 'java' command could be found in your PATH
```

significa que o Java está instalado, mas a variável de ambiente **JAVA_HOME** não foi configurada.

### ✔️ Verificar Java Instalado
```
java -version
```

### ✔️ Verificar onde o Java está instalado
Normalmente em:
```
C:\Program Files\Eclipse Adoptium\jdk-17*
```
ou  
```
C:\Program Files\Java\jdk1.8*
```

### ✔️ Definir JAVA_HOME (PowerShell como administrador)
```
setx JAVA_HOME "C:\Program Files\Eclipse Adoptium\jdk-17" /M
```

### ✔️ Adicionar o bin ao PATH
```
setx PATH "$env:PATH;$env:JAVA_HOME\bin" /M
```

### ✔️ Testar
```
echo $env:JAVA_HOME
java -version
```

Agora você pode instalar o Jenkins normalmente:

```
choco install jenkins -y
```


## 6. Instalar Jenkins via Chocolatey
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

## 7. Criar Primeiro Job no Jenkins
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
8. Salvar e clicar **Build Now**
9. Abrir **Console Output** para ver o resultado

