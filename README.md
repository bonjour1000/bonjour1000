# 📊 GitHub Metrics Generator

Ce repository génère automatiquement mes statistiques GitHub.

---

## 📈 Mes Statistiques

![GitHub Metrics](github-metrics.svg)

---

## 🔄 Mise à jour automatique

Les statistiques sont automatiquement mises à jour :
- ✅ **Toutes les 6 heures**
- ✅ **À chaque push**
- ✅ **Manuellement** via Actions

---

## 🔌 Plugins inclus

- 📅 **Isocalendar** - Calendrier annuel de contributions
- 💻 **Languages** - Analyse des langages utilisés
- 🕐 **Habits** - Habitudes de codage
- ⭐ **Notable** - Contributions remarquables
- 🎯 **Activity** - Activité récente
- 💬 **Discussions** - Participation aux discussions
- 🏷️ **Topics** - Sujets d'intérêt
- ⭐ **Stars** - Repositories étoilés
- 📊 **Stargazers** - Évolution des stars
- 👥 **People** - Followers et following
- 💖 **Reactions** - Réactions sur mes contenus
- 📋 **Follow-up** - Suivi des issues et PRs
- 📏 **Lines** - Lignes de code
- 📈 **Traffic** - Statistiques de trafic

---

## ⚙️ Configuration

Le workflow est configuré dans `.github/workflows/blank.yml`

### Personnalisation

Pour modifier les plugins ou les options, éditez le fichier de workflow.

**Exemples :**

```yaml
# Changer la fréquence de mise à jour
schedule: [{cron: "0 */12 * * *"}]  # Toutes les 12h

# Modifier le nombre de langages affichés
plugin_languages_limit: 12

# Désactiver un plugin
plugin_habits: no
```

---

## 🎨 Thèmes alternatifs

Pour tester différents styles visuels, utilisez le workflow `test-theme.yml` :

1. Allez dans **Actions**
2. Cliquez sur **"Test Theme"**
3. Sélectionnez un thème :
   - 🌙 **Dark** - Mode sombre
   - 💻 **Terminal** - Style console
   - 📦 **Compact** - Version minimaliste
   - 🌈 **Colorful** - Coloré

---

## 🛠️ Technologies

- [lowlighter/metrics](https://github.com/lowlighter/metrics) - Générateur de métriques GitHub
- GitHub Actions - Automatisation
- SVG - Format de sortie

---

## 📝 Licence

Utilise [lowlighter/metrics](https://github.com/lowlighter/metrics) sous licence MIT.

---

<div align="center">

**⏰ Dernière mise à jour automatique :** Toutes les 6 heures

**🔧 Propulsé par** [GitHub Actions](https://github.com/features/actions)

</div>
