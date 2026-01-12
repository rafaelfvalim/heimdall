# Monitor PMS5003 Dashboard

Dashboard para monitoramento de partículas PM2.5, PM1.0 e PM10 do sensor PMS5003.

## Build e Deploy

### Build local da imagem Docker

```bash
docker build -t monitor-dashboard .
```

### Executar localmente

```bash
docker run -p 8080:80 \
  -e API_BASE_URL=https://sua-api.com \
  -e API_KEY=sua-chave-secreta \
  monitor-dashboard
```

Acesse em: http://localhost:8080

### Deploy no Easypanel

1. Conecte seu repositório Git ao Easypanel
2. Configure o serviço para usar o Dockerfile
3. A porta padrão é 80 (o Easypanel geralmente mapeia automaticamente)
4. Configure as variáveis de ambiente obrigatórias:
   - `API_BASE_URL`: URL base da API (ex: `https://sites-automator.aal5pu.easypanel.host`)
   - `API_KEY`: Chave de autenticação da API

## Estrutura

- `index.html` - Página principal do dashboard
- `Dockerfile` - Configuração do container Docker
- `nginx.conf` - Configuração do servidor web nginx
- `entrypoint.sh` - Script que injeta variáveis de ambiente no HTML
- `.dockerignore` - Arquivos ignorados no build

## Variáveis de Ambiente

O dashboard utiliza variáveis de ambiente para configuração:

- **API_BASE_URL** (obrigatório): URL base da API
  - Exemplo: `https://sites-automator.aal5pu.easypanel.host`
  
- **API_KEY** (obrigatório): Chave de autenticação da API
  - Esta chave será injetada automaticamente no HTML durante o build

### Configuração no Easypanel

No painel do Easypanel, adicione as variáveis de ambiente na seção de configuração do serviço:

```
API_BASE_URL=https://sua-api.com
API_KEY=sua-chave-secreta
```

**Nota:** As variáveis são injetadas no HTML na inicialização do container. Se você alterar as variáveis, será necessário reiniciar o container.
