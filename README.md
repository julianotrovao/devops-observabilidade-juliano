
# move-tech-cloud-application-comp-5
Aluno-juliano
Ponto de partida da **Competência 5 — Observabilidade e Resiliência de Sistemas**.

Este repositório é um template. Use-o como base para criar o seu próprio repositório e trabalhar na competência.

> Parte do curso **Move Tech** — Magalu × Prósper Digital Skills  
> Formação em Cloud Computing para iniciantes

---

## Etapas anteriores

> [move-tech-cloud-application-comp-3](https://github.com/move-tech-cloud-computing/move-tech-cloud-application-comp-3) · [move-tech-cloud-application-comp-4](https://github.com/move-tech-cloud-computing/move-tech-cloud-application-comp-4)

---

## O que você vai fazer nesta competência

Ao final da Competência 5, a aplicação deve estar **monitorada e resiliente**.

O código de observabilidade já está no repositório — logs em JSON, `/health` com verificação do banco, `/stats` com contagens e `/metrics` em formato Prometheus. Seu trabalho é configurar o monitoramento e observar a aplicação em produção.

- [ ] Fazer o deploy da aplicação
- [ ] Verificar os logs estruturados via `kubectl logs`
- [ ] Consultar `/health`, `/stats` e `/metrics` em produção
- [ ] Instalar Prometheus e Grafana via Helm no cluster K3s (`kube-prometheus-stack`)
- [ ] Criar o `ServiceMonitor` e confirmar a aplicação como target UP no Prometheus
- [ ] Simular uma falha e observar a recuperação automática pelo Kubernetes

---

## Como rodar localmente

**Pré-requisito:** [Docker Desktop](https://www.docker.com/products/docker-desktop/) instalado (Mac e Windows) ou [Docker Engine](https://docs.docker.com/engine/install/) (Linux).

```bash
docker compose up --build
```

Acesse a documentação interativa em: http://localhost:8000/docs

---

## Secrets necessários no GitHub

| Secret | Descrição |
|--------|-----------|
| `MGC_REGISTRY_USER` | Usuário do Container Registry da MGC |
| `MGC_REGISTRY_PASSWORD` | Senha do Container Registry da MGC |
| `MGC_REGISTRY_NAME` | Nome do seu registry na MGC |
| `MGC_KUBECONFIG` | Conteúdo do arquivo `kubeconfig.yaml` (cole o conteúdo diretamente) |
| `DATABASE_URL` | String de conexão do PostgreSQL (`postgresql://user:pass@host/orders`) |

---

## Próxima etapa

Ao concluir esta competência, a solução de referência será publicada em:  
[move-tech-cloud-application-comp-6](https://github.com/move-tech-cloud-computing/move-tech-cloud-application-comp-6)
