# 🖼️ Système de Menus (GUI)

L'API fournit une structure simplifiée pour créer des inventaires interactifs sans gérer les événements `InventoryClickEvent` manuellement.

### Création d'un menu
Il suffit d'étendre la classe `CubixMenu` :

```java
import com.cubixmc.api.gui.CubixMenu;
import com.cubixmc.api.utils.ItemBuilder;
import org.bukkit.Material;
import org.bukkit.entity.Player;
import org.bukkit.inventory.Inventory;
import org.bukkit.inventory.ItemStack;

public class BoutiqueMenu extends CubixMenu {
    @Override
    public String getTitle() { return "§8Menu de la Boutique"; }

    @Override
    public int getRows() { return 3; }

    @Override
    public void setItems(Player player, Inventory inv) {
        // Utilisation de l'ItemBuilder de l'API
        inv.setItem(13, new ItemBuilder(Material.DIAMOND)
            .setName("§bAcheter un bonus")
            .setLore("§7Prix : §6500 Coins")
            .setAction("buy_bonus") // Tag d'action unique !
            .build());
    }

    @Override
    public void handleInteract(Player player, int slot, ItemStack item) {
        if ("buy_bonus".equals(getAction(item))) {
            player.sendMessage("§aVous avez cliqué sur l'achat du bonus !");
            player.closeInventory();
        }
    }
}
```

### Ouvrir le menu
```java
new BoutiqueMenu().open(player);
```
