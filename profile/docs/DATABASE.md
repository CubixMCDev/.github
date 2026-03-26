# 🗄️ Base de données SQL

L'API utilise un `DatabaseManager` pour gérer les connexions MariaDB/MySQL. Les tables principales sont automatiquement créées au premier démarrage.

### Tables natives de l'API
* `cubix_players` : Stocke l'UUID, le grade, l'économie et la langue.
* `rank_permissions` : Stocke les permissions spécifiques de chaque grade.

---

### ⚡ Exécuter des requêtes simplifiées
L'API intègre des méthodes utilitaires dans le `DatabaseManager` pour vous éviter d'écrire de longs blocs `try-catch` dans vos propres plugins.

**1. Faire une modification (INSERT, UPDATE, DELETE) :**
La méthode `update` prépare automatiquement les variables pour éviter les failles SQL.
```java
import com.cubixmc.api.databases.DatabaseManager;

DatabaseManager db = API.getInstance().getDatabaseManager();

// Exemple : Insérer une statistique dans une table d'un mini-jeu
db.update("INSERT INTO mini_jeux_stats (uuid, kills) VALUES (?, ?)", player.getUniqueId().toString(), 10);
```

**2. Faire une lecture (SELECT) :**
La méthode `query` utilise un `ResultSetConsumer` pour traiter les résultats proprement.
```java
db.query("SELECT kills FROM mini_jeux_stats WHERE uuid = ?", rs -> {
    if (rs.next()) {
        int kills = rs.getInt("kills");
        player.sendMessage("Tu as fait " + kills + " kills !");
    }
}, player.getUniqueId().toString());
```
