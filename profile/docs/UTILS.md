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
L'API intègre un puissant gestionnaire de traductions multilingues (`fr_fr`, `en_us`, etc.) lié directement à la base de données (MariaDB). Il crée dynamiquement un dossier `langs` par plugin et gère les variables ainsi que les messages multi-lignes.

**1. Initialisation dans le `onEnable` de votre plugin :**
```java
import com.cubixmc.api.utils.LangManager;

LangManager.init(this); // Charge tous les fichiers YAML du dossier langs/ de votre plugin
LangManager.setDefaultLang("fr_fr"); // Langue par défaut de secours
```

**2. Configuration des fichiers (ex: `langs/fr_fr.yml` & `langs/en_us.yml`) :**
Le système supporte les codes couleurs (`&`), les sauts de ligne (`\n`), et les arguments dynamiques indexés (`{0}`, `{1}`, etc.).

*Dans `fr_fr.yml` :*
```yaml
welcome.message: "&eBienvenue {0} sur le serveur !\n&7Vous avez actuellement &6{1} coins&7."
```

*Dans `en_us.yml` :*
```yaml
welcome.message: "&eWelcome {0} to the server!\n&7You currently have &6{1} coins&7."
```

**3. Utilisation en jeu :**
L'API va automatiquement récupérer la langue du joueur via son profil (`CubixPlayer`), formater le message avec les arguments, et l'envoyer.
```java
// Paramètres : Joueur, ID du message, Message de secours (fallback), Activer les couleurs, Arguments...
LangManager.sendMessage(player, "welcome.message", "§cMessage introuvable", true, player.getName(), cp.getCoins());
```

**4. Sélection obligatoire de la langue :**
Lors de leur toute première connexion au réseau, la langue des joueurs est définie sur `null` dans la base de données. L'API les force automatiquement à ouvrir une interface graphique (`LanguageMenu`) qu'ils ne peuvent pas fermer (anti-Échap) tant qu'ils n'ont pas sélectionné leur drapeau. Leur choix est ensuite sauvegardé de manière globale pour tout le réseau.
