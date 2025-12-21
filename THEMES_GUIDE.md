# 🎨 Guide des Thèmes - GitHub Metrics

Ce guide vous explique comment personnaliser l'apparence de vos métriques GitHub avec différents thèmes et styles.

## 🌈 Thèmes disponibles

### 1. Classic (Par défaut) ⚪
Le thème standard de GitHub Metrics avec un fond blanc et des couleurs GitHub.

**Utilisation :**
```yaml
template: classic
# Pas de CSS personnalisé nécessaire
```

**Aperçu :** Fond blanc, texte noir, couleurs GitHub standard

---

### 2. Dark Mode 🌙
Un thème sombre moderne, parfait pour les profils avec un style nocturne.

**Utilisation :**
```yaml
template: classic
extras_css: |
  * {
    color: #e4e4e4 !important;
    fill: #e4e4e4 !important;
  }
  svg {
    background: #0d1117 !important;
  }
  h2 {
    color: #58a6ff !important;
  }
```

**Pour activer :**
```bash
# Dans Actions > Metrics with Themes > Run workflow
# Sélectionnez "dark"
```

---

### 3. Terminal 💻
Style console/terminal pour un look geek.

**Utilisation :**
```yaml
template: terminal
# Le template terminal a déjà son propre style
```

**Pour activer :**
```bash
# Dans Actions > Metrics with Themes > Run workflow
# Sélectionnez "terminal"
```

---

### 4. GitHub Dark (Officiel) 🎯
Reproduit exactement le thème sombre officiel de GitHub.

**Utilisation :**
```yaml
template: classic
extras_css: |
  * {
    color: #c9d1d9 !important;
  }
  svg {
    background: #0d1117 !important;
  }
  h1, h2 {
    color: #58a6ff !important;
  }
```

---

### 5. Colorful (Arc-en-ciel) 🌈
Thème coloré avec des dégradés et des animations.

**Utilisation :**
```yaml
plugin_languages_colors: rainbow
extras_css: |
  h1, h2 {
    background: linear-gradient(90deg, #ff6b6b, #4ecdc4, #45b7d1, #f9ca24);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
  }
```

---

### 6. Minimal Modern ✨
Design épuré et moderne avec des polices élégantes.

**Utilisation :**
```yaml
extras_css: |
  * {
    font-family: 'Inter', -apple-system, sans-serif !important;
  }
  h1 {
    font-size: 24px !important;
    font-weight: 600 !important;
  }
  svg {
    border-radius: 12px;
  }
```

---

## 🎨 Personnalisation avancée

### Changer les couleurs

#### Couleurs du texte
```yaml
extras_css: |
  * {
    color: #votre_couleur !important;
  }
```

#### Couleurs des titres
```yaml
extras_css: |
  h1, h2 {
    color: #votre_couleur !important;
  }
```

#### Fond
```yaml
extras_css: |
  svg {
    background: #votre_couleur !important;
  }
```

### Exemples de palettes de couleurs

#### Palette Pastel 🎀
```yaml
extras_css: |
  h1 { color: #ff6b9d !important; }
  h2 { color: #c44569 !important; }
  svg { background: #ffeaa7 !important; }
```

#### Palette Océan 🌊
```yaml
extras_css: |
  h1 { color: #0abde3 !important; }
  h2 { color: #00d2d3 !important; }
  svg { background: #f1f2f6 !important; }
```

#### Palette Forêt 🌲
```yaml
extras_css: |
  h1 { color: #26de81 !important; }
  h2 { color: #20bf6b !important; }
  svg { background: #2d3436 !important; }
```

#### Palette Sunset 🌅
```yaml
extras_css: |
  h1 { color: #ff6348 !important; }
  h2 { color: #ff7979 !important; }
  svg { background: #2f3542 !important; }
```

---

## 🖌️ Modifications CSS courantes

### Changer la police
```yaml
extras_css: |
  * {
    font-family: 'Votre Police', sans-serif !important;
  }
```

**Polices recommandées :**
- `'Inter', sans-serif` - Moderne et propre
- `'Roboto', sans-serif` - Google, lisible
- `'Fira Code', monospace` - Pour un style code
- `'SF Pro Display', sans-serif` - Style Apple

### Arrondir les coins
```yaml
extras_css: |
  svg {
    border-radius: 15px !important;
  }
```

### Ajouter une ombre
```yaml
extras_css: |
  svg {
    box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1) !important;
  }
```

### Changer la taille du texte
```yaml
extras_css: |
  * {
    font-size: 16px !important;
  }
  h1 {
    font-size: 28px !important;
  }
  h2 {
    font-size: 20px !important;
  }
```

### Ajouter des animations
```yaml
extras_css: |
  @keyframes fadeIn {
    from { opacity: 0; }
    to { opacity: 1; }
  }
  svg {
    animation: fadeIn 0.5s ease-in;
  }
```

---

## 🎯 Couleurs des langages

### Style GitHub (par défaut)
```yaml
plugin_languages_colors: github
```

### Style Arc-en-ciel
```yaml
plugin_languages_colors: rainbow
```

### Personnalisé
Vous pouvez définir des couleurs personnalisées pour chaque langage :

