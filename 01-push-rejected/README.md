# ❌ Git Problèmes #1 : `git push` rejected (fetch first)

[![Regarder la vidéo](https://img.youtube.com/vi/8Lk0sc89Jp0/maxresdefault.jpg)](https://www.youtube.com/watch?v=8Lk0sc89Jp0)

📺 **Vidéo :** [Git push rejected (fetch first) : la solution en 3 minutes](https://www.youtube.com/watch?v=8Lk0sc89Jp0)

## L'erreur

```
To https://github.com/TON-PSEUDO/TON-DEPOT.git
 ! [rejected]        main -> main (fetch first)
error: failed to push some refs to 'https://github.com/TON-PSEUDO/TON-DEPOT.git'
hint: Updates were rejected because the remote contains work that you do
hint: not have locally.
```

| Mot | Signification |
|---|---|
| `rejected` | refusé |
| `fetch first` | récupère d'abord |
| `remote contains work…` | GitHub a des commits que tu n'as pas sur ton ordinateur |

## Pourquoi ça arrive

```
GitHub          A ── B          ← un commit B a été ajouté en ligne (collègue, README modifié sur le site…)
Ton ordinateur  A ── C          ← tu as fait un commit C de ton côté
```

Les deux historiques ont **divergé**. Si Git acceptait ton push, le commit **B serait écrasé**. Git refuse pour protéger ce travail.

## ✅ La solution

```bash
git pull --rebase    # récupère B, puis replace ton commit C par-dessus
git push             # cette fois, ça passe !
```

Résultat :

```
A ── B ── C   (une ligne droite, sur GitHub comme sur ton ordinateur)
```

Vérifier :

```bash
git log --oneline
```

## ⚠️ Et s'il y a un conflit ?

Si B et C modifient la même ligne, Git s'arrête :

```
CONFLICT (content): Merge conflict in index.html
```

1. Ouvre le fichier et garde la bonne version (supprime les lignes `<<<<<<<`, `=======`, `>>>>>>>`).
2. Puis :

```bash
git add .
git rebase --continue
```

Perdu ? Tout annuler et revenir comme avant :

```bash
git rebase --abort
```

## 🚫 Le piège à éviter

```bash
git push --force     # ❌ remplace l'historique de GitHub par le tien : le commit B est EFFACÉ
```

> Règle : **jamais `--force` sur une branche partagée**, surtout pas sur `main`.

## 💡 Ne plus jamais avoir l'erreur

1. `git pull` avant de commencer à travailler.
2. `git pull` avant chaque `git push`.
3. Astuce : faire du rebase le comportement par défaut de `git pull` :

```bash
git config --global pull.rebase true
```

---

⬅️ [Retour au sommaire](../README.md) · Prochain épisode : **Permission denied (publickey)**
