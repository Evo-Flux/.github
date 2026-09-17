# Evoflux

Intégrateur **Sage 100** et éditeur de logiciels, à Chartres.

Nos applications métier prolongent Sage 100 là où il s'arrête : la logistique
d'entrepôt, la livraison sur le terrain, la production, la gestion interne. Elles
sont écrites en **.NET** (ASP.NET Core, Blazor, MAUI) et en **TypeScript**
(Next.js), et partagent un socle commun — une librairie de briques et un design
system — plutôt que de recopier le même code d'un dépôt à l'autre.

---

## Les applications

| Dépôt | Ce que c'est | Stack |
| --- | --- | --- |
| [**EvoStock**](https://github.com/Evo-Flux/EvoStock) | WMS — gestion d'entrepôt intégrée à Sage 100 : client mobile/tablette, interface PC de supervision, API REST + SignalR temps réel, génération d'étiquettes | .NET 10 · MAUI Blazor · ASP.NET Core · Blazor WASM · FastAPI |
| [**EvoTrack**](https://github.com/Evo-Flux/EvoTrack) | Gestion de livraisons et WMS terrain, intégrée à Sage 100c : tournées, optimisation d'itinéraires (OSRM), preuves de livraison, app cross-platform et installeur MSI signé | .NET 9 · MAUI Blazor · ASP.NET Core (x86, COM Sage) · SQL Server |
| [**EvoProd**](https://github.com/Evo-Flux/EvoProd) | Suivi de production | .NET 10 · Blazor WASM · ASP.NET Core · Tailwind v4 |
| [**EvoConges**](https://github.com/Evo-Flux/EvoConges) | Gestion des congés en interne : règles de décompte, 2FA, déploiement conteneurisé | .NET 10 · Blazor WASM · ASP.NET Core · PostgreSQL |
| [**DevalidationFacturesEtAutres**](https://github.com/Evo-Flux/DevalidationFacturesEtAutres) | Dévalidation de documents Sage (factures et autres pièces) | .NET 10 · Blazor WASM · ASP.NET Core |
| [**OutilBaptiste**](https://github.com/Evo-Flux/OutilBaptiste) | Outillage interne de test : manipulation rapide des préparations et bons de livraison Sage, sans passer par l'interface Sage | .NET 10 · Blazor WASM · ASP.NET Core |
| [**EvoCRM**](https://github.com/Evo-Flux/EvoCRM) | CRM — amorçage | à venir |
| [**Website**](https://github.com/Evo-Flux/Website) | Site vitrine [www.evo-flux.fr](https://www.evo-flux.fr) et son backoffice d'édition de contenu | Next.js 15 · React 19 · TypeScript · Prisma · PostgreSQL |

## Le socle commun

| Dépôt | Rôle |
| --- | --- |
| [**EvofluxLibrary**](https://github.com/Evo-Flux/EvofluxLibrary) | Les briques partagées, publiées en packages NuGet sur GitHub Packages : `Evoflux.Core`, `.Data`, `.Logging`, `.Http`, `.AspNetCore`, `.Components` (Blazor), `.Realtime` (SignalR). Ce qui était recopié d'un projet à l'autre vit désormais à un seul endroit, versionné et testé. |
| [**EvoUI**](https://github.com/Evo-Flux/EvoUI) | Le design system : palette officielle, classes utilitaires, états de formulaire, mode sombre. |

La palette, issue du logo :

`#156584` · `#2F316F` · `#264B7A` · `#58A6AF` · `#9CCDD0`

## Comment nous travaillons

- **Une direction de dépendance unique** dans les applications : front et back
  partagent leurs contrats via une librairie qui, elle, ne référence rien.
- **Des versions portées par les tags**, un `CHANGELOG.md` au format
  [Keep a Changelog](https://keepachangelog.com/fr/1.1.0/), du versionnage
  sémantique.
- **Sage 100 en COM et SQL** : les lectures passent par SQL, les écritures par
  l'API COM officielle — jamais l'inverse.
- **Tests** en xUnit (+ bUnit côté composants), CI GitHub Actions.
- **Documentation en français**, README d'onboarding et `CLAUDE.md` pour le
  détail technique.

## Consommer nos packages

Les packages `Evoflux.*` sont publiés sur GitHub Packages. Une fois par poste :

```bash
dotnet nuget add source https://nuget.pkg.github.com/Evo-Flux/index.json \
  --name evoflux --username <compte-github> --password <PAT read:packages> \
  --store-password-in-clear-text
```

---

<sub>Les dépôts sont privés sauf mention contraire. Pour toute demande :
[evo-flux.fr](https://www.evo-flux.fr)</sub>
