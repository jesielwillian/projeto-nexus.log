<div align="center">

# NEXUS LOG

### Transporte inteligente. Conexões que movem negócios.

**Website institucional de transporte, logística e rastreamento**

![HTML5](https://img.shields.io/badge/HTML5-estrutura-e34f26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-estilos-1572b6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-f7df1e?logo=javascript&logoColor=111)
![Status](https://img.shields.io/badge/status-front--end%20demonstrativo-19bfff)

</div>

---

## 1. Visão geral

A **Nexus Log** é uma página institucional de uma empresa fictícia de transporte e logística. A experiência visual comunica tecnologia, previsibilidade e eficiência operacional, apresentando serviços, indicadores, cobertura geográfica, frota e canais de contato.

O projeto é desenvolvido com **HTML semântico, CSS e JavaScript nativo**, sem framework de interface ou etapa obrigatória de build.

> **Escopo atual:** front-end demonstrativo. Rastreamento, telemetria, dados da frota, indicadores e envio de cotação não representam operações reais enquanto não forem conectados a serviços e APIs de produção.

## 2. Mapa do projeto

```text
nexus/
├── index.html                 # Página institucional e estrutura das seções
├── readme.md                  # Documentação técnica do projeto
│
├── css/
│   └── style.css              # Tokens, reset, layout, componentes e responsividade
│
├── js/
│   ├── config.js              # Configuração e carregamento opcional do Google Maps
│   ├── main.js                # Interações, animações, rastreamento e mapas
│   ├── custom-select.js       # Selects personalizados e acessibilidade por teclado
│   └── counter.js             # Animação dos indicadores numéricos
│
└── imagens/
    ├── hero_poster.webp       # Imagem de poster do vídeo principal
    └── hero_video.mp4         # Vídeo de destaque da página
```

### Responsabilidade por arquivo

| Arquivo | Responsabilidade |
|---|---|
| `index.html` | Conteúdo, hierarquia semântica, formulários, componentes e pontos de inicialização |
| `css/style.css` | Identidade visual, variáveis, estilos de componentes, animações e breakpoints |
| `js/config.js` | Configuração global e inclusão condicional da API do Google Maps |
| `js/main.js` | Comportamentos centrais da interface e recursos demonstrativos |
| `js/custom-select.js` | Camada visual dos campos select, mantendo o select nativo como fonte do valor |
| `js/counter.js` | Contadores animados com suporte a casas decimais, sufixos e formato abreviado |
| `imagens/hero_poster.webp` | Poster estático exibido antes ou durante o carregamento do vídeo |
| `imagens/hero_video.mp4` | Mídia de fundo/destaque da seção principal |

## 3. Mapa da página

A página é organizada em uma única experiência institucional, com navegação por âncoras.

| Ordem | Área / identificador | Objetivo |
|---:|---|---|
| 01 | Header / navegação | Acesso às seções e ações principais |
| 02 | Hero / início | Apresentação da marca, proposta de valor e chamadas para ação |
| 03 | `#stats` | Indicadores e números institucionais |
| 04 | `#historia` | História e posicionamento da empresa |
| 05 | `#servicos` | Portfólio de soluções logísticas |
| 06 | `#tecnologia` | Recursos e diferenciais tecnológicos |
| 07 | `#rastreamento` | Consulta demonstrativa e painel visual da frota |
| 08 | `#cotacao` | Formulário para solicitação de cotação |
| 09 | Rodapé | Contatos, links e navegação complementar |

### Componentes de rastreamento

Dentro da área `#rastreamento`, o HTML contém pontos de montagem para:

- `#fleetMap`: mapa da frota.
- `#vehicleList`: lista de veículos.
- `#trackingEvents`: eventos operacionais.
- `#trackingResult`: resultado visual da consulta.
- `#trackingHistory`: histórico demonstrativo.

A área de cobertura possui o ponto de montagem `#coverageMap`.

## 4. Tecnologias e dependências

- **HTML5:** estrutura e semântica.
- **CSS3:** layout responsivo, variáveis, transições e animações.
- **JavaScript ES6+:** interações sem dependência de framework.
- **Google Fonts:** famílias Quicksand e Archivo.
- **Font Awesome 6.5.2:** biblioteca de ícones carregada por CDN.
- **Google Maps JavaScript API:** integração opcional para mapas.

Não há `package.json`, bundler ou gerenciador de dependências necessário para abrir a versão estática.

## 5. Como executar localmente

### Opção A — servidor HTTP simples

Na raiz da pasta `nexus`, execute:

```bash
python -m http.server 8000
```

Acesse:

```text
http://localhost:8000
```

### Opção B — Node.js

Se tiver o pacote `http-server` instalado:

```bash
http-server . -p 8000
```

> Recomenda-se utilizar um servidor HTTP local em vez de abrir o arquivo diretamente com `file://`, especialmente para testar mídia, scripts e integrações externas.

## 6. Configuração do Google Maps

O arquivo `js/config.js` expõe a configuração em `window.NEXUS_CONFIG` e injeta o script do Google Maps somente quando uma chave válida é informada.

Edite:

```js
window.NEXUS_CONFIG = Object.freeze({
  GOOGLE_MAPS_API_KEY: "SUA_CHAVE_DO_GOOGLE_MAPS",
  GOOGLE_MAP_ID: "SEU_MAP_ID",
});
```

### Requisitos no Google Cloud

1. Crie ou selecione um projeto no Google Cloud Console.
2. Ative o faturamento, quando exigido pelo serviço.
3. Habilite a **Maps JavaScript API** e as APIs adicionais necessárias ao mapa utilizado.
4. Crie uma chave de API.
5. Configure restrição por HTTP referrer para os domínios autorizados.
6. Configure limites de uso e alertas de faturamento.
7. Informe a chave e o Map ID no arquivo de configuração.

**Segurança:** uma chave utilizada no navegador não é secreta. Restrinja-a por domínio e por API. Não coloque credenciais privadas, tokens administrativos ou segredos de backend no JavaScript entregue ao navegador. Para ambientes com múltiplos domínios, use configurações específicas por ambiente.

Sem chave válida, o carregamento do Google Maps é ignorado. A interface deve ser tratada como demonstração até a integração real estar configurada.

## 7. Organização do JavaScript

Os scripts são carregados no final do documento, após o conteúdo HTML, nesta ordem:

1. `config.js` — disponibiliza as configurações e prepara o carregamento opcional do Maps.
2. `main.js` — inicializa interações gerais, rastreamento e recursos de mapa.
3. `custom-select.js` — configura os campos select personalizados.
4. `counter.js` — inicializa os contadores animados.

### `main.js`

Concentra os comportamentos de interface, incluindo:

- Helpers de seleção de elementos.
- Carregamento sob demanda do vídeo.
- Loader, progresso de rolagem e menu.
- Revelação de elementos e microinterações.
- Efeitos de inclinação e interação com ponteiro.
- Consulta demonstrativa de rastreamento.
- Dados e renderização visual da frota.
- Inicialização dos mapas e alternativa visual quando a API não está disponível.

### `custom-select.js`

Personaliza visualmente os campos marcados com `data-select`. O `<select>` nativo permanece no DOM, preservando o valor real do campo e a integração com formulários. O componente personalizado também trata estados de abertura, fechamento e interação por teclado.

### `counter.js`

Procura elementos com `data-counter` e anima seus valores quando entram na área visível. Os atributos `data-decimal`, `data-suffix` e `data-format` controlam a apresentação.

Exemplo de configuração no HTML:

```html
<span
  data-counter="12500"
  data-format="k"
  data-suffix="+"
>
  0
</span>
```

## 8. Organização do CSS

O arquivo `css/style.css` concentra toda a camada visual.

A estrutura foi mantida em blocos funcionais para facilitar a navegação:

1. Variáveis globais (`:root`).
2. Reset e estilos base.
3. Estrutura de layout e componentes.
4. Estilos das seções e elementos específicos.
5. Estados e microinterações.
6. Animações (`@keyframes`).
7. Media queries e preferências do usuário.

### Convenções de manutenção

- Reutilize os tokens de `:root` antes de criar cores ou medidas globais novas.
- Agrupe estilos próximos por componente ou seção.
- Evite duplicar regras para o mesmo seletor.
- Mantenha os breakpoints em ordem decrescente quando a estratégia for desktop-first.
- Preserve a ordem de declarações que dependem da cascata, de fallbacks ou de sobrescritas.
- Respeite `prefers-reduced-motion` para reduzir animações quando solicitado pelo sistema.

**Importante sobre ordenação:** a ordem alfabética de propriedades não deve ser aplicada cegamente. Declarações repetidas, fallbacks e combinações de shorthand/longhand podem depender da ordem original. Ao editar, priorize equivalência visual e funcional em vez de ordenação mecânica.

## 9. Integrações reais necessárias para produção

Os recursos abaixo são demonstrações de interface e precisam de serviços reais antes de serem utilizados em uma operação logística:

| Recurso | Integração necessária |
|---|---|
| Rastreamento | API de TMS/transportadora com consulta autenticada por código |
| Posição da frota | API de telemetria, GPS ou serviço de localização |
| Eventos operacionais | Backend que forneça eventos e timestamps confiáveis |
| Mapa de cobertura | Dados geográficos e regras reais de regiões atendidas |
| Cotação | Endpoint de backend com validação, persistência e envio para CRM/ERP |
| Indicadores | Fonte de dados operacional confiável e atualizada |

### Contrato recomendado para rastreamento

Uma API de rastreamento pode retornar, por exemplo:

```json
{
  "trackingCode": "NX-000123",
  "status": "in_transit",
  "updatedAt": "2026-01-15T14:30:00Z",
  "origin": {
    "city": "São Paulo",
    "state": "SP"
  },
  "destination": {
    "city": "Curitiba",
    "state": "PR"
  },
  "events": [
    {
      "description": "Carga em transferência",
      "occurredAt": "2026-01-15T14:30:00Z"
    }
  ]
}
```

Esse JSON é uma sugestão de contrato de integração, não uma API já implementada no projeto.

## 10. Segurança e qualidade

Antes de publicar:

- [ ] Validar os dados do formulário no frontend e no backend.
- [ ] Implementar validação de origem, destino, tipo de carga e contato no servidor.
- [ ] Adicionar proteção contra spam e abuso no endpoint de cotação.
- [ ] Não confiar em dados enviados pelo navegador.
- [ ] Não expor credenciais privadas no bundle frontend.
- [ ] Restringir a chave do Google Maps por domínio e API.
- [ ] Utilizar HTTPS em produção.
- [ ] Definir política de privacidade e tratamento de dados pessoais.
- [ ] Implementar logs e monitoramento no backend.
- [ ] Tratar falhas, timeouts e indisponibilidade das APIs.
- [ ] Testar navegação por teclado, foco e leitores de tela.
- [ ] Verificar responsividade em dispositivos reais.
- [ ] Otimizar imagens e vídeo para reduzir o tempo de carregamento.

## 11. Checklist de publicação

### Front-end

- [ ] Conferir todos os links e âncoras.
- [ ] Conferir caminhos de imagens, CSS e JavaScript.
- [ ] Testar menu e navegação mobile.
- [ ] Testar campos personalizados e formulário.
- [ ] Verificar console do navegador.
- [ ] Testar vídeo com rede lenta e reprodução bloqueada.
- [ ] Validar layout nos principais breakpoints.

### Integrações

- [ ] Configurar Google Maps em ambiente de produção.
- [ ] Conectar rastreamento a uma API real.
- [ ] Conectar frota a uma fonte de telemetria.
- [ ] Conectar formulário a backend/CRM.
- [ ] Implementar tratamento de erros e estados de carregamento.

### Infraestrutura

- [ ] Configurar domínio e HTTPS.
- [ ] Configurar cache para assets estáticos.
- [ ] Habilitar compressão HTTP.
- [ ] Configurar monitoramento e logs.
- [ ] Revisar SEO, metadados e compartilhamento social.

## 12. Princípios para evoluir o projeto

Para manter o código sustentável:

1. **Separação de responsabilidades:** estrutura no HTML, apresentação no CSS e comportamento no JavaScript.
2. **Progressive enhancement:** os conteúdos principais devem continuar acessíveis mesmo quando uma integração externa falhar.
3. **Acessibilidade:** estados visuais também devem ser refletidos por atributos semânticos e foco de teclado.
4. **Performance:** manter lazy-load para mídia pesada e evitar trabalho desnecessário durante o scroll.
5. **Segurança:** toda validação crítica e regra de negócio deve existir no backend.
6. **Observabilidade:** integrações reais devem registrar erros e permitir diagnóstico sem expor dados sensíveis.

---

<div align="center">

**NEXUS LOG**  
*Conectando operações. Movendo negócios.*

Documentação do projeto front-end.

</div>
