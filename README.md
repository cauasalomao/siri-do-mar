# Pousada Siri do Mar — Site

Site institucional da **Pousada Siri do Mar**, em Praia de Leste, Pontal do Paraná. HTML/CSS/JS estático, sem build, sem framework, sem `package.json`.

## Rodando localmente

```bash
python -m http.server 8000
# ou
npx serve .
```

Abra http://localhost:8000.

## Estrutura

```
/                       Home
/sobre/                 História e diferenciais
/experiencia/           Estrutura, lazer e entorno
/acomodacoes/           Suíte Padrão (11 unidades)
/galeria/               Galeria de fotos com lightbox
/localizacao/           Mapa + atrações próximas
/contato/               Formulário + mapa

assets/css/style.css    CSS único (paleta azul-mar / coral / areia)
assets/js/main.js       JS único (constantes do hotel no topo)
assets/img/             Logo + fotos do cliente (exterior, quartos, piscina, recepcao, pessoas)
hotel-config.json       Fonte de verdade dos dados do hotel
favicon.svg             Favicon
sitemap.xml             Sitemap (sem blog)
robots.txt              Robots
```

## TODOs antes de publicar

Tudo que estiver marcado `TODO` no projeto precisa ser preenchido:

1. **`assets/js/main.js` (topo do arquivo):**
   - `WEBHOOK_URL` — URL do n8n/Zapier que recebe leads
   - `BOOKING_URL` e `MOTOR_BASE` já apontam para o motor HQBeds: `https://booking.hqbeds.com.br/pousadasiridomar`
   - Formato da URL gerada: `{MOTOR_BASE}?checkin=YYYY-MM-DD&checkout=YYYY-MM-DD&adults=N&children=N&childrenAges=A1,A2` (validar com a HQBeds se os nomes dos parâmetros precisam ser ajustados)
2. **`hotel-config.json`:**
   - `address.zip` (CEP)
   - `address.coordinates` (lat/lng exatos para o mapa e JSON-LD)
   - `business.cnpj`
   - `pet_policy` (alérgico/permitido?)
   - `food_policy` (café da manhã?)
   - `policies` (crianças, pagamento, cancelamento)
   - `integrations` (webhook, GTM, motor, domínio definitivo)
3. **GTM:** quando tiver o ID, injetar nos blocos `<!-- GTM HEAD -->` e `<!-- GTM BODY -->` de cada `index.html`.
4. **Domínio:** confirmar `pousadasiridomar.com.br` (ou outro) e atualizar nos blocos JSON-LD, OG/Twitter, sitemap e canonical de cada página.

## Arquitetura

Para detalhes (modais globais injetados via JS, como o header troca entre hero-mode e solid, paleta da logo, etc.) leia `CLAUDE.md`.
