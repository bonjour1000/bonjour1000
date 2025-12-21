# 🧪 Guide de Test des Workflows

## ✅ Étapes dans l'ordre

### 1️⃣ Push vos fichiers sur GitHub (MAINTENANT)

```bash
git add .
git commit -m "Configuration complète GitHub Metrics avec documentation"
git push origin main
```

**C'est OK de push maintenant !** Les workflows ne s'exécuteront pas automatiquement sans le token.

---

### 2️⃣ Créer votre token GitHub (5 minutes)

1. **Allez sur :** https://github.com/settings/tokens/new

2. **Configuration du token :**
   - **Note :** `Metrics Token`
   - **Expiration :** `No expiration` (ou `1 year`)
   
3. **Sélectionnez ces scopes :**
   ```
   ✅ repo (Full control of private repositories)
   ✅ read:org (Read org and team membership, read org projects)
   ✅ read:user (Read ALL user profile data)
   ✅ read:packages (Download packages from GitHub Package Registry)
   ✅ read:project (Read access to projects)
   ✅ read:discussion (Read team discussions)
   ```

4. **Générez et COPIEZ le token** ⚠️ Vous ne pourrez plus le voir après !

---

### 3️⃣ Ajouter le secret au repository (2 minutes)

1. Allez sur : `https://github.com/VOTRE_USERNAME/bonjour1000`

2. Cliquez sur **Settings** (⚙️ en haut)

3. Dans le menu gauche : **Secrets and variables** → **Actions**

4. Cliquez sur **"New repository secret"** (bouton vert)

5. Remplissez :
   - **Name :** `METRICS_TOKEN`
   - **Secret :** Collez votre token
   
6. Cliquez sur **"Add secret"**

✅ **Le secret est maintenant configuré !**

---

### 4️⃣ Activer GitHub Actions (30 secondes)

1. Allez dans l'onglet **Actions** de votre repository

2. Si c'est la première fois, GitHub affiche un avertissement de sécurité

3. Cliquez sur **"I understand my workflows, go ahead and enable them"**

✅ **Les workflows sont maintenant activés !**

---

## 🧪 Tester les workflows

### Option A : Workflow principal (RECOMMANDÉ POUR COMMENCER)

**Fichier :** `metrics.yml`

**Comment lancer :**

1. Onglet **Actions**
2. Dans la liste à gauche, cliquez sur **"Metrics"**
3. Cliquez sur **"Run workflow"** (bouton bleu à droite)
4. Branch : `main` (déjà sélectionné)
5. Cliquez sur le bouton vert **"Run workflow"**

**Temps d'exécution :** ~2-3 minutes

**Fichier généré :** `github-metrics.svg`

**Ce qui sera testé :**
- ✅ Toutes les statistiques de base
- ✅ 15+ plugins (isocalendar, languages, habits, etc.)
- ✅ Repos privés et publics
- ✅ Mise à jour automatique configurée (toutes les 6h)

---

### Option B : Workflows étendus (APRÈS LE TEST DU PRINCIPAL)

**Fichier :** `metrics-extended.yml`

**Comment lancer :**

1. Onglet **Actions**
2. Cliquez sur **"Metrics Extended (Statistiques avancées)"**
3. **"Run workflow"** → **"Run workflow"**

**Temps d'exécution :** ~5-8 minutes (génère 7 fichiers)

**Fichiers générés :**
- `github-metrics-extended.svg`
- `metrics-isocalendar.svg`
- `metrics-habits.svg`
- `metrics-languages.svg`
- `metrics-activity.svg`
- `metrics-notable.svg`
- `metrics-repositories.svg`

---

### Option C : Tester les thèmes (OPTIONNEL)

**Fichier :** `metrics-themes.yml`

**Comment lancer :**

1. Onglet **Actions**
2. Cliquez sur **"Metrics with Themes (Thèmes personnalisés)"**
3. **"Run workflow"**
4. **⚠️ Important :** Sélectionnez un thème dans le menu déroulant :
   - `default`
   - `dark`
   - `terminal`
   - `github-dark`

5. **"Run workflow"**

**Temps d'exécution :** ~2-3 minutes par thème

**Exemple de fichier généré :** `github-metrics-dark.svg`

---

