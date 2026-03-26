# 🛠️ Boîte à Outils (Utils)

L'API met à disposition plusieurs classes utilitaires pour gagner un temps précieux lors du développement.

### 📝 Le Logger Intelligent (`CubixLogger`)
Oubliez les `System.out.println`. Le `CubixLogger` ajoute de belles couleurs dans la console et détecte automatiquement quel plugin l'a appelé pour afficher le bon préfixe !

```java
import com.cubixmc.api.utils.CubixLogger;

CubixLogger.info("Message classique en blanc");
CubixLogger.success("Génère un message vert avec un check ✔");
CubixLogger.warn("Génère un message jaune avec un avertissement ⚠");
CubixLogger.error("Affiche une erreur rouge ✖", exception);
```

### 🪨 Création d'Items (`ItemBuilder`)
L'`ItemBuilder` permet de générer des `ItemStack` complexes en une seule ligne, avec une prise en charge automatique des couleurs Hexadécimales (`#FFFFFF`) pour les versions modernes.

```java
import com.cubixmc.api.utils.ItemBuilder;

ItemStack epee = new ItemBuilder(Material.DIAMOND_SWORD)
    .setName("#FF0000Épée Sanguinaire") // Traduit automatiquement le code Hexa en Component !
    .setLore("§7Une arme terrible...", "", "§c+10 Dégâts")
    .addEnchant(Enchantment.SHARPNESS, 5)
    .setUnbreakable(true)
    .setAction("arme_speciale") // Ajoute un tag d'action caché dans l'item pour les GUI !
    .build();
```

### 🌍 Système de Langue (`LangManager`)
L'API gère la traduction multilingue (`fr_fr`, `en_us`) en créant dynamiquement un dossier `langs` pour votre plugin.

**1. Initialisation dans le `onEnable` de votre plugin :**
```java
import com.cubixmc.api.utils.LangManager;

LangManager.init(this); // Charge les fichiers YAML du dossier langs/
LangManager.setDefaultLang("fr_fr");
```

**2. Utilisation en jeu :**
L'API va automatiquement vérifier la langue choisie par le joueur dans la base de données et formater le message.
```java
// Dans fr_fr.yml : welcome_message: "Bienvenue %s sur le jeu !"
// Dans en_us.yml : welcome_message: "Welcome %s to the game!"

// Envoie directement le message traduit au joueur en remplaçant %s par son pseudo
LangManager.sendMessage(player, "welcome_message", "Fallback par défaut", true, player.getName());
```
