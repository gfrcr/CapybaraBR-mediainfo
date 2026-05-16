Este custom do CapybaraBR para o Prowlarr lê o **MediaInfo** retornado pela API do tracker e adiciona os idiomas no título do release.

Exemplo:

```
The Matrix 1999 2160p WEB-DL DUAL-Grupo / Brazilian, English
```

Isso ajuda o Radarr/Sonarr a identificar áudio PT-BR, Brazilian ou Dual Audio antes de baixar o arquivo.

## Baixe o arquivo

[Baixar capybarabr_mediainfo.yml](https://github.com/gfrcr/CapybaraBR-mediainfo/raw/main/capybarabr_mediainfo.yml)

## Copie para a pasta Custom do Prowlarr

O arquivo precisa ficar em:

```
/config/Definitions/Custom/
```

Se a pasta não existir, crie.

Reinicie o Prowlarr.

## Adicione o indexer no Prowlarr

No Prowlarr:

```
Indexers > Add Indexer
```

Procure por:

```
CapybaraBR Media Info (API)
```

Preencha sua **API key do CapybaraBR**.

### Extract Mediainfo language

- Liga a leitura do MediaInfo retornado pela API.
- É isso que permite adicionar idiomas no final do título, como **/ Brazilian, English, Japanese**.
- Recomendado: **ON**.

### Extract Mediainfo language on RSS/feed

- Faz a mesma leitura de MediaInfo também no RSS/feed.
- Pode deixar o indexer pesado, porque RSS costuma buscar muitos resultados de uma vez.
- Recomendado: **OFF**.

### Results per page when Mediainfo is enabled

- Controla quantos resultados a API busca por página quando o MediaInfo está ligado.
- Quanto maior, mais pesado fica.
- Recomendado: **30**. Se der timeout, use **20**.

### Languages appended to release title

- Controla quais idiomas serão adicionados no título.
- **Brazilian and English only**: mostra só Brazilian e English. Recomendado para Radarr.
- **Brazilian only**: mostra só Brazilian.
- **All mapped audio languages**: mostra todos os idiomas detectados.
- **Do not append audio languages**: não adiciona idiomas no título.

Configuração recomendada:

```
Extract Mediainfo language: ON
Extract Mediainfo language on RSS/feed: OFF
Results per page when Mediainfo is enabled: 30
Languages appended to release title: Brazilian and English only
```

Clique em **Test** e depois **Save**.

## Configuração recomendada para Radarr

Para o Radarr, recomendo usar esse custom sem RSS:

```
RSS: OFF
Automatic Search: ON
Interactive Search: ON
Categories: 2000
```

### O que essas opções significam?

- **RSS**: monitora releases novos automaticamente. Neste custom, recomendo deixar OFF para evitar timeout.
- **Automatic Search**: permite que o Radarr use o indexer em buscas automáticas, como Search on Add.
- **Interactive Search**: permite usar o indexer na busca manual/interativa.