## 📊 Suivre l'exécution en temps réel

Après avoir lancé un workflow :

1. Restez dans l'onglet **Actions**
2. Vous verrez une ligne jaune 🟡 avec le nom du workflow
3. Cliquez dessus pour voir les détails
4. Cliquez sur le job (ex: "github-metrics")
5. Vous verrez les logs en temps réel !

**États possibles :**
- 🟡 **Jaune (en cours)** : Le workflow s'exécute
- ✅ **Vert (success)** : Terminé avec succès !
- ❌ **Rouge (failed)** : Erreur (voir les logs)

---

## ✅ Vérifier que ça a fonctionné

### Méthode 1 : Vérifier les fichiers

1. Retournez à la racine de votre repository
2. Vous devriez voir les nouveaux fichiers `.svg` apparaître
3. Cliquez sur un fichier SVG pour le prévisualiser

### Méthode 2 : Vérifier les commits

1. Allez dans l'onglet **Code**
2. Vous verrez des commits automatiques :
   ```
   Update github-metrics.svg - [Skip GitHub Action]
   ```

### Méthode 3 : URL directe

Ouvrez cette URL dans votre navigateur :
```
https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/github-metrics.svg
```

(Remplacez `VOTRE_USERNAME` par votre vrai username)

---

## 🎯 Ordre de test recommandé

### Test 1 : Workflow principal (COMMENCEZ ICI)
```
1. Push vos fichiers ✅
2. Créer le token ✅
3. Ajouter le secret ✅
4. Activer Actions ✅
5. Lancer "Metrics" ✅
6. Attendre 2-3 min ⏳
7. Vérifier github-metrics.svg ✅
```

**Si ça fonctionne :** Passez au test 2

**Si ça échoue :** Consultez la section "Dépannage" ci-dessous

---

### Test 2 : Workflow étendu (OPTIONNEL)
```
1. Lancer "Metrics Extended" ✅
2. Attendre 5-8 min ⏳
3. Vérifier les 7 fichiers SVG ✅
```

---

### Test 3 : Thème (OPTIONNEL)
```
1. Lancer "Metrics with Themes" ✅
2. Choisir "dark" dans le menu ✅
3. Attendre 2-3 min ⏳
4. Vérifier github-metrics-dark.svg ✅
```

---

## 🔧 Dépannage

### ❌ Erreur : "Resource not accessible by integration"

**Cause :** Le secret `METRICS_TOKEN` n'est pas configuré ou invalide

**Solution :**
1. Vérifiez que le secret est bien nommé `METRICS_TOKEN` (exact)
2. Vérifiez que le token a toutes les permissions requises
3. Générez un nouveau token si nécessaire

---

### ❌ Erreur : "Bad credentials"

**Cause :** Le token est invalide ou expiré

**Solution :**
1. Générez un nouveau token
2. Mettez à jour le secret `METRICS_TOKEN`
3. Relancez le workflow

---

### ❌ Le workflow ne démarre pas

**Cause :** GitHub Actions n'est pas activé

**Solution :**
1. Onglet **Actions**
2. Cliquez sur "I understand my workflows..."

---

### ⚠️ Avertissement : "Context access might be invalid"

**C'est NORMAL !** Ces avertissements apparaissent avant d'ajouter le secret.

Une fois le secret ajouté, le workflow fonctionnera correctement.

---

### ⏱️ Le workflow prend trop de temps

**Normal pour la première fois !** Les workflows peuvent prendre :
- `metrics.yml` : 2-3 minutes
- `metrics-extended.yml` : 5-8 minutes (7 jobs)
- `metrics-themes.yml` : 2-3 minutes

**Si ça prend plus de 10 minutes :**
1. Vérifiez qu'il n'y a pas d'erreur dans les logs
2. Annulez et relancez

---

### 📊 Le fichier SVG est vide ou cassé

**Causes possibles :**
1. Le workflow n'est pas terminé
2. Il y a eu une erreur dans le workflow
3. Les permissions du token sont insuffisantes

**Solution :**
1. Vérifiez les logs du workflow
2. Assurez-vous que le workflow est terminé (✅ vert)
3. Vérifiez les permissions du token

---

## 💡 Conseils pour les tests

