# 🎮 Outils pour Mini-Jeux & Esthétique

L'API fournit des standards pour faciliter le développement de vos modes de jeu.

### 🔄 Les États de Jeu (GameState)
Afin d'unifier le code entre tous les mini-jeux, l'API propose une énumération `GameState` avec les états classiques d'une partie.

* `LOBBY` : En attente de joueurs.
* `STARTING` : Chronomètre de lancement en cours.
* `PLAYING` : Partie en cours.
* `FINISH` : Fin de la partie et affichage des vainqueurs.

**Exemple d'utilisation :**
```java
import com.cubixmc.api.game.GameState;

private GameState currentState = GameState.LOBBY;

public void startGame() {
    this.currentState = GameState.PLAYING;
    // Lancer la partie...
}
```

---

### 📋 Personnaliser la Tablist
Vous pouvez modifier l'apparence des joueurs dans le menu TAB et la couleur de leur pseudo au-dessus de leur tête en implémentant l'interface `TabProvider`.

```java
import com.cubixmc.api.tab.TabProvider;
import net.kyori.adventure.text.Component;
import net.kyori.adventure.text.format.NamedTextColor;
import net.kyori.adventure.text.format.TextColor;

API.getInstance().getTabManager().setProvider(new TabProvider() {
    @Override
    public Component getPlayerName(Player player) {
        // Définit l'affichage complet dans le menu TAB
        return Component.text("[Joueur] " + player.getName(), NamedTextColor.GRAY);
    }

    @Override
    public TextColor getTeamColor(Player player) {
        // Définit la couleur du nom affiché au-dessus du personnage
        return NamedTextColor.GRAY;
    }
});
```
