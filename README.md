# SGBIM — Controle de Licenças Autodesk (Completo v5)

Versão **completa**: interface completa + 17 colunas Autodesk + Supabase + importação que **ignora linhas inválidas**.

## Colunas CSV
Autodesk products, Quantidade, Tipo de Licença, Inicio, Expiração, Situação, Contrato, Grupo, Equipamento, Modelo Equipamento, User, Nome usuário, Setor, Email Associado, Telefone, Whatsapp, Observação

Obrigatórios por linha: Contrato, Nome usuário, Email Associado. Linhas sem isso (ou e-mail inválido) são **puladas**; as demais entram.

## Supabase
```sql
create table if not exists public.licencas (
  id bigint primary key, produto text, quantidade integer default 1, tipo_licenca text,
  inicio text, expiracao text, situacao text, contrato text, grupo text, equipamento text,
  modelo_equipamento text, user_login text, nome_usuario text, setor text, email text,
  telefone text, whatsapp text, observacao text, modificado_por text
);
alter table public.licencas enable row level security;
create policy "leitura anon" on public.licencas for select to anon using (true);
create policy "escrita anon" on public.licencas for all to anon using (true) with check (true);
```

## Usuários
Admins (admin123): sgbim.adm@outlook.com · sgbim.direcao@outlook.com · sgbim.suporte@outlook.com
Consulta (user123): sgbim.consulta@outlook.com
