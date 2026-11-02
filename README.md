# movingclimate.cz

Web firmy Moving Climate s.r.o. Je to jedna statická stránka (`index.html`) s fotkami v `img/` a písmem v `fonts/`. Nic se nesestavuje, Netlify publikuje přímo tuhle složku.

Hosting je zdarma na Netlify. Doména `movingclimate.cz` zůstává na Wedosu, kde se jen nastaví DNS.

## Jak se web mění

Každá změna ve větvi `main` se na webu objeví sama, zhruba do minuty.

- **Přes Clauda:** napište v projektu, co změnit. Claude to připraví jako pull request. Vy ho na GitHubu zkontrolujete a dáte **Merge**.
- **Ručně:** na GitHubu otevřete `index.html`, klikněte na tužku, upravte text a uložte (Commit changes).

Netlify u každého pull requestu udělá i náhled (Deploy Preview), takže změnu uvidíte dřív, než ji pustíte ven.

## Nastavení (stačí jednou)

### 1. Napojit Netlify na tohle repo

1. Na [app.netlify.com](https://app.netlify.com) se přihlaste přes GitHub.
2. Zvolte **Add new site → Import an existing project → GitHub** a vyberte `Tomasraketak/WebMovingClimate`.
3. Build command nechte prázdný, Publish directory `.` (to už je nastavené v `netlify.toml`). Klikněte na **Deploy**.
4. V **Site configuration → Change site name** zvolte jméno, třeba `movingclimate`. Web pak poběží na `movingclimate.netlify.app`.

### 2. Doména

1. V Netlify: **Domain management → Add a domain**, zadejte `movingclimate.cz` a potvrďte i `www`.
2. Na Wedosu: [client.wedos.com](https://client.wedos.com) → **Domény → movingclimate.cz → DNS záznamy**.
   1. Smažte stávající A a AAAA záznamy s prázdným názvem a záznam `www`.
   2. Přidejte tyto dva záznamy:

| Název | Typ | Hodnota |
|---|---|---|
| *(prázdné)* | A | `75.2.60.5` |
| `www` | CNAME | `movingclimate.netlify.app` |

3. Až se DNS propíše (minuty až hodiny), Netlify sám zapne https. Pokud ne, v **Domain management → HTTPS** klikněte na **Verify DNS configuration**.

### 3. Formulář

Formulář zpracovává Netlify Forms, zdarma do 100 zpráv měsíčně.

1. Po prvním nasazení zkontrolujte v Netlify sekci **Forms**, že je tam formulář `kontakt`. Pokud ne, zapněte **Enable form detection** a v **Deploys** dejte **Trigger deploy**.
2. Nastavte posílání zpráv e-mailem: **Site configuration → Notifications → Form submission notifications → Email notification**, třeba na `moving.climate@gmail.com`.

### 4. E-mail zakazky@movingclimate.cz zdarma

Adresu přesměrujete na Gmail přes [ImprovMX](https://improvmx.com).

1. V ImprovMX zadejte doménu `movingclimate.cz` a cíl `moving.climate@gmail.com`.
2. Na Wedosu v DNS přidejte tyto záznamy a smažte staré MX:

| Název | Typ | Priorita | Hodnota |
|---|---|---|---|
| *(prázdné)* | MX | 10 | `mx1.improvmx.com` |
| *(prázdné)* | MX | 20 | `mx2.improvmx.com` |
| *(prázdné)* | TXT | | `v=spf1 include:spf.improvmx.com ~all` |

## Pravidla obsahu

Web je pro města. Píšeme jen to, co už reálně máme: žádné ceny, dokud nejsou ověřené, a žádná roadmapa.

Barvy:
- `#FDFBF7` krémová
- `#2B3240` tmavě modrá
- `#FF6C33` oranžová
