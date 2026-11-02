# SGBIM — Controle de Licenças Autodesk (Final)

## Colunas da planilha / importação CSV
| Coluna |
|--------|
| Autodesk products |
| Quantidade |
| Tipo de Licença |
| Inicio |
| Expiração |
| Situação |
| Contrato |
| Grupo |
| Equipamento |
| Modelo Equipamento |
| User |
| Nome usuário |
| Setor |
| Email Associado |
| Telefone |
| Whatsapp |
| Observação |

Obrigatórios na importação: **Contrato**, **Nome usuário**, **Email Associado**.

## Supabase — criar tabela
```sql
create table if not exists public.licencas (
  id bigint primary key,
  produto text,
  quantidade integer default 1,
  tipo_licenca text,
  inicio text,
  expiracao text,
  situacao text,
  contrato text,
  grupo text,
  equipamento text,
  modelo_equipamento text,
  user_login text,
  nome_usuario text,
  setor text,
  email text,
  telefone text,
  whatsapp text,
  observacao text,
  modificado_por text
);

alter table public.licencas enable row level security;

create policy "leitura anon" on public.licencas for select to anon using (true);
create policy "escrita anon" on public.licencas for all to anon using (true) with check (true);
```

Se a tabela antiga existir, prefira **dropar e recriar** ou adicionar as colunas novas.

## Usuários
- Admins (admin123): sgbim.adm@outlook.com · sgbim.direcao@outlook.com · sgbim.suporte@outlook.com
- Consulta (user123): sgbim.consulta@outlook.com

## Deploy
Substitua index.html, README.md e vercel.json no GitHub. Vercel redeploya sozinha.
