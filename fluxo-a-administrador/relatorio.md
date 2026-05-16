# Relatório — Laboratório de Inspeção HTTP/HTTPS — Fluxo A (Administrador)

> **Como usar este template.** Preencha cada campo `[...]` com sua resposta e arraste as capturas de tela diretamente para os locais indicados. Preserve a formatação Markdown.
>
> **Escopo:** este fluxo inclui HTTP em texto claro, HTTPS sem decriptação e HTTPS com decriptação TLS pelo Fiddler Classic.

---

## Como anexar capturas de tela

1. Faça a captura de tela e salve como PNG.
2. No editor do GitHub ou GitHub.dev, posicione o cursor no local indicado.
3. Arraste o PNG para o editor. O GitHub inserirá uma linha `![image](...)`.

---

## Identificação

| Campo | Valor |
|---|---|
| Nome | Rafael Inacio Santos da Silva  |
| RA | 239853 |
| Disciplina | Redes de Computadores |
| Turma | SI/N |
| Data | 15/05/2026 |
| Fluxo | **A — Aluno com privilégio de administrador** |
| SO utilizado | Windows 11] |
| Ferramenta de proxy | Fiddler Classic |
| Navegador(es) | Chrome |
| Decriptação HTTPS habilitada? | sim |
| Certificado Fiddler instalado durante a atividade? | sim |

---

## Atividade 1 — Primeira captura

### Captura

<img width="694" height="416" alt="image" src="https://github.com/user-attachments/assets/64596c40-b3b3-419c-a9a5-ff2ec1fb5bab" />
<!-- arraste a captura aqui: sessão de http://example.com com Request/Response Raw -->

**Request-line:**

GET https://example.com/ HTTP/1.1
Host: example.com
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache
sec-ch-ua: "Chromium";v="148", "Brave";v="148", "Not/A)Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/148.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8
Sec-GPC: 1
Accept-Language: pt-BR,pt;q=0.7
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br, zstd


**Status-line:**

HTTP/1.1 200 OK
Date: Sat, 16 May 2026 00:01:58 GMT
Content-Type: text/html
Connection: keep-alive
Server: cloudflare
last-modified: Thu, 14 May 2026 20:05:43 GMT
allow: GET, HEAD
Age: 11642
cf-cache-status: HIT
CF-RAY: 9fc61c61efaf86c5-GRU
Content-Length: 528

