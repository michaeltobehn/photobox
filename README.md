# Photobox

DIY Party-Fotobox als Web-App (Tablet/iPad).

Live: https://photobox-bice.vercel.app (Vercel, Auto-Deploy bei Push auf `main`).

## QR-Sharing

Nach „Behalten" wird jedes Foto in den Supabase-Storage-Bucket `fotobox`
(Projekt **SM-Marketing**) hochgeladen und ein QR-Code angezeigt, über den
Gäste das Foto aufs Handy laden. Die QR-Bilder rendert
`https://qr-coder.supermatt.agency/api/render`.

## Slideshow (TV/Beamer)

Live-Diashow aller Event-Fotos: Auf dem TV/Beamer-Gerät die Fotobox-URL
öffnen, denselben Eventnamen eingeben und „📺 Slideshow für TV/Beamer"
tippen — oder direkt ansteuern:
`https://photobox-bice.vercel.app/#slideshow=<event-slug>&title=<Anzeigename>`
(Slug = Eventname kleingeschrieben mit Bindestrichen, z. B.
`annas-30-geburtstag`). Neue Fotos erscheinen automatisch nach wenigen
Sekunden und werden in der Rotation vorgezogen. Beenden mit ✕ oder Escape.

**Aufräumen nach dem Event:** Die Foto-Links sind nicht erratbar, aber
öffentlich für jeden, der sie hat, und bleiben unbegrenzt online. Zum Löschen:
Supabase-Dashboard → Projekt *SM-Marketing* → Storage → Bucket `fotobox` →
Ordner des Events (benannt nach dem Eventnamen, z. B. `annas-30-geburtstag`)
auswählen und löschen.
