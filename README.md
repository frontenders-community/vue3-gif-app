#Frontenders Community

## Challenge #6 - GIF APP

In questa challenge andiamo a creare un'app per cercare delle gif, insernedo parole chiave. Per la ricerca utilizzeremo https://tenor.com/gifapi.
Dopo aver inserito la chiave di ricerca e premuto invio, l'utente potrà visulizzare le gif posizinati nella griglia. Ricordate che non vedremo tutte le gif, perché sono divise in pagine. Quindi dobbiamo eseguire le chiamate api al scroll della pagina, implementando l'effetto dell'infinite scroll.

Altre funzionalità del progetto sono:
- possibilità di cambiare tema: light/dark mode switcher;
- possibilità di condividere il link della gif tramite whatsapp;
- possibilità di copiare link in clipboard;
- layout responsive.


### Starter Kit

Nello starter kit troverte una cartella assets, suddivisa in questo modo:

- **sounds**: contiene i suoni da riprodurre al click dei tasti (credits: https://plays.org/virtu-drum-pads/)
- **data.js**: un array js che contiene i dati dei suoni e delle altre informazioni utili allo sviluppo

### Consigli

Questa challenge potrebbe essere realizzata tramite vanilla js, ma sicuramente è più consigliato utilizzare uno dei framework che renderà la struttura del progetto più manutenibile.

Partiamo dalla documentazione https://developers.google.com/tenor/guides/quickstart, quindi ci registriamo in Google Cloud Console e richiediamo API Key per poter accedere al Tenor. Ricordate che le credenziali di accesso non dovrebbero essere publiche e quindi trovate il modo per non condividerli su github. 

**Font**: Roboto
**Icone**: Fontawesome

### Bonus
- Implementa filtro delle gif per categoria.

### Tecnologie

HTML, CSS/SASS.
JS plain o React / Vue / Svelte.
No librerie CSS.

### Preview
![desktop dark](desktop-dark.png)
![desktop light](desktop-light.png)

### Demo:
https://olga-demina-gif-app.netlify.app/


