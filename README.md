# Monitor PMS5003 Dashboard

Dashboard para monitoramento de partículas PM2.5, PM1.0 e PM10 do sensor PMS5003.

## Build e Deploy

### Build local da imagem Docker

```bash
docker build -t monitor-dashboard .
```

### Executar localmente

```bash
docker run -p 8080:80 monitor-dashboard
```

Acesse em: http://localhost:8080

### Deploy no Easypanel

1. Conecte seu repositório Git ao Easypanel
2. Configure o serviço para usar o Dockerfile
3. A porta padrão é 80 (o Easypanel geralmente mapeia automaticamente)
4. Configure variáveis de ambiente se necessário

## Estrutura

- `index.html` - Página principal do dashboard
- `Dockerfile` - Configuração do container Docker
- `nginx.conf` - Configuração do servidor web nginx
- `.dockerignore` - Arquivos ignorados no build

## Configuração da API

A URL da API pode ser configurada diretamente na interface do dashboard através do campo "API Base URL".
