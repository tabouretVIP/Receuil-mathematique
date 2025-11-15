# Recueil Mathématique - Template LaTeX

## Description

Ce template LaTeX est conçu pour créer des documents mathématiques de grande ampleur, inspiré par "An Infinitely Large Napkin" d'Evan Chen. Il offre une mise en page élégante et professionnelle avec de nombreuses fonctionnalités adaptées aux mathématiques.

## Caractéristiques principales

### 📖 Mise en page élégante
- **Police principale** : Linux Libertine (élégante et lisible)
- **Police mathématique** : newtxmath (assortie à Libertine)
- **Marges optimisées** : Adaptation pour impression recto-verso
- **En-têtes personnalisés** : Numéros de page colorés et informations de navigation

### 🎨 Page de garde spectaculaire
- Design moderne avec motifs géométriques
- Utilisation de TikZ pour des effets visuels
- Ornements mathématiques discrets
- Boîte centrale élégante avec ombres portées
- Entièrement personnalisable

### 📑 Tables des matières
- **Table générale** : Vue d'ensemble complète du document
- **Tables locales par partie** : Utilisation de `\parttoc`
- **Mini-tables par chapitre** : Utilisation de `\minitoc`
- Navigation facilitée dans les grands documents

### 🎯 Environnements mathématiques
Boîtes colorées avec `tcolorbox` pour :
- **Théorèmes** (bleu foncé)
- **Propositions** (bleu vif)
- **Lemmes** (rouge profond)
- **Définitions** (gris élégant)
- **Exemples, Corollaires, Remarques** (styles variés)

### 🔧 Packages inclus
- `minitoc` : Tables des matières locales
- `tcolorbox` : Boîtes colorées pour théorèmes
- `tikz` : Graphiques et dessins
- `fancyhdr` : En-têtes et pieds de page
- `hyperref` : Liens hypertextes internes
- `titlesec` : Personnalisation des titres

## Structure du document

```
recueil_mathematique.tex
├── Page de garde personnalisée
├── Matière préliminaire (frontmatter)
│   ├── Préface
│   └── Table des matières générale
├── Matière principale (mainmatter)
│   ├── Partie I : Fondements
│   │   └── Chapitre 1 : Logique
│   ├── Partie II : Théorie des ensembles
│   │   └── Chapitre 2 : Ensembles
│   ├── Partie III : Algèbre
│   │   └── Chapitre 3 : Structures
│   └── ... (autres parties)
└── Matière finale (backmatter)
    ├── Index des notations
    └── Bibliographie
```

## Compilation

### Méthode 1 : latexmk (recommandée)
```bash
latexmk -pdf recueil_mathematique.tex
```

### Méthode 2 : Compilation manuelle
```bash
pdflatex recueil_mathematique.tex
pdflatex recueil_mathematique.tex  # Deux fois pour les références
```

**Important** : Pour que les mini-tables des matières fonctionnent, il faut compiler **au moins deux fois**.

## Personnalisation

### Changer les couleurs du thème
Dans le préambule, modifiez ces lignes :
```latex
\definecolor{primarycolor}{RGB}{0,51,102}      % Couleur principale
\definecolor{secondarycolor}{RGB}{204,51,51}   % Couleur secondaire
\definecolor{accentcolor}{RGB}{0,102,204}      % Couleur d'accent
```

### Modifier la page de garde
La page de garde utilise TikZ. Vous pouvez :
- Changer le titre : modifier `Recueil Mathématique`
- Changer le sous-titre : modifier `Un voyage à travers les mathématiques supérieures`
- Changer l'auteur : modifier `Votre Nom`
- Adapter les motifs géométriques dans le code TikZ

### Ajouter de nouvelles parties
```latex
\part{Titre de la partie}
\label{part:identifiant}

\parttoc  % Table des matières locale pour cette partie

\chapter{Titre du chapitre}
\minitoc   % Mini-table pour ce chapitre
\vspace{1cm}

\section{Première section}
% Contenu...
```

### Utiliser les environnements de théorèmes

#### Théorèmes avec boîtes colorées
```latex
\begin{theoreme}{Titre du théorème}{label}
Énoncé du théorème.
\end{theoreme}

\begin{proposition}{Titre}{label}
Énoncé de la proposition.
\end{proposition}

\begin{lemme}{Titre}{label}
Énoncé du lemme.
\end{lemme}

\begin{definition}{Titre}{label}
Énoncé de la définition.
\end{definition}
```

#### Environnements sans boîtes
```latex
\begin{corollaire}
Énoncé du corollaire.
\end{corollaire}

\begin{exemple}
Un exemple illustratif.
\end{exemple}

\begin{remarque}
Une remarque importante.
\end{remarque}

\begin{proof}
Démonstration...
\end{proof}
```

## Commandes mathématiques prédéfinies

Le template inclut des commandes pour les ensembles classiques :
- `\N` : ℕ (entiers naturels)
- `\Z` : ℤ (entiers relatifs)
- `\Q` : ℚ (rationnels)
- `\R` : ℝ (réels)
- `\C` : ℂ (complexes)
- `\K` : 𝕂 (corps quelconque)

Et des opérateurs :
- `\Card` : Cardinal
- `\Ima` : Image
- `\Ker` : Noyau
- `\Hom` : Homomorphismes
- `\End` : Endomorphismes
- `\Aut` : Automorphismes

## Conseils d'utilisation

### Pour les documents très longs
1. Créez un fichier principal (comme celui-ci)
2. Créez des fichiers séparés pour chaque partie : `partie1.tex`, `partie2.tex`, etc.
3. Utilisez `\input{partie1}` dans le fichier principal

Exemple :
```latex
\mainmatter

\input{partie1_fondements}
\input{partie2_ensembles}
\input{partie3_algebre}
```

### Navigation rapide
Grâce aux mini-tables des matières et aux liens hypertextes :
- Cliquez sur les numéros de page dans la table des matières
- Utilisez les signets PDF (bookmarks) dans votre lecteur PDF
- Les références croisées sont cliquables : `\ref{chap:logique}`

### Gestion de la mémoire TeX
Pour les très gros documents, vous pourriez avoir besoin d'augmenter les limites de mémoire :
```bash
# Dans votre terminal (Linux/Mac)
export max_print_line=1000
export error_line=254
export half_error_line=238
```

## Dépendances

Packages LaTeX requis (généralement inclus dans TeX Live ou MiKTeX) :
- KOMA-Script (`scrbook`)
- `libertine`, `newtxmath` (polices)
- `minitoc` (tables locales)
- `tcolorbox` (boîtes colorées)
- `tikz` (graphiques)
- `fancyhdr` (en-têtes)
- `hyperref` (liens)
- `amsmath`, `amsthm`, `amssymb` (mathématiques)

## Licence

Ce template est fourni en l'état pour un usage personnel ou académique. Vous êtes libre de le modifier et de l'adapter à vos besoins.

## Crédits

Inspiré par :
- **An Infinitely Large Napkin** d'Evan Chen
- Les nombreux exemples de la communauté LaTeX sur TeX.StackExchange

## Support

Pour toute question ou suggestion d'amélioration, n'hésitez pas à consulter :
- [CTAN](https://ctan.org/) pour la documentation des packages
- [TeX.StackExchange](https://tex.stackexchange.com/) pour des questions spécifiques
- La documentation de `minitoc`, `tcolorbox` et `tikz`

---

**Bonne rédaction mathématique ! 📐✨**