### 1. Testez un workflow à la fois
Ne lancez pas les 3 workflows en même temps la première fois.

### 2. Attendez la fin complète
Ne relancez pas un workflow s'il est déjà en cours.

### 3. Consultez toujours les logs
En cas d'erreur, les logs vous diront exactement ce qui ne va pas.

### 4. Commencez simple
Testez d'abord `metrics.yml` avant les autres.

### 5. Soyez patient
La première exécution peut prendre du temps.

---

## 🎨 Après le premier test réussi

Une fois que `metrics.yml` fonctionne :

### 1. Mettez à jour votre README de profil

Créez un repository avec le même nom que votre username, puis ajoutez :

```markdown
# 👋 Salut, je suis [Votre Nom] !

![GitHub Metrics](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/github-metrics.svg)
```

### 2. Testez les autres workflows

Si vous voulez les métriques séparées :
- Lancez `metrics-extended.yml`

Si vous voulez tester des thèmes :
- Lancez `metrics-themes.yml` avec différents thèmes

### 3. Personnalisez

Modifiez les workflows selon vos besoins :
- Changez la fréquence de mise à jour
- Activez/désactivez des plugins
- Changez les couleurs et le style

---

## 📋 Checklist de test complète

### Avant de lancer
- [ ] Fichiers pushés sur GitHub
- [ ] Token créé avec toutes les permissions
- [ ] Secret `METRICS_TOKEN` ajouté
- [ ] GitHub Actions activé

### Test du workflow principal
- [ ] Workflow "Metrics" lancé
- [ ] Workflow terminé avec succès (✅)
- [ ] Fichier `github-metrics.svg` présent
- [ ] Fichier visible et correct

### Tests optionnels
- [ ] Workflow "Metrics Extended" testé
- [ ] 7 fichiers SVG générés
- [ ] Workflow "Metrics with Themes" testé
- [ ] Thème appliqué correctement

### Finalisation
- [ ] README de profil créé/mis à jour
- [ ] Métriques visibles sur le profil
- [ ] Mise à jour automatique configurée

---

## 🚀 Commandes Git pour push

### Option 1 : Push simple
```bash
git add .
git commit -m "✨ Configuration GitHub Metrics avec documentation complète"
git push origin main
```

### Option 2 : Push avec vérification
```bash
# Voir ce qui a changé
git status

# Ajouter tous les fichiers
git add .

# Voir ce qui sera commité
git status

# Commit
git commit -m "✨ Configuration GitHub Metrics

- Ajout de 3 workflows (metrics, extended, themes)
- Documentation complète (README, guides)
- 15+ plugins configurés
- Support repos privés et publics
- Mise à jour automatique toutes les 6h"

# Push
git push origin main
```

### Option 3 : Push avec branches (avancé)
```bash
# Créer une branche de test
git checkout -b setup-metrics

# Ajouter et commit
git add .
git commit -m "✨ Configuration GitHub Metrics"

# Push la branche
git push origin setup-metrics

# Ensuite sur GitHub : créer une Pull Request pour merger dans main
```

---

## ⏭️ Après le push

1. **Allez sur GitHub :** `github.com/VOTRE_USERNAME/bonjour1000`

2. **Vérifiez les fichiers :** Tous les fichiers doivent être présents

3. **Onglet Actions :** Vous verrez les workflows disponibles

4. **Ajoutez le secret :** `METRICS_TOKEN`

5. **Lancez votre premier test !** 🚀

---

## 📞 Besoin d'aide ?

Si quelque chose ne fonctionne pas :

1. ✅ Vérifiez cette checklist
2. 📖 Consultez les logs dans Actions
3. 🔍 Regardez la section dépannage du README.md
4. 📚 Consultez la [documentation officielle](https://github.com/lowlighter/metrics)

---

## 🎉 Récapitulatif express

```
1. git push origin main                    ← Faites ça MAINTENANT
2. Créer le token sur GitHub              ← 5 minutes
3. Ajouter le secret METRICS_TOKEN        ← 2 minutes
4. Actions > Metrics > Run workflow       ← 1 clic
5. Attendre 2-3 minutes                   ← ☕
6. Admirer vos métriques !                ← 🎉
```

---

**Vous êtes prêt à push et tester ! Bonne chance ! 🚀**