<!doctype html><html lang="en"><head><title>Example Domain</title><meta name="viewport" content="width=device-width, initial-scale=1"><style>body{background:#eee;width:60vw;margin:15vh auto;font-family:system-ui,sans-serif}h1{font-size:1.5em}div{opacity:0.8}a:link,a:visited{color:#348}</style></head><body><div><h1>Example Domain</h1><p>This domain is for use in documentation examples without needing permission. Avoid use in operations.</p><p><a href="https://iana.org/domains/example">Learn more</a></p></div></body></html>


**Cabeçalhos do request:**

| Cabeçalho       | Função                                                                        |
| --------------- | ----------------------------------------------------------------------------- |
| Host            | Indica o endereço do site que foi acessado. Nesse caso, o site é example.com. |
| Connection      | Indica que a conexão pode continuar aberta para outras requisições.           |
| Cache-Control   | Informa que o navegador pediu para não usar uma resposta antiga do cache.     |
| User-Agent      | Mostra informações do navegador e do sistema operacional usado na requisição. |
| Accept          | Informa quais tipos de conteúdo o navegador aceita receber como resposta.     |
| Accept-Language | Indica o idioma preferido do navegador, nesse caso português do Brasil.       |

**Resposta:**

| Campo         | Valor observado               |
| ------------- | ----------------------------- |
| Content-Type  | text/html                     |
| Server        | cloudflare                    |
| Date          | Fri, 15 May 2026 00:15:8 GMT  |
| Last-Modified | Thu, 14 May 2026 20:05:43 GMT |
| Allow         | GET, HEAD                     |

---

## Atividade 2 — Anatomia de um GET

### Captura

<img width="1911" height="1000" alt="image" src="https://github.com/user-attachments/assets/8583e8c1-d667-4558-a280-4d0c6ee203a0" />


**Request-line completa:**

GET https://http.aulasrede.com.br/get?aluno=RafaelInacio&curso=redes HTTP/1.1
Host: http.aulasrede.com.br
Connection: keep-alive
sec-ch-ua: "Chromium";v="148", "Brave";v="148", "Not/A)Brand";v="99"
sec-ch-ua-mobile: ?0
sec-ch-ua-platform: "Windows"
Upgrade-Insecure-Requests: 1
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/148.0.0.0 Safari/537.36
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8
Sec-GPC: 1
Accept-Language: pt-BR,pt;q=0.5
Sec-Fetch-Site: none
Sec-Fetch-Mode: navigate
Sec-Fetch-User: ?1
Sec-Fetch-Dest: document
Accept-Encoding: gzip, deflate, br, zstd



**Cabeçalhos-chave:**

 Cabeçalho | Valor |
|---|---|
| `Host` | `http.aulasrede.com.br` |
| `User-Agent` | `Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/148.0.0.0 Safari/537.36` |
| `Accept` | `text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8` |

**Campos do JSON de resposta:**

```json
{
  "args": {
    "aluno": "RafaelInacio",
    "curso": "redes"
  },
  "headers": {
    "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8",
    "Accept-Language": "pt-BR,pt;q=0.5",
    "Host": "http.aulasrede.com.br",
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/148.0.0.0 Safari/537.36"
  },
  "origin": "IP de origem do cliente"
}

**Resposta curta:** o que o campo `origin` representa? O `User-Agent` retornado coincide com o enviado?

O campo `origin` mostra o IP de origem do acesso. O `User-Agent` retornado é o mesmo que foi enviado, mostrando que o servidor recebeu as informações do navegador usado na requisição.

---

## Atividade 3 — POST e envio de formulário

### Captura

<img width="1916" height="967" alt="image" src="https://github.com/user-attachments/assets/d511e7bf-1451-4b51-a0f2-1720e70e8957" />


**Request-line do POST:**

POST https://http.aulasrede.com.br/post HTTP/1.1

| Cabeçalho | Valor |
|---|---|
| `Content-Type` | keep-alive |
| `Content-Length` | 111 |

**Corpo do request:**

nome=Rafael+Inacio+Santos+da+Silva&disciplina=Redes&observacao=Teste+de+formul%C3%A1rio+HTTP.&interesse=headers

**Campo `form` da resposta:**

```json
{
  "disciplina": "Redes",
  "interesse": "headers",
  "nome": "Rafael Inacio Santos da Silva",
  "observacao": "teste do formulário HTTP"
}

**Resposta curta:** qual formato codifica o corpo? Qual aba mostra literalmente os bytes enviados: `WebForms` ou `Raw`?

O corpo foi enviado no formato `application/x-www-form-urlencoded`. Nesse formato, os dados do formulário são enviados como pares de campo e valor. A aba `WebForms` mostra esses dados de forma organizada, mas a aba `Raw` mostra literalmente o conteúdo enviado na requisição.

---

## Atividade 4 — Status codes

### Captura

<!-- arraste a captura aqui: lista do Fiddler com as quatro sessões -->

| # | Método | URL | Status-line | Tamanho/body |
|---|---|---|---|---|
| 1 | GET | `https://http.aulasrede.com.br/status/200` | [...] | [...] |
| 2 | GET | `https://http.aulasrede.com.br/redirect-to?status_code=301&url=/get` | [...] | [...] |
| 3 | GET | `https://http.aulasrede.com.br/status/404` | [...] | [...] |
| 4 | GET | `https://http.aulasrede.com.br/status/500` | [...] | [...] |

**Resposta curta:** no `301`, qual cabeçalho informa o destino do redirecionamento?

[resposta]

---

## Atividade 5 — Cabeçalhos essenciais

### Captura

<!-- arraste a captura aqui: Inspectors → Headers -->

| Cabeçalho | Req/Resp | Valor capturado | Função |
|---|---|---|---|
| `Host` | [...] | [...] | [...] |
| `User-Agent` | [...] | [...] | [...] |
| `Accept` | [...] | [...] | [...] |
| `Content-Type` | [...] | [...] | [...] |
| `Content-Length` / `Transfer-Encoding` | [...] | [...] | [...] |
| `Content-Encoding` | [...] | [...] | [...] |
| `Set-Cookie` | [...] | [...] | [...] |
| `Cache-Control` | [...] | [...] | [...] |
| `Strict-Transport-Security` | [...] | [...] | [...] |

**Resposta curta:** qual é o papel de `Content-Encoding` e de `Strict-Transport-Security`?

[resposta]

---

## Atividade 6 — HTTP vs HTTPS

### Captura — HTTP puro

<!-- arraste a captura aqui: http://http.aulasrede.com.br/get com redirecionamento 301 para HTTPS -->

### Captura — HTTPS sem decriptação

<!-- arraste a captura aqui: https://http.aulasrede.com.br/get sem decriptação -->

### Captura — HTTPS com decriptação

<!-- arraste a captura aqui: https://http.aulasrede.com.br/get com decriptação -->

| Situação | O que ficou visível? | O que ficou oculto? |
|---|---|---|
| HTTP puro | [...] | [...] |
| HTTPS sem decriptação | [...] | [...] |
| HTTPS com decriptação | [...] | [...] |

**Resposta curta:** por que a decriptação HTTPS pelo Fiddler exige instalar um certificado raiz?

[resposta]

---

## Atividade 7 — Cookies e sessão

### Captura

<!-- arraste a captura aqui: sequência cookies/set e cookies -->

| # | URL | `Set-Cookie` recebido | `Cookie` enviado |
|---|---|---|---|
| 1 | `/cookies/set?...` | [...] | [...] |
| 2 | `/cookies` | [...] | [...] |
| 3 | `/cookies` após recarregar | [...] | [...] |

**Resposta curta:** `Set-Cookie` apareceu em toda requisição ou apenas quando o servidor definiu/atualizou cookies? Quais atributos foram observados?

[resposta]

---

## Atividade 8 — Manipulação simples com breakpoint *(Opcional)*

### Captura

<!-- arraste a captura aqui: breakpoint com User-Agent editado -->

**JSON de resposta:**

```json
{
  "user-agent": ["[valor observado]"]
}
```

**Resposta curta:** o que este teste mostra sobre o papel ativo de um proxy?

[resposta]

- [ ] Breakpoints desabilitados ao final

---

## Reflexão final (opcional)

[até 10 linhas]

---

## Encerramento — Higiene de segurança

### Captura antes da remoção

<!-- arraste aqui a captura do certmgr.msc mostrando DO_NOT_TRUST_FiddlerRoot presente -->

### Captura depois da remoção

<!-- arraste aqui a captura mostrando o certificado ausente -->

- [ ] `Decrypt HTTPS traffic` desabilitado no Fiddler
- [ ] Certificado `DO_NOT_TRUST_FiddlerRoot` removido do Windows
- [ ] Certificado `DO_NOT_TRUST_FiddlerRoot` removido do Firefox, se aplicável
- [ ] Fiddler fechado

**Por que esta etapa é importante?**

[resposta curta]

---

## Checklist de entrega

- [ ] Campos `[...]` substituídos
- [ ] Capturas inseridas
- [ ] Atividades 1 a 7 preenchidas; Atividade 8 preenchida se executada
- [ ] Encerramento com duas capturas concluído
- [ ] PDF gerado como `SOBRENOME_NOME_RA_LAB_HTTP_FLUXOA.pdf`
- [ ] PDF submetido no Microsoft Teams
