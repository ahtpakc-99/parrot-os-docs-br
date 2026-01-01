# AppArmor

O **AppArmor** é um sistema de segurança de aplicativos para Linux, eficaz e fácil de usar. Ele protege proativamente o sistema operacional e os aplicativos contra ameaças externas ou internas (mesmo ataques de dia zero/zero-day), impondo um bom comportamento e impedindo que falhas de aplicativos, mesmo as desconhecidas, sejam exploradas.

As políticas de segurança do AppArmor definem completamente quais recursos do sistema os aplicativos individuais podem acessar e com quais privilégios.

## 1. Verificando o Status
O AppArmor e seus perfis já devem estar habilitados e rodando por padrão no Parrot OS.

Para verificar se está ativo:
```bash
sudo aa-status --enabled; echo $?

```

*Se a saída for `0`, ele está ativo.*

Alternativamente, para ver os perfis carregados:

```bash
sudo aa-status

```

*Se por algum motivo o AppArmor não estiver instalado, siga as instruções abaixo.*

---

## 2. Instalação e Habilitação

Caso precise instalar manualmente:

```bash
sudo apt install apparmor apparmor-utils auditd

```

* **apparmor:** Pacote principal.
* **apparmor-utils:** Utilitários para controlar perfis.
* **auditd:** Ferramentas de geração automática de perfis e auditoria.

### Habilitar no Boot (GRUB)

Para garantir que o kernel carregue o AppArmor na inicialização:

1. Crie a configuração do GRUB:
```bash
sudo mkdir -p /etc/default/grub.d
echo 'GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT apparmor=1 security=apparmor"' | sudo tee /etc/default/grub.d/apparmor.cfg

```


2. Atualize o GRUB e reinicie:
```bash
sudo update-grub
sudo reboot

```



---

## 3. Gerenciando Perfis

Após reiniciar, verifique o estado detalhado:

```bash
sudo aa-status

```

Isso listará todos os perfis carregados e seus status:

* **Enforced:** As regras são aplicadas e violações são bloqueadas.
* **Complain:** As violações são permitidas, mas registradas nos logs (útil para testes).
* **Unconfined:** O processo roda sem restrições.

Para ver quais processos estão rodando em modo restrito (Enforced) agora:

```bash
ps auxZ | grep -v '^unconfined'

```

### Instalar Perfis Extras

Os perfis ficam em `/etc/apparmor.d/`. Você pode instalar perfis adicionais mantidos pela comunidade:

```bash
sudo apt install apparmor-profiles apparmor-profiles-extra

```

### Carregar Perfis (Complain vs Enforce)

Exemplo: Vamos colocar todos os perfis "extras" em modo **Complain** (apenas logar, não bloquear).

```bash
cd /usr/share/doc/apparmor-profiles/extras
sudo cp -i *.* /etc/apparmor.d/

# Loop para colocar todos em modo de reclamação (complain)
for f in *.*; do 
    sudo aa-complain /etc/apparmor.d/$f; 
done

```

> **⚠️ Cuidado:** Para definir como **Enforce** (bloqueio ativo), use `aa-enforce` em vez de `aa-complain`.
> Porém, muitos perfis extras podem estar desatualizados e quebrar o funcionamento dos programas. Use `enforce` apenas se estiver pronto para testar e corrigir as regras.

---

## 4. Debug e Diagnóstico

### Notificações de Bloqueio

O comando `aa-notify` pode exibir uma notificação na área de trabalho sempre que um programa gerar uma mensagem "DENIED" (Negado).

1. Dê permissão de leitura dos logs ao seu usuário:
```bash
sudo adduser "$USER" adm

```


2. O `aa-notify` deve iniciar automaticamente no próximo login. Se não, inicie manualmente:
```bash
aa-notify -p

```



### Verificar Logs

Para descobrir por que algo não está funcionando, verifique os logs em busca de bloqueios:

```bash
sudo tail -f /var/log/syslog | grep 'DENIED'

```

*Ou, se estiver usando auditd:*

```bash
sudo tail -f /var/log/audit/audit.log | grep 'DENIED'

```

### Testar Desativando um Perfil

Se suspeitar que o AppArmor está causando um bug em um programa específico (ex: Pidgin), desative apenas o perfil dele e teste novamente:

```bash
sudo aa-disable /etc/apparmor.d/usr.bin.pidgin

```

Se o bug sumir, o problema era o perfil. Você pode reativá-lo com:

```bash
sudo aa-enforce /etc/apparmor.d/usr.bin.pidgin

```

### Verificar Portas Desprotegidas

Para listar processos com portas TCP/UDP que **não** possuem perfis AppArmor carregados:

```bash
sudo aa-unconfined --paranoid

```

---

## 5. Desativar o AppArmor (Totalmente)

Se precisar desativar o sistema inteiro (não recomendado para segurança):

1. Edite a configuração do GRUB:
```bash
sudo mkdir -p /etc/default/grub.d
echo 'GRUB_CMDLINE_LINUX_DEFAULT="$GRUB_CMDLINE_LINUX_DEFAULT apparmor=0"' | sudo tee /etc/default/grub.d/apparmor.cfg

```


2. Aplique e reinicie:
```bash
sudo update-grub
sudo reboot

```
