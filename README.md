# A Cidade Submersa — Next.js + Supabase

Protótipo funcional da proposta visual: cidade submersa, estética azul-clara/clean, jornada linear por regiões e áreas separadas de aluno/professor.

## Funcionalidades
- Landing page narrativa.
- Cadastro/login de aluno e professor.
- Código de acesso para cadastro de professor.
- Jornada sequencial: Porto → Corredores → Biblioteca → Torre → Câmara Central.
- Mapa visual com regiões bloqueadas/liberadas.
- Desafios de geometria, tentativas e validação.
- Progresso percentual.
- Câmara Central como etapa final.
- Resultado e histórico.
- Artefatos e inventário.
- Recursos de apoio/fórmulas.
- Painel do professor com alunos, acertos, tentativas e pontos.
- Perfil de desempenho individual.
- Cadastro de regiões, desafios e artefatos pelo professor.
- RLS no Supabase.

## Instalação

```bash
npm install
cp .env.example .env.local
npm run dev
```

Preencha `.env.local` com a URL e a Publishable Key do Supabase.

## Banco
No Supabase, SQL Editor → cole `supabase/schema.sql` → Run.

## Professor
Defina `TEACHER_ACCESS_CODE` no `.env.local` e também na Vercel. O aluno não precisa desse código.

## Deploy
Envie o projeto para GitHub e importe na Vercel. Cadastre `NEXT_PUBLIC_SUPABASE_URL`, `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY` e `TEACHER_ACCESS_CODE` nas Environment Variables.

> Para produção escolar real, recomendo transformar o cadastro de professor em aprovação/invite, em vez de liberar qualquer pessoa que tenha o código.

## Correções da versão atual

- O alias `@/*` está configurado no `tsconfig.json` para apontar para a raiz do projeto.
- `@/components/Topbar` resolve para `components/Topbar.tsx`.
- O projeto usa `NEXT_PUBLIC_SUPABASE_URL` e `NEXT_PUBLIC_SUPABASE_PUBLISHABLE_KEY`.
- O `proxy.ts` usa export default compatível com Next.js 16.
- O schema inclui `resources` e permissões de professor para artefatos/conteúdo.

### Imports principais

```tsx
import Link from "next/link";
import { Topbar } from "@/components/Topbar";
```

Nos componentes que usam Supabase no navegador:

```tsx
import { createClient } from "@/lib/supabase-browser";
```

Nas páginas server:

```tsx
import { createClient } from "@/lib/supabase-server";
```
