# 🚀 CSF/LFD to UFW + Fail2Ban Migrator (Ansible)

Este repositório contém uma solução automatizada, não-interativa e segura para migrar o firewall de servidores Linux de **CSF/LFD** para **UFW + Fail2Ban** em lote, utilizando o **Ansible**.

A migração foi projetada para ser **idempotente** (pode ser executada várias vezes sem quebrar o sistema) e possui mecanismos **anti-lockout** para garantir que você não perca o acesso SSH aos servidores durante o processo.

---

## ✨ Características do Projeto

* 🛑 **Totalmente Não-Interativo:** Sem pausas ou prompts de confirmação (`read -r`), ideal para execuções em paralelo via Ansible.
* 🛡️ **Proteção Anti-Lockout:** Garante explicitamente a liberação da porta `22/tcp` (SSH) antes de ativar o UFW, evitando bloqueios acidentais.
* 🔄 **Idempotência Nativa:** Se um host já foi migrado, o script detecta a ausência do CSF e pula as etapas de remoção/migração, realizando apenas a higienização e validação do UFW/Fail2Ban.
* 📦 **Backup Automático:** Cria um tarball de segurança de `/etc/csf` e `/etc/lfd` antes de qualquer alteração (caso o CSF ainda exista).
* 📋 **Relatório de Auditoria:** Exibe o status final das regras do UFW e das Jails do Fail2Ban no log do Ansible.


wget https://raw.githubusercontent.com/nicolasbrandaoc/-csf-ufw-fail2ban_migrator-ansible/main/migracao.sh
