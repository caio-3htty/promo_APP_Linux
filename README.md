# Promo App Linux

Shell Electron dedicado ao Linux que carrega o `promo_APP_Web`.

## Stack
- Electron
- Build embutido do `../promo_APP_Web`

## Requisitos
- Node.js 20+
- npm 10+
- Ambiente Linux para empacotamento local (`AppImage` e `deb`)

Observacao de portabilidade:
- Em Windows, `electron-builder --linux` pode falhar por privilegio de symlink.
- O empacotamento oficial Linux deste app e feito no CI Ubuntu.

## Rodar local (desktop)
```bash
npm install
npm run desktop:dev
```

Por padrao os scripts procuram o repo web em `../promo_APP_Web`.
Se estiver em outro caminho, defina `PROMO_APP_WEB_DIR`.

## Gerar pacotes Linux
```bash
npm run desktop:build:linux
```

Se estiver em Windows e quiser apenas validar paridade web embutida:
```bash
npm run desktop:prepare:web
```

Artefatos em `release/`:
- `.AppImage`
- `.deb`

## Variaveis de ambiente
Build embutido do web usa as variaveis do `promo_APP_Web`:
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_PUBLISHABLE_KEY`

## GitHub Actions
- `linux-ci`: valida preparacao do bundle web embutido em Ubuntu.
- `linux-release`: gera `.AppImage` e `.deb` e publica artefatos.

## Code Hygiene
```bash
npm run cleanup:analyze
npm run cleanup:verify
```

Para validar empacotamento Linux final, execute `npm run desktop:build:linux` em runner Ubuntu.

# Promo_APP_Linux
