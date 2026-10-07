# dsh-locale-fr

French locale pack for the [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness) interface.

Adds **Français** to the language selector in **Settings → General**, translating the full UI: **58 namespaces, 2614 keys**, with automatic fallback to English for any key not yet translated.

## Install

```sh
dsh plugin --profile web add dsh-locale-fr
```

Or from the in-app marketplace (**Settings → Plugin Market**): search for `dsh-locale-fr`.

## Activate

1. Reload the page (or restart the desktop app).
2. Open **Settings → General → Language**.
3. Select **Français**.

## What is translated

Every namespace registered with the Harness locale service at build time: chat, conversations, commands, settings (general, models, providers, plugins, permissions, schedules, workspaces…), sidebar panels (markdown, PDF, Office, images, code preview), jobs, plans, goals, subagents, skills, and common UI elements (buttons, dialogs, empty states).

Missing keys — for example after a Harness update adds new strings — automatically fall back to English, so the interface always stays usable.

## Known limitations

- Texts captured outside the slot-render at registration time (e.g. `/model` command descriptions) remain in their registration language — this is a documented limitation of the Harness locale service itself, not of this pack.
- The pack is generated from the English dictionaries bundled with the running Harness version. When a new Harness release adds keys, they appear in English until the pack is regenerated.

## How it works

The client module registers a `fr` locale with fallback to `en` via `ctx.locale.addLanguage({ id: 'fr', label: 'Français', fallback: 'en' })`, then contributes its dictionaries with `ctx.locale.register(namespace, 'fr', dict)` for each of the 58 namespaces. No patches to Harness source files — pure plugin protocol, survives Harness updates.

Note: `client.js` is a web-only module (loaded through `window.__ModuleLoader__`, not ESM `import`); the npm entry point `index.js` is intentionally a no-op.

## License

MIT

---

# dsh-locale-fr (Français)

Pack de langue française pour l'interface de [DeepSeek Harness](https://github.com/deepseek-ai/deepseek-harness).

Ajoute **Français** au sélecteur de langue dans **Réglages → Général**, avec traduction complète de l'interface : **58 espaces de noms, 2614 clés**, et repli automatique vers l'anglais pour toute clé non encore traduite.

## Installation

```sh
dsh plugin --profile web add dsh-locale-fr
```

Ou depuis le marché intégré (**Réglages → Plugin Market**) : cherchez `dsh-locale-fr`.

## Activation

1. Rechargez la page (ou redémarrez l'application de bureau).
2. Ouvrez **Réglages → Général → Langue**.
3. Sélectionnez **Français**.

## Limites connues

- Les textes capturés hors du rendu des slots au moment de l'enregistrement (par exemple les descriptions de la commande `/model`) restent dans leur langue d'origine — limitation documentée du service de locale de Harness, pas de ce pack.
- Après une mise à jour de Harness ajoutant de nouvelles clés, celles-ci s'affichent en anglais jusqu'à la régénération du pack.

## Fonctionnement

Le module client enregistre une locale `fr` (repli `en`) puis contribue ses dictionnaires pour chacun des 58 espaces de noms. Aucune modification des fichiers sources de Harness — protocole de plugin pur, compatible avec les mises à jour.

Note : `client.js` est un module web uniquement (chargé via `window.__ModuleLoader__`, pas par `import` ESM) ; le point d'entrée npm `index.js` est volontairement vide.

## Licence

MIT
