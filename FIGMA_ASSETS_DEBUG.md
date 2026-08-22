# 🔍 Diagnóstico e Solução: Imagens não aparecem

## 🚨 Problema Identificado

As imagens com o esquema `figma:asset/` não estavam sendo carregadas no aplicativo.

### Causa Raiz

1. **Falta de Plugin Vite**: O Vite não tinha configuração para processar o esquema virtual `figma:asset`
2. **Sem Declaração de Tipos**: TypeScript não reconhecia imports com `figma:asset/*`
3. **Falta de Debug**: Não havia logs para identificar erros de carregamento
4. **Sem Feedback Visual**: Usuário não via se a imagem estava carregando ou com erro

## ✅ Soluções Implementadas

### 1. Plugin Vite para Figma Assets (`/vite-figma-assets-plugin.ts`)

```typescript
// Intercepta imports com figma:asset e converte para URLs
export function figmaAssetsPlugin(): Plugin {
  return {
    name: 'vite-plugin-figma-assets',
    enforce: 'pre',
    resolveId(id: string) {
      if (id.startsWith('figma:asset/')) return id;
    },
    load(id: string) {
      if (id.startsWith('figma:asset/')) {
        const assetHash = id.replace('figma:asset/', '');
        const assetUrl = `/figma-assets/${assetHash}`;
        return `export default "${assetUrl}";`;
      }
    }
  };
}
```

**Benefícios:**
- ✅ Processa imports `figma:asset/` corretamente
- ✅ Converte hashes em URLs utilizáveis
- ✅ Logs detalhados no console
- ✅ Compatível com hot reload

### 2. Declaração de Tipos (`/src/vite-env.d.ts`)

```typescript
declare module 'figma:asset/*' {
  const src: string;
  export default src;
}
```

**Benefícios:**
- ✅ TypeScript reconhece imports figma:asset
- ✅ Autocomplete funciona
- ✅ Sem erros de tipo

### 3. ImageWithFallback Aprimorado

**Melhorias:**
- ✅ **Loading State**: Mostra "Loading..." enquanto carrega
- ✅ **Error Handling**: Exibe mensagem clara em caso de erro
- ✅ **Debug Logs**: Console logs detalhados
- ✅ **Informações de Erro**: Mostra URL que falhou

```typescript
// Logs automáticos:
console.log('[ImageWithFallback] Image src:', props.src)
console.error('[ImageWithFallback] Failed to load image:', {...})
console.log('[ImageWithFallback] Image loaded successfully:', props.src)
```

### 4. Vite Config Atualizado

```typescript
import { figmaAssetsPlugin } from './vite-figma-assets-plugin'

export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
    figmaAssetsPlugin(), // ← Novo plugin
  ],
})
```

## 🧪 Como Testar

### 1. Verificar Console do Browser

Abra o DevTools (F12) e procure por:

```
[ImageWithFallback] Image src: figma:asset/000b6d05dd55266fbc6ff183e80a3d34af152e22.png
[Figma Assets Plugin] Loading asset: { id: ..., assetHash: ..., assetUrl: ... }
```

### 2. Verificar Network Tab

- Abra a aba Network (Rede) no DevTools
- Procure por requisições para `/figma-assets/`
- Status 200 = sucesso ✅
- Status 404 = asset não encontrado ❌

### 3. Verificar Elemento HTML

Inspecione a tag `<img>` e verifique:
- `src` deve começar com `/figma-assets/`
- Se mostrar placeholder cinza = erro de carregamento

## 🔧 Troubleshooting

### Imagem ainda não carrega?

**Causa Possível**: O asset não foi processado pelo sistema Figma Make

**Solução**:
1. Verifique se o arquivo foi anexado corretamente
2. Aguarde processamento do sistema
3. Verifique hash correto no console

### Erro 404 no Network?

**Causa Possível**: Backend Figma Make não está servindo o asset

**Solução**:
- O hash pode estar incorreto
- O asset pode não ter sido uploadado
- Verificar com time Figma Make

### TypeScript reclama do import?

**Solução**: Reinicie o TypeScript Server
- VSCode: Cmd/Ctrl + Shift + P → "TypeScript: Restart TS Server"

## 📊 Imagens Usadas no Projeto

| Arquivo | Hash | Localização |
|---------|------|-------------|
| Onboarding Hero | `000b6d05dd55266fbc6ff183e80a3d34af152e22.png` | OnboardingCase - Hero |
| Jira Board | `33884e873f635e0ec79b0acca371d761bea4e09d.png` | OnboardingCase - Tarefas |
| Cocriação | `1b33d906f8bb4f1128e79616c3ba4a78fdaeeda5.png` | OnboardingCase - Discovery |
| Confluence | `91f5ee9b236b31c1e077424c82eb8eef320b1621.png` | OnboardingCase - Documentação |
| Spreadsheet | `fda71ffcb44d9a23eba85d0fcf5f5ad45fc4be19.png` | OnboardingCase - Problemas |

## 🎯 Próximos Passos

Se as imagens ainda não aparecerem:

1. **Verificar Backend Figma Make**
   - Os assets precisam ser servidos em `/figma-assets/:hash`
   - Pode ser necessário configuração adicional

2. **Alternativa: Assets Estáticos**
   - Criar pasta `/public/assets/`
   - Mover imagens para lá
   - Usar URLs relativas: `/assets/image.png`

3. **Contatar Suporte Figma Make**
   - Se o problema persistir, pode ser limitação do sistema
