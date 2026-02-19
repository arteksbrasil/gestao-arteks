# 🔗 Guia de Integração com GitHub

Este guia mostra como integrar o Sistema Arteks ao seu repositório GitHub existente.

## 📂 Repositório Existente

Você já tem: `https://github.com/arteksbrasil/gestao-arteks`

## 🚀 Opções de Integração

### Opção 1: Substituir o index.html Atual

Se você quer substituir completamente o sistema existente:

```bash
# 1. Clone seu repositório
git clone https://github.com/arteksbrasil/gestao-arteks.git
cd gestao-arteks

# 2. Faça backup do index.html atual
mv index.html index_backup.html

# 3. Copie os novos arquivos
# (Copie todos os arquivos do sistema-web-arteks para a pasta)

# 4. Commit e push
git add .
git commit -m "feat: Sistema completo de gestão de impressão 3D"
git push origin main
```

### Opção 2: Manter Ambas as Versões

Se você quer manter o sistema antigo e adicionar o novo:

```bash
# 1. Clone seu repositório
git clone https://github.com/arteksbrasil/gestao-arteks.git
cd gestao-arteks

# 2. Renomeie o index.html atual
mv index.html sistema-simples.html

# 3. Copie os novos arquivos
# (Copie todos os arquivos do sistema-web-arteks)

# 4. Crie página de escolha
cat > index.html << 'EOF'
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Arteks - Escolha o Sistema</title>
    <style>
        * { margin: 0; padding: 0; box-sizing: border-box; }
        body {
            font-family: 'Segoe UI', Arial, sans-serif;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            min-height: 100vh;
            display: flex;
            align-items: center;
            justify-content: center;
            padding: 20px;
        }
        .container {
            max-width: 900px;
            width: 100%;
        }
        h1 {
            text-align: center;
            color: white;
            font-size: 48px;
            margin-bottom: 20px;
        }
        p {
            text-align: center;
            color: rgba(255,255,255,0.9);
            font-size: 18px;
            margin-bottom: 50px;
        }
        .cards {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 30px;
        }
        .card {
            background: white;
            border-radius: 20px;
            padding: 40px;
            text-align: center;
            box-shadow: 0 10px 40px rgba(0,0,0,0.2);
            transition: all 0.3s ease;
            cursor: pointer;
        }
        .card:hover {
            transform: translateY(-10px);
            box-shadow: 0 20px 60px rgba(0,0,0,0.3);
        }
        .icon {
            font-size: 60px;
            margin-bottom: 20px;
        }
        .card h2 {
            color: #1e3a8a;
            font-size: 24px;
            margin-bottom: 15px;
        }
        .card p {
            color: #6b7280;
            font-size: 14px;
            line-height: 1.6;
            margin-bottom: 25px;
        }
        .btn {
            display: inline-block;
            padding: 12px 30px;
            background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
            color: white;
            text-decoration: none;
            border-radius: 25px;
            font-weight: 600;
            transition: all 0.3s ease;
        }
        .btn:hover {
            transform: scale(1.05);
            box-shadow: 0 5px 20px rgba(102, 126, 234, 0.4);
        }
    </style>
</head>
<body>
    <div class="container">
        <h1>🎯 Arteks Gestão</h1>
        <p>Escolha a versão do sistema que deseja usar</p>
        
        <div class="cards">
            <div class="card" onclick="window.location.href='sistema-completo.html'">
                <div class="icon">🚀</div>
                <h2>Sistema Completo</h2>
                <p>Sistema avançado com calculadora, estoque, vendas, relatórios e muito mais. Ideal para operações profissionais.</p>
                <a href="sistema-completo.html" class="btn">Acessar Sistema Completo</a>
            </div>
            
            <div class="card" onclick="window.location.href='sistema-simples.html'">
                <div class="icon">⚡</div>
                <h2>Sistema Simples</h2>
                <p>Versão simplificada e rápida. Ideal para começar ou operações menores.</p>
                <a href="sistema-simples.html" class="btn">Acessar Sistema Simples</a>
            </div>
        </div>
    </div>
</body>
</html>
EOF

# 5. Renomeie o novo index.html
mv index.html sistema-completo.html
# Volte a criar o index de escolha acima

# 6. Commit
git add .
git commit -m "feat: Adicionar sistema completo + página de escolha"
git push origin main
```

