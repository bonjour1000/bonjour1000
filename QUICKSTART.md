# 🚀 Guide de Démarrage Rapide

Ce guide vous aidera à mettre en place vos métriques GitHub en quelques minutes !

## ⏱️ En 5 minutes chrono

### Étape 1️⃣ : Créer votre token (2 minutes)

1. **Allez sur** : https://github.com/settings/tokens/new
2. **Donnez un nom** : `Metrics Token`
3. **Expiration** : Choisissez "No expiration" ou "1 year"
4. **Cochez ces permissions** :
   ```
   ✅ repo
   ✅ read:org
   ✅ read:user
   ✅ read:packages
   ✅ read:project
   ✅ read:discussion
   ```
5. **Cliquez** sur "Generate token"
6. **COPIEZ** le token (vous ne le reverrez plus !)

### Étape 2️⃣ : Ajouter le secret (1 minute)

1. Allez dans votre repo `bonjour1000`
2. **Settings** → **Secrets and variables** → **Actions**
3. Cliquez **"New repository secret"**
4. Nom : `METRICS_TOKEN`
5. Valeur : Collez votre token
6. **"Add secret"**

### Étape 3️⃣ : Activer les workflows (30 secondes)

1. Onglet **Actions** de votre repo
2. Cliquez sur **"I understand my workflows, go ahead and enable them"**
3. Cliquez sur **"Metrics"** dans la liste à gauche
4. Cliquez sur **"Run workflow"** → **"Run workflow"**

### Étape 4️⃣ : Attendre (2-3 minutes)

⏳ Le workflow va s'exécuter et générer vos métriques.
- Vous pouvez suivre la progression en temps réel dans l'onglet Actions

### Étape 5️⃣ : Vérifier (30 secondes)

✅ Une fois terminé, vos fichiers SVG apparaîtront dans le repository :
- `github-metrics.svg`
- Et d'autres si vous avez lancé le workflow étendu

## 🎨 Ajouter à votre profil GitHub

### Option A : Repository de profil existant

Si vous avez déjà un repository avec votre username :

1. Ouvrez le `README.md` de ce repository
2. Ajoutez cette ligne où vous voulez afficher vos métriques :

```markdown
![GitHub Metrics](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/github-metrics.svg)
```

### Option B : Créer un nouveau repository de profil

1. Créez un **nouveau repository** avec le **même nom que votre username**
   - Par exemple, si votre username est `john`, créez un repo nommé `john`
2. Cochez **"Add a README file"**
3. Rendez le repository **public**
4. Ouvrez le `README.md` et ajoutez vos métriques

## 💡 Exemples de README

### Minimaliste

```markdown
# 👋 Salut, je suis [Votre Nom]

![Metrics](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/github-metrics.svg)
```

### Complet avec sections

```markdown
# 👋 Bonjour, je suis [Votre Nom] !

## 🚀 Développeur passionné

### 📊 Mes statistiques GitHub

![Metrics](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/github-metrics.svg)

<details>
<summary>📈 Plus de statistiques</summary>

### 📅 Calendrier de contributions
![Isocalendar](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/metrics-isocalendar.svg)

### 🕐 Mes habitudes de codage
![Habits](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/metrics-habits.svg)

### 💻 Langages que j'utilise
![Languages](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/metrics-languages.svg)

</details>

### 🛠️ Technologies

- 💻 Je code principalement en...
- 🌱 J'apprends actuellement...
- 👯 Je cherche à collaborer sur...

### 📫 Me contacter

- 🐦 Twitter: [@votre_twitter](https://twitter.com/votre_twitter)
- 💼 LinkedIn: [votre-profile](https://linkedin.com/in/votre-profile)
- 📧 Email: votre.email@example.com
```

### Avec style et emojis 🎨

```markdown
<div align="center">
  
# 👨‍💻 [Votre Nom]

### Développeur Full Stack | Open Source Enthusiast | Tech Lover

[![GitHub](https://img.shields.io/github/followers/VOTRE_USERNAME?label=Follow&style=social)](https://github.com/VOTRE_USERNAME)
[![Twitter](https://img.shields.io/twitter/follow/VOTRE_TWITTER?style=social)](https://twitter.com/VOTRE_TWITTER)

---

## 📊 GitHub Analytics

![Metrics](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/github-metrics.svg)

---

## 🔥 Contribution Streak

![Isocalendar](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/metrics-isocalendar.svg)

---

## 🕐 Coding Habits

![Habits](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/metrics-habits.svg)

---

## 💻 Tech Stack

![Languages](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/metrics-languages.svg)

</div>
```

## 🔄 Mettre à jour manuellement

Si vous voulez forcer une mise à jour de vos métriques :

1. Allez dans **Actions**
2. Cliquez sur **"Metrics"** (ou **"Metrics Extended"**)
3. Cliquez sur **"Run workflow"**
4. Sélectionnez la branche `main`
5. Cliquez sur **"Run workflow"**

## ⚡ Configuration rapide des workflows

### Mise à jour plus fréquente

Éditez `.github/workflows/metrics.yml` :

```yaml
schedule:
  - cron: "0 */3 * * *"  # Toutes les 3 heures (au lieu de 6)
```

### Mise à jour moins fréquente

```yaml
schedule:
  - cron: "0 0 * * *"  # Une fois par jour
```

### Désactiver les mises à jour automatiques

Supprimez ou commentez la section `schedule` :

```yaml
# schedule:
#   - cron: "0 */6 * * *"
```

Vous pourrez toujours lancer les workflows manuellement !

## 🎯 Prochaines étapes

Une fois vos métriques configurées :

1. ✅ Personnalisez les plugins selon vos préférences
2. ✅ Ajustez les couleurs et le style (voir README.md)
3. ✅ Explorez les autres plugins disponibles
4. ✅ Partagez votre profil !

## 🆘 Besoin d'aide ?

- 📖 Consultez le [README.md](README.md) complet
- 🐛 Un problème ? Vérifiez l'onglet **Actions** pour voir les logs
- 💬 Consultez la [documentation officielle](https://github.com/lowlighter/metrics)

---

**Astuce** : Les métriques se mettent à jour automatiquement, mais GitHub peut mettre en cache les images. Si vous ne voyez pas les changements immédiatement, videz le cache de votre navigateur ou ajoutez `?dummy=value` à la fin de l'URL de l'image.

**Exemple** :
```markdown
![Metrics](https://raw.githubusercontent.com/VOTRE_USERNAME/bonjour1000/main/github-metrics.svg?v=1)
```

Changez `v=1` en `v=2`, `v=3`, etc. pour forcer le rechargement !

