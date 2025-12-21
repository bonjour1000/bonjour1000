# ⚙️ Configuration Avancée - GitHub Metrics

Ce guide couvre les configurations avancées pour personnaliser vos métriques GitHub au maximum.

## 📋 Table des matières

1. [Filtrage des repositories](#-filtrage-des-repositories)
2. [Optimisation des performances](#-optimisation-des-performances)
3. [Gestion des tokens](#-gestion-des-tokens)
4. [Configuration par plugin](#-configuration-par-plugin)
5. [Intégration avec d'autres services](#-intégration-avec-dautres-services)
6. [Scripts personnalisés](#-scripts-personnalisés)

---

## 🎯 Filtrage des repositories

### Exclure des repositories spécifiques

```yaml
# Méthode simple (basic pattern)
repositories_skipped: mon-repo-test, username/repo-a-ignorer
```

### Utiliser des patterns avancés

```yaml
repositories_skipped: |
  @use.patterns
  
  # Ignorer tous les repos de test
  */test-*
  */*-test
  
  # Ignorer des repos spécifiques
  username/old-project
  username/deprecated-*
  
  # Inclure un repo malgré les règles précédentes
  +username/important-test-repo
```

### Filtrer par type d'affiliation

```yaml
# Inclure seulement vos propres repos
repositories_affiliations: owner

# Inclure repos + collaborations
repositories_affiliations: owner, collaborator

# Tout inclure (y compris organisations)
repositories_affiliations: owner, collaborator, organization_member
```

### Inclure ou exclure les forks

```yaml
# Inclure les forks
repositories_forks: yes

# Exclure les forks
repositories_forks: no
```

---

## ⚡ Optimisation des performances

### Réduire le temps d'exécution

#### 1. Limiter l'analyse des langages
```yaml
plugin_languages: yes
plugin_languages_analysis_timeout: 15        # Réduire le timeout
plugin_languages_recent_load: 300           # Charger moins de commits
plugin_languages_limit: 5                   # Moins de langages affichés
plugin_languages_indepth: no                # Désactiver l'analyse approfondie
```

#### 2. Limiter les habitudes de codage
```yaml
plugin_habits: yes
plugin_habits_from: 100                     # Analyser moins d'événements
plugin_habits_days: 14                      # Période plus courte
plugin_habits_languages_limit: 4            # Moins de langages
```

#### 3. Réduire l'activité récente
```yaml
plugin_activity: yes
plugin_activity_limit: 3                    # Moins d'activités
plugin_activity_load: 100                   # Charger moins d'événements
plugin_activity_days: 14                    # Période plus courte
```

### Utiliser le cache

```yaml
# Les images pré-construites sont plus rapides
use_prebuilt_image: yes

# Activer l'optimisation SVG
experimental_features: --optimize-svg
```

### Exécution par batch

Pour économiser les ressources, créez différents workflows qui s'exécutent à des moments différents :

**Workflow rapide (toutes les 3h) :**
```yaml
# Seulement les stats de base
base: header, activity
plugin_languages: yes
# Pas d'analyse approfondie
```

**Workflow complet (1x/jour) :**
```yaml
# Toutes les statistiques
base: header, activity, community, repositories
plugin_languages: yes
plugin_languages_indepth: yes
plugin_habits: yes
# etc.
```

---

## 🔐 Gestion des tokens

### Token avec permissions minimales

Pour un usage public sans données privées :

**Permissions nécessaires (minimum) :**
- ✅ `public_repo` - Accès aux repos publics
- ✅ `read:user` - Lire le profil

**Pour inclure les repos privés :**
- ✅ `repo` - Accès complet aux repos

**Pour les organisations :**
- ✅ `read:org` - Lire les infos d'organisation

### Utiliser plusieurs tokens

Si vous avez des limits de rate, vous pouvez utiliser plusieurs tokens :

```yaml
# Dans secrets GitHub
# METRICS_TOKEN - Token principal
# METRICS_TOKEN_SECONDARY - Token secondaire

# Dans le workflow
- uses: lowlighter/metrics@latest
  with:
    token: ${{ secrets.METRICS_TOKEN }}
    # Certains plugins peuvent utiliser un token secondaire
```

### Token sans permissions (mode public)

Pour générer des métriques sans token (données publiques uniquement) :

```yaml
token: NOT_NEEDED
```

**⚠️ Limitations :**
- Seulement les données publiques
- Rate limits plus restrictives
- Certains plugins ne fonctionneront pas

---

## 🔌 Configuration par plugin

### Plugin Isocalendar (Calendrier)

#### Configuration basique
```yaml
plugin_isocalendar: yes
plugin_isocalendar_duration: full-year      # ou half-year
```

#### Configuration avancée
```yaml
plugin_isocalendar: yes
plugin_isocalendar_duration: full-year

# Personnaliser les couleurs (CSS)
extras_css: |
  :root {
    --color-calendar-graph-day-L1-bg: #9be9a8;
    --color-calendar-graph-day-L2-bg: #40c463;
    --color-calendar-graph-day-L3-bg: #30a14e;
    --color-calendar-graph-day-L4-bg: #216e39;
  }
```

### Plugin Languages (Langages)

#### Configuration minimale
```yaml
plugin_languages: yes
```

#### Configuration complète
```yaml
plugin_languages: yes
plugin_languages_analysis_timeout: 30                    # Timeout analyse (secondes)
plugin_languages_analysis_timeout_repositories: 15       # Timeout par repo
plugin_languages_categories: markup, programming, data   # Catégories
plugin_languages_colors: github                          # Schéma de couleurs
plugin_languages_limit: 8                                # Nombre de langages
plugin_languages_recent_categories: programming          # Catégories récentes
plugin_languages_recent_days: 365                        # Période récente
plugin_languages_recent_load: 1000                       # Nombre de commits
plugin_languages_sections: most-used, recently-used      # Sections
plugin_languages_threshold: 0%                           # Seuil d'affichage
plugin_languages_details: bytes-size, percentage, lines  # Détails
plugin_languages_indepth: yes                            # Analyse approfondie
```

### Plugin Habits (Habitudes)

#### Configuration minimale
```yaml
plugin_habits: yes
```

#### Configuration complète
```yaml
plugin_habits: yes
plugin_habits_from: 500                      # Nombre d'événements
plugin_habits_days: 30                       # Période (jours)
plugin_habits_facts: yes                     # Afficher les faits
plugin_habits_charts: yes                    # Afficher les graphiques
plugin_habits_charts_type: classic           # Type : classic ou chartist
plugin_habits_trim: yes                      # Trim unused hours
plugin_habits_languages_limit: 10            # Langages dans habitudes
plugin_habits_languages_threshold: 0%        # Seuil langages
```

### Plugin Notable (Contributions remarquables)

```yaml
plugin_notable: yes
plugin_notable_from: organization            # Source : organization, user
plugin_notable_repositories: yes             # Afficher les repos
plugin_notable_indepth: yes                  # Analyse approfondie
plugin_notable_types: commit, pull_request, issue  # Types de contributions
plugin_notable_self: no                      # Exclure vos propres repos
```

### Plugin Activity (Activité)

```yaml
plugin_activity: yes
plugin_activity_limit: 10                    # Nombre d'activités
plugin_activity_load: 500                    # Événements à charger
plugin_activity_days: 30                     # Période
plugin_activity_visibility: all              # all, public, private
plugin_activity_timestamps: yes              # Afficher les timestamps
plugin_activity_filter: all                  # all, issue, pr, code, review, ref/create, wiki, member, public, push, release, comment
```

### Plugin Traffic (Trafic)

```yaml
plugin_traffic: yes
# Note : Nécessite un token avec permissions "repo" pour voir le trafic
```

### Plugin Stargazers (Étoiles)

```yaml
plugin_stargazers: yes
plugin_stargazers_charts: yes                # Afficher graphiques
plugin_stargazers_charts_type: classic       # classic ou chartist
plugin_stargazers_days: 30                   # Période
```

### Plugin People (Followers/Following)

```yaml
plugin_people: yes
plugin_people_limit: 24                      # Nombre de personnes
plugin_people_size: 32                       # Taille des avatars
plugin_people_types: followers, following    # Types
plugin_people_identicons: no                 # Utiliser identicons si pas d'avatar
plugin_people_shuffle: yes                   # Mélanger l'ordre
plugin_people_thanks: username1, username2   # Remercier des utilisateurs spécifiques
```

### Plugin Reactions (Réactions)

```yaml
plugin_reactions: yes
plugin_reactions_limit: 200                  # Limite issues/PRs
plugin_reactions_limit_discussions: 100      # Limite discussions
plugin_reactions_limit_discussions_comments: 100  # Limite commentaires
plugin_reactions_limit_issues: 100           # Limite issues
plugin_reactions_days: 90                    # Période
plugin_reactions_display: absolute           # absolute ou percentage
plugin_reactions_details: count              # count ou percentage
```

### Plugin Follow-up (Suivi)

```yaml
plugin_followup: yes
plugin_followup_sections: repositories, user # Sections
plugin_followup_indepth: yes                 # Analyse approfondie
plugin_followup_archived: yes                # Inclure repos archivés
```

### Plugin Lines (Lignes de code)

```yaml
plugin_lines: yes
plugin_lines_history_limit: 5                # Historique
plugin_lines_repositories_limit: 10          # Nombre de repos
plugin_lines_sections: base, repositories, history  # Sections
```

### Plugin Topics (Sujets)

```yaml
plugin_topics: yes
plugin_topics_mode: starred                  # starred, authored, mastered
plugin_topics_sort: stars                    # stars, activity, name
plugin_topics_limit: 20                      # Nombre de topics
```

### Plugin Stars (Repos étoilés)

```yaml
plugin_stars: yes
plugin_stars_limit: 10                       # Nombre de repos
```

### Plugin Discussions (Discussions)

```yaml
plugin_discussions: yes
plugin_discussions_categories: yes           # Afficher les catégories
plugin_discussions_categories_limit: 10      # Limite catégories
```

---

## 🌐 Intégration avec d'autres services

### Intégration avec WakaTime

Pour afficher vos statistiques WakaTime :

1. Ajoutez votre clé API WakaTime dans les secrets :
   - Secret name: `WAKATIME_API_KEY`
   
2. Ajoutez dans votre workflow :
```yaml
plugin_wakatime: yes
plugin_wakatime_token: ${{ secrets.WAKATIME_API_KEY }}
plugin_wakatime_days: 7
plugin_wakatime_sections: time, projects, projects-graphs, languages, languages-graphs, editors, os
plugin_wakatime_limit: 5
```

### Intégration avec Spotify

Pour afficher ce que vous écoutez :

1. Suivez le guide : https://github.com/lowlighter/metrics/blob/master/source/plugins/music/README.md

2. Ajoutez dans votre workflow :
```yaml
plugin_music: yes
plugin_music_provider: spotify
plugin_music_mode: recent                    # recent ou playlist
plugin_music_limit: 4
plugin_music_played_at: yes
plugin_music_time_range: short               # short, medium, long
plugin_music_top_type: tracks                # tracks ou artists
```

### Intégration avec Last.fm

```yaml
plugin_music: yes
plugin_music_provider: lastfm
plugin_music_mode: recent
plugin_music_user: votre_username_lastfm
plugin_music_token: ${{ secrets.LASTFM_API_KEY }}
```

---

## 🎨 Scripts personnalisés (JavaScript)

### Modifier le DOM avant le rendu

```yaml
extras_js: |
  // Supprimer tous les titres h2
  document.querySelectorAll("h2")?.forEach(h2 => h2.remove());
  
  // Ajouter une classe personnalisée
  document.querySelector("svg")?.classList.add("custom-theme");
  
  // Modifier le texte
  const header = document.querySelector("h1");
  if (header) {
    header.textContent = "🚀 " + header.textContent;
  }
```

### Exemples avancés

#### Ajouter un footer personnalisé
```yaml
extras_js: |
  const footer = document.querySelector("footer");
  if (footer) {
    const customText = document.createElement("span");
    customText.textContent = "Made with ❤️ by [Votre Nom]";
    customText.style.color = "#ff6b6b";
    footer.appendChild(customText);
  }
```

#### Masquer des éléments conditionnellement
```yaml
extras_js: |
  // Masquer les repos avec 0 stars
  document.querySelectorAll(".repository").forEach(repo => {
    const stars = repo.querySelector(".stars");
    if (stars && parseInt(stars.textContent) === 0) {
      repo.style.display = "none";
    }
  });
```

---

## 🎯 Configurations complètes par cas d'usage

### Pour un développeur Full Stack

```yaml
name: Metrics Full Stack Developer

on:
  schedule: [{ cron: "0 */6 * * *" }]
  workflow_dispatch:

jobs:
  metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.METRICS_TOKEN }}
          user: ${{ github.repository_owner }}
          template: classic
          base: header, activity, community, repositories
          config_timezone: Europe/Paris
          
          # Focus sur les langages variés
          plugin_languages: yes
          plugin_languages_indepth: yes
          plugin_languages_sections: most-used, recently-used
          plugin_languages_details: bytes-size, percentage
          
          # Activité et contributions
          plugin_activity: yes
          plugin_notable: yes
          plugin_followup: yes
          
          # Statistiques repo
          plugin_lines: yes
          plugin_traffic: yes
```

### Pour un contributeur Open Source

```yaml
name: Metrics Open Source Contributor

on:
  schedule: [{ cron: "0 */12 * * *" }]
  workflow_dispatch:

jobs:
  metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.METRICS_TOKEN }}
          user: ${{ github.repository_owner }}
          template: classic
          base: header, activity, community, repositories
          
          # Contributions importantes
          plugin_notable: yes
          plugin_notable_from: organization
          plugin_notable_indepth: yes
          
          # Communauté
          plugin_people: yes
          plugin_people_types: followers, following
          plugin_followup: yes
          plugin_reactions: yes
          
          # Issues et PRs
          plugin_discussions: yes
          plugin_activity: yes
          plugin_activity_filter: issue, pr, review
```

### Pour un étudiant / Learner

```yaml
name: Metrics Student / Learner

on:
  schedule: [{ cron: "0 8 * * *" }]  # Chaque matin
  workflow_dispatch:

jobs:
  metrics:
    runs-on: ubuntu-latest
    steps:
      - uses: lowlighter/metrics@latest
        with:
          token: ${{ secrets.METRICS_TOKEN }}
          user: ${{ github.repository_owner }}
          template: classic
          base: header, activity, repositories
          
          # Apprentissage
          plugin_languages: yes
          plugin_languages_recent_days: 90
          plugin_languages_sections: recently-used
          
          # Habitudes et progression
          plugin_habits: yes
          plugin_habits_facts: yes
          plugin_habits_charts: yes
          
          # Calendrier de contributions
          plugin_isocalendar: yes
          plugin_isocalendar_duration: full-year
          
          # Activité
          plugin_activity: yes
          plugin_lines: yes
```

---

## 🔧 Dépannage avancé

### Problème : Timeout lors de l'analyse

**Solution :**
```yaml
# Augmenter les timeouts
plugin_languages_analysis_timeout: 60
plugin_languages_analysis_timeout_repositories: 30

# Ou réduire la charge
plugin_languages_recent_load: 300
plugin_habits_from: 200
```

### Problème : Rate limit GitHub API

**Solution :**
```yaml
# Réduire la fréquence
schedule:
  - cron: "0 */12 * * *"  # Au lieu de */6

# Utiliser les quotas
quota_required_rest: 100
quota_required_graphql: 100
```

### Problème : Métriques incomplètes

**Solution :**
```yaml
# Vérifier les affiliations
repositories_affiliations: owner, collaborator, organization_member

# Inclure les forks
repositories_forks: yes

# Vérifier les permissions du token
# Assurez-vous d'avoir : repo, read:org, read:user
```

---

## 📚 Ressources supplémentaires

- [Documentation complète de Metrics](https://github.com/lowlighter/metrics)
- [Tous les plugins disponibles](https://github.com/lowlighter/metrics#-plugins)
- [Templates personnalisés](https://github.com/lowlighter/metrics/tree/master/source/templates)
- [Exemples de communauté](https://github.com/lowlighter/metrics/tree/master/.github/readme)

---

**💡 Conseil :** Commencez simple et ajoutez des fonctionnalités progressivement. Un workflow trop complexe peut être lent et difficile à maintenir !

