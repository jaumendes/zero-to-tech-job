# module-04.md

## Módulo 4 — Projeto Realista (Parte 2)

### Objetivo
Completar um pipeline real: build → deploy automático → notificação no Slack.

---

## 💡 O que vais aprender
- Criar um processo de deploy
- Usar ações pós-build do Jenkins
- Integrar Slack com Jenkins usando webhooks
- Entender notificações de sucesso e falha

---

## 📌 1. Adicionar Deploy Automático
No job do Jenkins:
1. Abre o job `projeto-realista-ci`
2. Vai a **Post-build Actions**
3. Adiciona um passo (ex.: *Execute Shell*) com um script simples:

```bash
#!/bin/bash
# Exemplo de deploy simples para uma pasta pública
cp -r * /var/www/html/projeto-realista/
```

Se preferires usar GitHub Pages:
```bash
git checkout gh-pages
cp -r * .
git add .
git commit -m "deploy automático"
git push origin gh-pages
```

---

## 📌 2. Criar Webhook no Slack
1. No Slack → *Manage Apps*
2. Procura **Incoming Webhooks**
3. Clica **Add New Webhook to Workspace**
4. Escolhe o canal (ex.: `#ci-cd`)
5. Copia a URL do webhook

---

## 📌 3. Adicionar Notificação no Jenkins
No job → **Post-build Actions** → *Execute Shell* (ou dentro do Jenkinsfile, se estiveres a usar Pipeline).

### Notificação em caso de sucesso:
```bash
curl -X POST -H 'Content-type: application/json' --data "{
  \"text\": \"Deploy realizado com sucesso! Build: ${BUILD_NUMBER}\"
}" <URL_DO_WEBHOOK_SLACK>
```

### Notificação em caso de falha:
Usa a secção de *Post-build* específica para falhas ou um bloco `post { failure {}}` em Jenkinsfile.

```bash
curl -X POST -H 'Content-type: application/json' --data "{
  \"text\": \"🚨 Deploy falhou! Build: ${BUILD_NUMBER}\"
}" <URL_DO_WEBHOOK_SLACK>
```

---

## 📌 4. Testar Tudo
1. Faz commit e push para uma branch
2. Jenkins deve:
   - Receber webhook
   - Fazer build
   - Executar deploy
   - Enviar notificação para Slack
3. Induz uma falha (linha inválida num script) e repete o teste

---

## 🎯 Resultado Final do Módulo 4
- Pipeline completo: CI + Deploy + Notificação
- Entendimento claro do fluxo DevOps
- Projeto realista pronto para portfólio

