# 📊 GitHub Metrics Generator

Ce repository génère automatiquement mes statistiques GitHub.

---

<img align="left" src="/left-metrics.svg" alt="Métriques principales" width="47%" />

<p align="right">
<img src="/right-metrics.svg" alt="Habitudes de codage" width="47%" />
</p>

<br clear="both" />

---

## 🔌 Plugins inclus

### Métriques principales (`left-metrics.svg`)
- 📅 **Isocalendar** - Calendrier annuel de contributions
- 💻 **Languages** - Analyse des langages utilisés
- 📏 **Lines** - Lignes de code par repository
- 🎯 **Activity** - Activité récente
- 👥 **Community** - Statistiques communautaires

### Habitudes de codage (`right-metrics.svg`)
- 🕐 **Recent activity charts** - Graphiques d'activité récente
  - Heures de commit par heure du jour
  - Commits par jour de la semaine
  - Habitudes de codage des 30 derniers jours (1000 événements)

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
   - Génère : `left-metrics.svg`
   
2. **`habits-charts.yml`** - Graphiques d'habitudes (toutes les 6h)
   - Génère : `right-metrics.svg`
   
3. **`test-theme.yml`** - Test de thèmes (manuel)

### Personnalisation

Pour modifier les plugins ou les options, éditez les fichiers de workflow.

**Exemples :**

```yaml
# Changer la période d'analyse des habitudes
plugin_habits_days: 30  # 30 jours

# Changer le type de graphique
plugin_habits_charts_type: graph  # Style SVG smooth

# Augmenter le nombre d'événements analysés
plugin_habits_from: 1000  # 1000 événements
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
