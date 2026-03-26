# 💎 API - Core Framework

<p align="center">
  <em>L'infrastructure centrale, performante et moderne du réseau <strong>CubixMC</strong>.</em>
</p>

---

## 📖 Présentation

**API** est un plugin natif **Paper** conçu pour centraliser toutes les fonctionnalités critiques du réseau CubixMC. Au lieu de dupliquer du code dans chaque mini-jeu (Hub, Rush, etc.), cette API fournit des outils unifiés, asynchrones et ultra-optimisés pour gérer les joueurs, l'économie, les interfaces et la communication inter-serveurs.

### ✨ Fonctionnalités Principales
* 👤 **Système de Joueurs (`CubixPlayer`) :** Mise en cache intelligente et requêtes SQL asynchrones.
* 🎖️ **Gestion des Rangs (`Rank`) :** Hiérarchie complète (OWNER, ADMIN, VIP, PLAYER) avec permissions dynamiques en base de données.
* 💰 **Économie Double :** Gestion fluide des `Coins` et des `Cristaux`.
* 🖼️ **Framework GUI (`CubixMenu`) :** Création d'inventaires interactifs orientés objet.
* 🌐 **BungeeCord (`BungeeManager`) :** Communication instantanée avec le proxy (téléportation, compteurs globaux).
* 🛡️ **Sécurité :** Filtrage dynamique des commandes (masquage des plugins dans l'auto-complétion).
* 📊 **Scoreboard & Tablist :** Affichage optimisé, personnalisable par chaque mini-jeu via des `Providers`.

---

## 🚀 Installation & Dépendance

Pour utiliser la puissance de l'**API** dans votre mini-jeu, ajoutez simplement l'API au classpath de votre projet.

Dans votre fichier **`paper-plugin.yml`** :
```yaml
name: MonMiniJeu
version: '1.0'
main: com.cubixmc.monjeu.MonJeu
api-version: '1.21'
dependencies:
  server:
    API:
      required: true
      join-classpath: true
```

---

## 📖 Sommaire de la Documentation
1. [👤 Gestion des Joueurs & Grades](docs/PLAYERS)
2. [💰 Économie & Statistiques](docs/ECONOMY)
3. [🖼️ Interface Graphique (Menus)](docs/GUI)
4. [🌐 Communication BungeeCord](docs/BUNGEE)
5. [🗄️ Base de données SQL](docs/DATABASE)
6. [🎮 Outils pour Mini-Jeux & Tablist](docs/GAME)
7. [🛠️ Boîte à Outils (Utils)](docs/UTILS)
8. [🎓 Tutoriel : Créer un mini-jeu](docs/TUTORIAL)

---

<p align="center">
  <b>Développé pour l'écosystème CubixMC.</b><br>
  <i>Ne pas distribuer.</i>
</p>
