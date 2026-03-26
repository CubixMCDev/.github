# 💰 Économie & Statistiques

L'API gère deux monnaies principales de manière asynchrone pour éviter tout lag lors des transactions SQL.

### Manipuler l'argent
Les méthodes sont directement accessibles via l'objet `CubixPlayer` :

```java
import com.cubixmc.api.API;
import com.cubixmc.api.players.CubixPlayer;

CubixPlayer cp = API.getInstance().getPlayerManager().getPlayer(player.getUniqueId());

// Ajouter des coins
cp.addCoins(100);

// Retirer des cristaux
cp.removeCristals(50);

// Récupérer le solde
int solde = cp.getCoins();
player.sendMessage("Vous avez actuellement " + solde + " coins.");
```

### Statistiques de jeu
L'API suit également le niveau et l'expérience du joueur :
* `cp.getLevel()` : Niveau actuel du joueur.
* `cp.getExp()` : Expérience accumulée.
