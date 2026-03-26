# 👤 Gestion des Joueurs & Grades

L'API utilise la classe `CubixPlayer` pour encapsuler les données Bukkit avec les informations persistantes de la base de données.

### Récupérer un joueur
Le `PlayerManager` permet d'accéder aux données d'un joueur connecté :
```java
import com.cubixmc.api.API;
import com.cubixmc.api.players.CubixPlayer;

CubixPlayer cp = API.getInstance().getPlayerManager().getPlayer(player.getUniqueId());
if (cp != null) {
    String rankName = cp.getRank().getDisplayName(); // Récupère le nom du grade
    player.sendMessage("Votre grade est : " + rankName);
}
```

### Vérifier les permissions
Le système de grade supporte l'héritage des permissions via le `PermissionManager`.
```java
import com.cubixmc.api.ranks.Rank;

if (cp.getRank().hasPermission(Rank.MODERATOR)) {
    // Le joueur est modérateur ou plus (ADMIN, OWNER)
    player.sendMessage("Vous avez accès aux commandes de modération.");
}
```

### Grades disponibles
Les grades par défaut sont : `OWNER`, `ADMIN`, `MODERATOR`, `VIP`, `PLAYER`.
