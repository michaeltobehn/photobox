# Photobox

DIY Party-Fotobox als Web-App (Tablet/iPad).

Live: https://sabrina.supermatt.agency (Vercel, Auto-Deploy bei Push auf `main`).

## QR-Sharing

Nach „Behalten" wird jedes Foto in den Supabase-Storage-Bucket `fotobox`
(Projekt **SM-Marketing**) hochgeladen und ein QR-Code angezeigt, über den
Gäste das Foto aufs Handy laden. Die QR-Bilder rendert
`https://qr-coder.supermatt.agency/api/render`.

## Slideshow (TV/Beamer)

Live-Diashow aller Event-Fotos: Auf dem TV/Beamer-Gerät die Fotobox-URL
öffnen, denselben Eventnamen eingeben und „📺 Slideshow für TV/Beamer"
tippen — oder direkt ansteuern:
`https://sabrina.supermatt.agency/#slideshow=<event-slug>&title=<Anzeigename>`
(Slug = Eventname kleingeschrieben mit Bindestrichen, z. B.
`annas-30-geburtstag`). Neue Fotos erscheinen automatisch nach wenigen
Sekunden und werden in der Rotation vorgezogen. Beenden mit ✕ oder Escape.

## Gäste-Onboarding + Handy-Galerie

Gäste scannen den Event-QR und landen auf
`https://sabrina.supermatt.agency/#gast=sabrinas-40-geburtstag&title=Sabrinas%2040.%20Geburtstag`:
kurzes Onboarding (Name → Tabelle `fotobox_gaeste` in Supabase, dort siehst
du, wer dabei ist), danach eine Live-Galerie aller Event-Fotos (neueste
zuerst, aktualisiert alle 12 s, Teilen/Sichern per iOS-Share). Die Galerie
ist bewusst read-only — Fotos kommen nur aus der Fotobox.

**Event-QR anlegen (einmalig, qr-coder-Console):** Dynamischen Code mit
obiger Gast-URL als Ziel erstellen (→ Scan-Statistik), QR drucken. Danach
die `/r/`-Kurz-URL in `index.html` bei `GUEST_QR_URL_OVERRIDE` eintragen —
dann zeigt auch die QR-Ecke der TV-Slideshow auf den getrackten Link.
Ohne Eintrag rendert die Slideshow-Ecke den QR direkt auf die Gast-URL
(funktioniert genauso, nur ohne Statistik).

**TV/Beamer:** Zweitgerät (iPhone/iPad/Mac) öffnet die Slideshow-URL in
Safari und spiegelt per AirPlay — oder der Smart-TV-Browser öffnet sie
direkt. Das Fotobox-iPad dafür nicht benutzen, das ist die Kamera.

**Aufräumen nach dem Event:** Die Foto-Links sind nicht erratbar, aber
öffentlich für jeden, der sie hat, und bleiben unbegrenzt online. Zum Löschen:
Supabase-Dashboard → Projekt *SM-Marketing* → Storage → Bucket `fotobox` →
Ordner des Events (benannt nach dem Eventnamen, z. B. `annas-30-geburtstag`)
auswählen und löschen.
