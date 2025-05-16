# 🛡️ XSS Project – Vue.js Vulnerability Simulation

Este projeto foi criado com o intuito de demonstrar uma vulnerabilidade do tipo **XSS (Cross-Site Scripting)** em aplicações Vue.js 3, especificamente relacionada ao uso indevido da diretiva `v-html` em conjunto com a biblioteca de internacionalização **i18n**.

O objetivo é mostrar como falhas de segurança podem surgir com más práticas e como é possível corrigi-las de forma simples.

## 📁 Estrutura dos Componentes

- **`DialogVulnerability.vue`**  
  Componente vulnerável à XSS. Utiliza `v-html` diretamente com conteúdo vindo do i18n, sem validação/sanitização adequada.

- **`DialogFix.vue`**  
  Componente corrigido. Mostra como evitar a vulnerabilidade usando boas práticas.

📺 **Demonstração em vídeo**  
Para melhor entendimento das medidas tomadas, assista ao vídeo:  
[https://www.youtube.com/watch?v=nEsLGKc-RcA](https://www.youtube.com/watch?v=nEsLGKc-RcA)

---

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Lints and fixes files
```
npm run lint
```

