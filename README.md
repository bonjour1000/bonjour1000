# 📊 GitHub Metrics Generator

Ce repository génère automatiquement mes statistiques GitHub.

---

<table>
  <tr>
    <td width="50%" valign="top">
      
## 📈 Statistiques principales

![GitHub Metrics](github-metrics.svg)

    </td>
    <td width="50%" valign="top">
      
## 🕐 Habitudes de codage

![Habits Charts](metrics.plugin.habits.charts.svg)

    </td>
  </tr>
</table>

---

## 🔌 Plugins inclus

### Métriques principales (`github-metrics.svg`)
- 📅 **Isocalendar** - Calendrier annuel de contributions
- 💻 **Languages** - Analyse des langages utilisés
- 📏 **Lines** - Lignes de code par repository

### Habitudes de codage (`metrics.plugin.habits.charts.svg`)
- 🕐 **Recent activity charts** - Graphiques d'activité récente
  - Heures de commit par heure du jour
  - Commits par jour de la semaine
  - Habitudes de codage des 14 derniers jours

---

## 🔄 Mise à jour automatique

Les statistiques sont automatiquement mises à jour :
- ✅ **Toutes les 6 heures**
- ✅ **À chaque push**
- ✅ **Manuellement** via Actions

---

## 🎨 Thèmes alternatifs

Pour tester différents styles visuels, utilisez le workflow `test-theme.yml` :

<details>
<summary>🌙 Dark Mode</summary>

![Dark Theme](github-metrics-dark.svg)

</details>

<details>
<summary>🌈 Colorful</summary>

![Colorful Theme](github-metrics-colorful.svg)

</details>

---

## ⚙️ Configuration

### Workflows actifs

1. **`metrics.yml`** - Métriques principales (toutes les 6h)
2. **`habits-charts.yml`** - Graphiques d'habitudes (toutes les 6h)
3. **`test-theme.yml`** - Test de thèmes (manuel)

### Personnalisation

Pour modifier les plugins ou les options, éditez les fichiers de workflow.

**Exemples :**

```yaml
# Changer la période d'analyse des habitudes
plugin_habits_days: 30  # Au lieu de 14

# Changer le type de graphique
plugin_habits_charts_type: graph  # Au lieu de classic

# Augmenter le nombre d'événements analysés
plugin_habits_from: 500  # Au lieu de 200
```

---

## 📚 Documentation

- [Plugin Habits](https://github.com/lowlighter/metrics/blob/v3.34/source/plugins/habits/README.md) - Documentation complète des habitudes de codage
- [Documentation Metrics](https://github.com/lowlighter/metrics) - Documentation officielle
- [Liste des plugins](https://github.com/lowlighter/metrics#-plugins) - Tous les plugins disponibles

---

## 🛠️ Technologies

- [lowlighter/metrics](https://github.com/lowlighter/metrics) - Générateur de métriques GitHub
- GitHub Actions - Automatisation
- SVG - Format de sortie

---

<div align="center">

**⏰ Dernière mise à jour automatique :** Toutes les 6 heures

**🔧 Propulsé par** [GitHub Actions](https://github.com/features/actions)

</div>