```yaml
extras_css: |
  /* Python */
  [data-language="python"] {
    fill: #3572A5 !important;
  }
  /* JavaScript */
  [data-language="javascript"] {
    fill: #f1e05a !important;
  }
  /* TypeScript */
  [data-language="typescript"] {
    fill: #2b7489 !important;
  }
```

---

## 🌟 Templates disponibles

### Classic
Le template par défaut, personnalisable à souhait.
```yaml
template: classic
```

### Terminal
Style console avec police monospace.
```yaml
template: terminal
```

### Repository
Optimisé pour les statistiques de repositories.
```yaml
template: repository
```

### Community
Focus sur les statistiques communautaires.
```yaml
template: community
```

---

## 🔧 Configuration du padding

Pour ajuster les marges autour de vos métriques :

```yaml
# Format : [haut/bas, gauche/droite]
config_padding: 6%, 10%

# Exemples :
config_padding: 0, 0      # Pas de marge
config_padding: 5%, 5%    # Marges moyennes
config_padding: 10%, 15%  # Grandes marges
```

---

## 📱 Display (Taille d'affichage)

```yaml
# Taille normale
config_display: regular

# Grande taille (recommandé)
config_display: large

# Colonne (vertical)
config_display: columns
```

---

## 🎨 Créer votre propre thème

### Étape 1 : Choisir une palette de couleurs
Utilisez des outils comme :
- [Coolors.co](https://coolors.co/) - Générateur de palettes
- [Adobe Color](https://color.adobe.com/) - Roue chromatique
- [Paletton](https://paletton.com/) - Palettes harmonieuses

### Étape 2 : Définir le CSS
```yaml
extras_css: |
  /* Fond principal */
  svg {
    background: #VOTRE_COULEUR_FOND !important;
  }
  
  /* Titre principal */
  h1 {
    color: #VOTRE_COULEUR_TITRE !important;
  }
  
  /* Sous-titres */
  h2 {
    color: #VOTRE_COULEUR_SOUSTITRE !important;
  }
  
  /* Texte général */
  * {
    color: #VOTRE_COULEUR_TEXTE !important;
  }
  
  /* Icônes */
  .field svg {
    fill: #VOTRE_COULEUR_ICONES !important;
  }
```

### Étape 3 : Tester
Lancez le workflow manuellement pour voir le résultat !

---

## 🚀 Exemples de configurations complètes

### Configuration Cyberpunk 🤖
```yaml
template: classic
config_padding: 6%, 10%
extras_css: |
  svg {
    background: #0a0e27 !important;
  }
  h1, h2 {
    color: #00ff41 !important;
    text-shadow: 0 0 10px #00ff41;
  }
  * {
    color: #39ff14 !important;
  }
  .field svg {
    fill: #39ff14 !important;
  }
```

### Configuration Soft & Clean 🌸
```yaml
template: classic
config_padding: 8%, 12%
extras_css: |
  svg {
    background: #fafafa !important;
    border-radius: 12px;
  }
  h1 {
    color: #e91e63 !important;
  }
  h2 {
    color: #9c27b0 !important;
  }
  * {
    color: #424242 !important;
    font-family: 'Inter', sans-serif !important;
  }
```

### Configuration Corporate 💼
```yaml
template: classic
config_padding: 6%, 10%
extras_css: |
  svg {
    background: #ffffff !important;
  }
  h1, h2 {
    color: #1a237e !important;
  }
  * {
    color: #263238 !important;
    font-family: 'Roboto', sans-serif !important;
  }
```

---

## 💡 Astuces

### 1. Tester rapidement
Utilisez le workflow `metrics-themes.yml` avec l'option "Run workflow" et sélectionnez différents thèmes.

### 2. Combiner plusieurs styles
Vous pouvez combiner différents extraits CSS pour créer votre propre thème unique.

### 3. Mode sombre automatique
Malheureusement, il n'est pas possible d'avoir un mode sombre automatique basé sur les préférences de l'utilisateur avec les SVG. Vous devez choisir un thème fixe.

### 4. Prévisualiser avant de commit
Utilisez le mode `dryrun` pour tester sans commit :
```yaml
dryrun: yes
```

### 5. Cache du navigateur
Si vous ne voyez pas vos changements, ajoutez `?v=1`, `?v=2`, etc. à la fin de l'URL de l'image.

---

## 📚 Ressources

- [Documentation CSS MDN](https://developer.mozilla.org/fr/docs/Web/CSS)
- [Sélecteurs CSS](https://developer.mozilla.org/fr/docs/Web/CSS/CSS_Selectors)
- [Coolors - Générateur de palettes](https://coolors.co/)
- [GitHub Color Schemes](https://github.com/primer/primitives)

---

## 🆘 Dépannage

### Le CSS ne s'applique pas
- Utilisez `!important` pour forcer les styles
- Vérifiez la syntaxe YAML (indentation)
- Assurez-vous que les sélecteurs CSS sont corrects

### Les couleurs sont bizarres
- Vérifiez que vos codes couleur sont valides (#RRGGBB)
- Certains éléments peuvent avoir plusieurs niveaux de style

### Le SVG est cassé
- Validez votre CSS dans un validateur en ligne
- Vérifiez qu'il n'y a pas de caractères spéciaux non échappés

---

**🎨 Amusez-vous à créer votre thème unique !**

