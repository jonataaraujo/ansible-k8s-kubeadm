# Ansible K8S Kubeadm

Este repositório fornece uma coleção Ansible para montar um cluster Kubernetes (kubeadm) composto por um Control Plane sem redundância e workers.

Resumo rápido
- Configuração e orquestração via Ansible.

Requisitos mínimos:
- VMs criadas com distruibuição REDHAT (Rocky Linux 9);
- Recursos recomendados para cluster padrão (1 control plane + 2 workers): ≥ 6 CPUs, ≥ 10 GB RAM, ≥ 50 GB disco.

Instalação e deploy do cluster:

1. Clone este repositório:
```
   git clone https://github.com/jonataaraujo/ansible-k8s-kubeadm.git && cd ansible-k8s-kubeadm
```
2. Certifique-se de ter o ansible:
```
   ansible --version
```
3. Configure os IPs, usuário e senha dos hosts no arquivo de inventory:
   ```
   vi inventory.ini
   ```

4. Executar o deploy:
```
   ansible-playbook site.yml
```

5. A versão do repositório do kubernetes e `v1.31` e a versão do kubernetes é a `v1.31.14`, para mudar a versão, pode ser passado como parametro extra na execução do deploy:
```
ansible-playbook site.yml -e kube_repo_version=v1.32 -e kube_version=v1.32.10
```

Estrutura do projeto
- ansible/ — playbooks, roles e a coleção Ansible.
- ansible.cfg — Configurações para o ansible.
- inventory.ini/ — inventários de exemplo para Ansible.
- README.md - Arquivo de documentação
- site.yml - Playbook para provisioning.

Configurações importantes
- Verifique o inventário em `inventory.ini` para alterar IPs/hostnames.
- A configuração do kubeconfig costuma estar disponível em `~/admin.conf` na VM control plane; copie para `~/.kube/config` se desejar usar kubectl localmente via SSH.

Dicas e solução de problemas
- Para ativar debug do Ansible: adicione `-vvv` ao comando `ansible-playbook`.

Contribuição
- Pull requests são bem-vindos. Abra issues para bugs ou sugestões.
- Mantenha commits pequenos e descreva claramente as mudanças.

Autor: [Jonata Martins](https://www.linkedin.com/in/jonataaraujo/)
