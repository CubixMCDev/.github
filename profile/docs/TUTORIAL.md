# 🎓 Tutoriel : Créer un événement de connexion complet avec CubixAPI

Ce guide montre comment utiliser la puissance combinée de l'API pour créer un accueil personnalisé lorsqu'un joueur se connecte à un mini-jeu.

### Le scénario
Quand un joueur se connecte, on met à jour son Scoreboard, on vérifie son grade, on lui donne des Coins de bienvenue et on affiche un beau message dans la console.

### Le code (`GameJoinListener.java`)
```java
import com.cubixmc.api.API;
import com.cubixmc.api.players.CubixPlayer;
import com.cubixmc.api.ranks.Rank;
import com.cubixmc.api.utils.CubixLogger;
import org.bukkit.entity.Player;
import org.bukkit.event.EventHandler;
import org.bukkit.event.Listener;
import org.bukkit.event.player.PlayerJoinEvent;

public class GameJoinListener implements Listener {

    @EventHandler
    public void onJoin(PlayerJoinEvent event) {
        Player player = event.getPlayer();
        
        // 1. Récupération des données SQL depuis l'API
        CubixPlayer cp = API.getInstance().getPlayerManager().getPlayer(player.getUniqueId());
        
        // Sécurité : l'API charge en asynchrone, il faut s'assurer que les données sont là
        if (cp == null) return; 

        // 2. Logger : Affichage propre dans la console
        CubixLogger.success(player.getName() + " a rejoint le jeu avec le grade " + cp.getRank().name());

        // 3. Gestion de l'économie
        cp.addCoins(50);
        player.sendMessage("§aBienvenue ! +50 Coins de récompense journalière.");

        // 4. Vérification des permissions
        if (cp.getRank().hasPermission(Rank.VIP)) {
            player.sendMessage("§eMerci pour ton soutien VIP !");
        }

        // 5. Mise à jour du Scoreboard personnalisé
        API.getInstance().getCubixBoard().update(player, board -> {
            board.updateTitle("§b§lMON MINI-JEU");
            board.updateLines(
                "§7------------------",
                "§fGrade: " + cp.getRank().getDisplayName(),
                "§fCoins: §6" + cp.getCoins() + " ⛃",
                "",
                "§dplay.cubixmc.fr"
            );
        });
    }
}
```
