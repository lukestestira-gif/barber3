# Barber Booking V5

Moderni responsive barber booking sajt + admin panel.

## Pokretanje

Potrebno: Node.js 18+

```bash
npm start
```

Server po defaultu koristi port 3000. Ako je 3000 zauzet, automatski pokušava 3001, 3002 itd. (do 3009). U terminalu će ispisati tačnu adresu.

Sajt: `http://localhost:3000`
Admin: `http://localhost:3000/admin`

Admin podaci:
- username: `admin`
- početna lozinka: `Barber123!` (prva prijava zahteva da je promeniš; koristi najmanje 12 znakova)

Nova lozinka se čuva kao scrypt hash u `data/admin-auth.json`. Ako koristiš `ADMIN_PASS`, promena lozinke se upravlja kroz tu serversku environment promenljivu. Ne objavljuj `data/` folder niti backup fajlove.

Za produkciju postavi jedinstvene kredencijale kroz environment variables:

```bash
ADMIN_USER=noviadmin ADMIN_PASS=jaka-lozinka npm start
```

Neuspešni pokušaji prijave su ograničeni. Autentifikovani admin može preuzeti JSON backup iz Dashboard > Bezbednost; backup sadrži rezervacije i kontakt podatke, pa ga čuvaj privatno.

## V5 novosti

- Zakazani termin odmah nestaje iz slobodnih termina; preklapajući termini se takođe ne nude.
- Live osvežavanje termina preko Server-Sent Events, bez ručnog F5.
- Posle uspešne rezervacije korisnik se vraća na vrh sajta i dobija potvrdu termina.
- Admin kalendar ima desktop prikaz sa kolonama po barberu i poseban responsive mobilni prikaz sa tabovima po barberu.
- Novi termini se u admin kalendaru pojavljuju odmah.
- Pokretna barber traka radi u kontinuitetu i sadržaj se menja iz admin panela (`FRESH FADE|MID FADE|...`).
- Admin > Uredi sajt: logo, hero fotografija, akcent boja, brend/kontakt, hero tekstovi, CTA, marquee, sekcijski naslovi, app tekst i footer.
- Upload logo slike, hero slike, barber fotografija i fade/galerija fotografija direktno sa telefona.
- Mobilni install banner je odmah na prvom ekranu sajta; PWA podrška za instalaciju na početni ekran.
- Poboljšano prelamanje velikih naslova da se slova ne preklapaju na telefonu.
- Ako je port 3000 zauzet, server automatski proba sledeći slobodan port.

## Napomena za PWA

Za pravu instalaciju na telefonu kada se sajt objavi online potreban je HTTPS (localhost radi i bez HTTPS-a u razvoju).
