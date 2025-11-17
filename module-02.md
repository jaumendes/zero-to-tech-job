# Exercicios GitHub e Jenkins

## Objetivo
Criar uma conta no GitHub, enviar arquivos para um repositório e automatizar a publicação de um site simples usando GitHub Pages e Jenkins.

---

## 1. Criar conta no GitHub
1. Acesse **github.com**
2. Clique em **Sign up**
3. Preencha usuário, e-mail e senha
4. Confirme a conta

---

## 2. Criar um repositório para o site
1. Clique em **New Repository**
2. Nome: `meu-site`
3. Escolha **Public**
4. Marque **Add a README**
5. Clique em **Create Repository**

---

## 3. Criar um site simples
Crie um arquivo chamado `index.html` com o conteúdo:
```
<!DOCTYPE html>
<html>
<head>
<title>Meu Site</title>
</head>
<body>
<h1>Site publicado automaticamente!</h1>
</body>
</html>
```

---

## 4. Enviar o site para o GitHub via PowerShell
```
git clone https://github.com/SEU_USUARIO/meu-site.git
type index.html > meu-site/index.html
cd meu-site
git add .
git commit -m "Primeiro deploy"
git push
```

---

## 5. Ativar GitHub Pages
1. No GitHub, abra o repositório
2. Vá em **Settings** → **Pages**
3. Em **Source**, selecione **main** e **root**
4. Salve

O site ficará disponível em:
```
https://SEU_USUARIO.github.io/meu-site/
```

---

## 6. Automatizar deploy com Jenkins
### Criar o job
1. No Jenkins, clique **New Item**
2. Nome: `deploy-github`
3. Tipo: **Freestyle project**

### Configuração Git
Em **Source Code Management**, escolha:
```
https://github.com/SEU_USUARIO/meu-site.git
```

### Build Step
Adicionar um build step **Execute Windows batch command**:
```
echo <h1>Deploy automático %date% %time%</h1> > index.html
git add index.html
git commit -m "Deploy automático"
git push
```

---

## 7. Executar deploy
Clique em **Build Now**.
O Jenkins atualizará automaticamente o conteúdo do site publicado no GitHub Pages.

---
