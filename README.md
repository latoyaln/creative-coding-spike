# WOGO
Welkom bij de WOGO Website, een website gebouwd met SvelteKit en Contentful. WOGO biedt een dynamisch platform voor cocktailbars en sterke drank merken, met functies zoals, ticketverkoop voor cocktail walks en informatie over samenwerkingen.

## Inhoud

### [Kenmerken](https://github.com/Seijno/wogo?tab=readme-ov-file#kenmerken)
### [Preview ](https://github.com/Seijno/wogo?tab=readme-ov-file#preview)
### [Live pagina](https://github.com/Seijno/wogo?tab=readme-ov-file#live-pagina)
### [Gebruikersaanwijzing](https://github.com/Seijno/wogo?tab=readme-ov-file#gebruikersaanwijzing-1)
### [Huisstijl](https://github.com/Seijno/wogo?tab=readme-ov-file#huisstijl-1)
### [Bronnen](https://github.com/Seijno/wogo?tab=readme-ov-file#bronnen-1)
### [Installatie](https://github.com/Seijno/wogo?tab=readme-ov-file#installatie-1)


## Kenmerken
🖋 WOGO Huisstijl: De site is opgezet met de aangeleverde WOGO Huisstijl. 

🏠 Homepagina: De gebruiker komt terecht op de homepage. Hier ziet je een overzicht van hoe WOGO werkt, wat WOGO doet en kan je ook de cocktail walks exploren. Ook zie je reviews van mensen die eerder een WOGO cocktail ervaring hebben gekocht. 

🚶🏽‍♀️Route Pagina: Bij de Rotterdam Route pagina is meer detail te vinden over wat je eigenlijk koopt. Er is te lezen dat je 3 barren bezoekt, cocktails inclusief zijn en meer over de boeking.

🛠SvelteKit & Contentful: De website is gebouwd met SvelteKit en haalt de data dynamisch op via de Contentful API.

------------------------------------------------------------------------------------------------------------------
## Preview
![Schermafbeelding 2024-10-09 om 7 37 17 AM](https://github.com/user-attachments/assets/47271912-3dd8-4516-8c91-b490b0b8c2dc)

------------------------------------------------------------------------------------------------------------------


## Live pagina

Bekijk de live pagina [hier](wogohva.netlify.app/home)

<img src="https://github.com/user-attachments/assets/85259dab-f723-4358-a147-0b0d545b0bff" width=800 height=400>


## Gebruikersaanwijzing
### Navigeren door de pagina
Homepagina:
- De gebruiker begint op de homepagina, hier kan je naar beneden scrollen om de what we do en how it works te bekijken.

Navigatie:
- De gebruiker gaat via de navigatie naar de rotterdam tickets pagina.

Rotterdam tickets:
- Na dat er is geklikt op Rotterdam tickets ziet de gebruiker nu een banner over de rotterdam walks. Ook ziet de gebruiker kaarten met details over wat je precies krijgt.

## Huisstijl

Wij hebben van WOGO kleuren en fonts gehad waar wij mee kunnen werken. 

Dit gaat om de fonts Lulo Clean One en Brandon Grotesque.

Hoe wij deze gebruiken/ toepassen in het project is te lezen in onze wiki onder [Conventies](https://github.com/Seijno/wogo/wiki/Conventies)

### Animaties
Zowel de homepage als rotterdam ticket page bevatten animaties. Bij de hero komt de tekst van links in beeld naar rechts. Voor de kaarten van How it Works (homepage) komen de kaarten tevoorschijn zodra je scrollt.

## Bronnen
Hier vind je de bronnen van de tools die we hebben gebruikt. 

#### [Sveltekit](https://kit.svelte.dev/) - Voor het bouwen van de site

#### [Svelte Docs](https://svelte.dev/docs/special-elements#svelte-component) - Over het dynamisch maken van de site

#### [Vercel Docs](https://vercel.com/docs/frameworks/sveltekit) - Voor het live zetten van de site

#### [Contentful](https://www.contentful.com) - Voor het ophalen van de data

#### [Atomic Web Design](https://bradfrost.com/blog/post/atomic-web-design/) - Werken met atoms, molecules, organisms

## Installatie
Instructies voor het lokaal opzetten van de squadpage, zodat ontwikkelaars het project kunnen downloaden, installeren en zelf kunnen draaien met behulp van SvelteKit.

*1. Vereisten*

Zorg ervoor dat je de volgende software hebt geïnstalleerd:

- Node.js
- Packetmanager zoals npm of yarn

Ook heb je voor dit project een .env file nodig. Bekijk onze .env.example wat hier in komt te staan

*2. git repository clonen*

Je kunt op de main pagina de repo clonen en je eigen lokale versie opvragen.

*3. SvelteKit en packets installeren*

Om aan het project te werken, moet je eerst een nieuw SvelteKit-project opzetten. Dit kan eenvoudig gedaan worden met create-svelte.

Open je terminal.
Voer ```npm install``` of ```yarn install``` uit om de juiste packets te installeren om aan het project te werken.

*4. Deployen op vercel*

Op [vercel.com](https://vercel.com/docs/frameworks/sveltekit) kun je verder op weg met het deployen van een svelteproject. 

