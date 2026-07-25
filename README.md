# EBOK Stats 📊🏀

> **La saisie et l'analyse de statistiques, du live scoring au bilan de saison.**
> Repo réservé — le développement n'a pas encore commencé.

## Stack prévue (standard de la galaxie)

- **Next.js** (App Router) déployé sur **Vercel** — sous-domaine `stats.ebok.fr`
- **Clerk** pour le compte unique EBOK (voir `docs/AUTH.md` du repo
  [EBOK-BASKETBALL](https://github.com/marleyebok/EBOK-BASKETBALL))
- **Neon Postgres**, schéma `stats` + référence à la table partagée `shared.users`
- Barre commune `ebok-galaxy.js` en haut de page, comme sur toutes les apps

## ⚠️ Compte unique EBOK (Clerk) — à faire dès la création de l'app

Ne pas repartir sur un système d'auth maison : cette app doit se connecter
dès le départ à l'instance Clerk **partagée** de la galaxie (compte unique
« 1 compte, 10 outils », domaine `clerk.ebok.fr`). Reprendre le schéma déjà
en place sur **EBOK-WORKOUT** et **EBOK-MEDIAS** :

- `@clerk/nextjs`, `<ClerkProvider>` avec la clé publiable de la galaxie en
  repli (`pk_live_Y2xlcmsuZWJvay5mciQ`, publique — pas de risque à la coder en dur).
- Middleware `clerkMiddleware` en repli silencieux (fail-open) tant que
  `CLERK_SECRET_KEY` n'est pas configurée, pour ne jamais casser le site public.
- Admin = allowlist d'e-mails Clerk (`ADMIN_EMAILS`), `marley.ebok@gmail.com`
  admin d'office — voir `lib/admin.ts` sur EBOK-WORKOUT / EBOK-MEDIAS.
- Détail complet du plan : `docs/AUTH.md` du repo
  [EBOK-BASKETBALL](https://github.com/marleyebok/EBOK-BASKETBALL).

## Statut

🟡 **Bientôt** — repo créé pour réserver la place dans la galaxie.
Le développement n'a pas encore commencé.