### Opção 3: Usar Branch Separada

Para testar antes de publicar:

```bash
# 1. Clone seu repositório
git clone https://github.com/arteksbrasil/gestao-arteks.git
cd gestao-arteks

# 2. Crie nova branch
git checkout -b sistema-completo

# 3. Copie todos os arquivos do sistema-web-arteks

# 4. Commit
git add .
git commit -m "feat: Sistema completo de gestão"
git push origin sistema-completo

# 5. Depois de testar, faça merge na main
git checkout main
git merge sistema-completo
git push origin main
```

## 🌐 Ativar GitHub Pages

Depois de fazer push dos arquivos:

1. Vá em `https://github.com/arteksbrasil/gestao-arteks/settings/pages`
2. Em **Source**, selecione:
   - Branch: `main`
   - Folder: `/root`
3. Clique em **Save**
4. Aguarde alguns minutos
5. Seu site estará em: `https://arteksbrasil.github.io/gestao-arteks/`

## 📱 Domínio Customizado (Opcional)

Se você tem um domínio próprio:

1. No seu provedor de domínio, crie um registro CNAME:
   ```
   www.seudominio.com.br -> arteksbrasil.github.io
   ```

2. No GitHub Pages settings, adicione:
   - Custom domain: `www.seudominio.com.br`
   - ✅ Enforce HTTPS

3. Seu site estará em: `https://www.seudominio.com.br`

## 🔄 Atualizar o Sistema

Para atualizar o sistema no futuro:

```bash
# 1. Entre na pasta do repositório
cd gestao-arteks

# 2. Faça as alterações necessárias nos arquivos

# 3. Commit e push
git add .
git commit -m "update: Descrição da atualização"
git push origin main

# 4. GitHub Pages atualiza automaticamente em ~5 minutos
```

## 📁 Estrutura Recomendada Final

```
gestao-arteks/
├── index.html              # Página principal (ou de escolha)
├── sistema-completo.html   # Sistema completo (opcional)
├── sistema-simples.html    # Sistema antigo (opcional)
├── css/
│   └── styles.css
├── js/
│   ├── app.js
│   ├── calculadora.js
│   ├── produtos.js
│   ├── estoque.js
│   ├── vendas.js
│   ├── relatorios.js
│   └── configuracoes.js
├── assets/                 # Imagens, logos, etc
├── README.md
└── LICENSE
```

## ✅ Checklist Pós-Deploy

- [ ] Testar todos os links
- [ ] Verificar se os gráficos carregam
- [ ] Testar em mobile
- [ ] Verificar se as fórmulas calculam corretamente
- [ ] Testar exportação de dados
- [ ] Verificar se o LocalStorage funciona
- [ ] Testar em diferentes navegadores

## 🐛 Troubleshooting

**Página não carrega:**
- Verifique se o GitHub Pages está ativado
- Aguarde 5-10 minutos após o push
- Limpe o cache do navegador

**CSS/JS não carregam:**
- Verifique os caminhos dos arquivos
- Confirme que as pastas css/ e js/ existem
- Veja o console do navegador (F12) para erros

**LocalStorage não funciona:**
- Verifique se está usando HTTPS
- Confirme que cookies estão habilitados
- Teste em modo anônimo

## 📞 Suporte

Se precisar de ajuda:
- Abra uma issue: https://github.com/arteksbrasil/gestao-arteks/issues
- Email: contato@arteks.com.br

---

**Boa sorte com seu sistema! 🚀**
