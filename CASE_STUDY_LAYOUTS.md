# 5 Opções de Layout para Case Studies

## Visão Geral

Criei 5 opções diferentes de apresentação para páginas de case study, cada uma otimizada para diferentes estilos de leitura e tipos de conteúdo. Todas atendem aos requisitos de:

✅ Fácil escaneabilidade  
✅ Navegação clara entre seções  
✅ Informações principais visíveis rapidamente  
✅ Foco em elementos visuais  
✅ Pular facilmente entre seções  
✅ Suporte para 8-12 seções  
✅ Design minimalista e impactante  
✅ Títulos que contam uma história  

---

## 1. Timeline Lateral ⏱️

### Quando Usar
- Projetos longos com muitas seções
- Quando você quer mostrar progresso linear
- Leitores que gostam de ver "onde estão" na história

### Características
- **Barra lateral fixa** com lista de seções
- Indicador visual da seção ativa
- Ideal para desktop (barra lateral oculta no mobile)
- Navegação por clique direto

### Vantagens
✓ Contexto constante de onde você está  
✓ Fácil pular para qualquer seção  
✓ Ótimo para projetos complexos  

### Desvantagens
✗ Ocupa espaço lateral no desktop  
✗ Menos eficaz em mobile  

---

## 2. Capítulos 📖

### Quando Usar
- Projetos que contam uma história sequencial
- Quando você quer controlar o ritmo de leitura
- Conteúdo denso que se beneficia de foco em uma seção por vez

### Características
- **Navegação estilo livro** (anterior/próximo)
- Grid de capítulos sempre visível
- Barra de progresso visual
- Transições suaves entre seções
- Uma seção por vez na tela

### Vantagens
✓ Reduz sobrecarga cognitiva  
✓ Ótimo para storytelling sequencial  
✓ Navegação intuitiva  

### Desvantagens
✗ Requer mais cliques para ver tudo  
✗ Não permite scroll contínuo  

---

## 3. Minimal Sticky 🎯

### Quando Usar
- Projetos com seções curtas e objetivas
- Quando você quer design mais clean
- Leitores que preferem scroll contínuo

### Características
- **Navegação sticky no topo** (fixa ao rolar)
- Scroll livre e contínuo
- Pills de navegação horizontais
- Máximo de conteúdo visível
- Layout centralizado

### Vantagens
✓ Design mais limpo e moderno  
✓ Scroll natural (UX familiar)  
✓ Ótimo para mobile  
✓ Maximiza espaço para conteúdo  

### Desvantagens
✗ Navegação pode ficar escondida se muitas seções  
✗ Menos contexto de "onde estou"  

---

## 4. Índice Lateral 📑

### Quando Usar
- Projetos acadêmicos ou técnicos
- Quando você quer referência constante
- Conteúdo que será consultado, não apenas lido

### Características
- **Sidebar fixa com índice completo**
- Metadados do projeto sempre visíveis
- Layout 2 colunas (índice + conteúdo)
- Indicador visual da seção ativa
- Ótimo para documentação

### Vantagens
✓ Referência constante ao projeto  
✓ Navegação ultra rápida  
✓ Ótimo para conteúdo técnico  
✓ Profissional e organizado  

### Desvantagens
✗ Menos espaço para conteúdo principal  
✗ Sidebar fixa ocupa espaço  

---

## 5. Flutuante ⚪

### Quando Usar
- Projetos visuais e imersivos
- Quando você quer minimizar distrações
- Portfolio de alto impacto visual

### Características
- **Dots de navegação flutuantes** (direita da tela)
- Design ultra minimalista
- Máximo foco no conteúdo
- Animações suaves ao scroll
- Tooltips ao hover nos dots

### Vantagens
✓ Máximo espaço para conteúdo visual  
✓ Design sofisticado e moderno  
✓ Mínima distração  
✓ Ótimo para storytelling visual  

### Desvantagens
✗ Navegação menos óbvia para usuários novos  
✗ Dots podem passar despercebidos  
✗ Apenas visível em desktop  

---

## Como Implementar

### Uso Básico

```tsx
import { CaseStudyLayoutSwitcher } from "./components/CaseStudyLayoutSwitcher";

const projectData = {
  title: "Nome do Projeto",
  tags: ["Tag 1", "Tag 2", "Tag 3"],
  role: "Seu papel no projeto",
  industry: "Indústria/Setor",
  sections: [
    {
      number: "01",
      title: "Título que Conta História",
      content: <div>Conteúdo em JSX</div>
    },
    // ... mais seções
  ]
};

<CaseStudyLayoutSwitcher projectData={projectData} />
```

### Estrutura de Seções

Cada seção deve ter:
- **number**: String com numeração (ex: "01", "02")
- **title**: Título que conta história, não genérico
- **content**: JSX com o conteúdo completo

### Títulos que Contam História ✅

❌ **Evite títulos genéricos:**
- "Pesquisa"
- "Wireframes"
- "Design Visual"
- "Resultados"

✅ **Use títulos narrativos:**
- "Do Caos à Consistência: O Desafio Invisível"
- "Ouvindo as Dores Reais do Time"
- "Construindo um Sistema de Verdade, Não Policiamento"
- "Resultados que Ninguém Esperava (Mas Todos Mereciam)"

---

## Recomendações por Tipo de Projeto

| Tipo de Projeto | Layout Recomendado |
|-----------------|-------------------|
| Design System / Processos | **Timeline** ou **Índice** |
| Produto Digital | **Minimal** ou **Capítulos** |
| Redesign/Visual | **Flutuante** ou **Minimal** |
| Case Técnico | **Índice** ou **Timeline** |
| Storytelling | **Capítulos** ou **Flutuante** |

---

## Personalização

Todos os layouts suportam:
- Cards customizados
- Imagens e vídeos
- Citações e depoimentos
- Métricas e resultados
- Grids e tabelas
- Animações Motion/Framer

---

## Acessibilidade

Todos os layouts incluem:
✓ Navegação por teclado  
✓ Scroll suave para reduzir motion sickness  
✓ Contraste adequado  
✓ Indicadores visuais claros  
✓ Responsividade mobile  

---

## Próximos Passos

1. **Teste cada layout** com seu conteúdo real
2. **Peça feedback** de colegas sobre qual é mais claro
3. **Considere o público**: stakeholders técnicos preferem Índice, criativos preferem Flutuante
4. **Mantenha consistência** entre projetos do mesmo tipo

---

**Criado por:** Product Designer com 15+ anos de experiência  
**Data:** Janeiro 2026  
**Versão:** 1.0
