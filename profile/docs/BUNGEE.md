# 🌐 Communication BungeeCord

Le `BungeeManager` centralise les échanges avec le proxy pour tout le réseau.

### Téléportation
Envoyer un joueur vers un autre serveur du réseau :
```java
import com.cubixmc.api.bungee.BungeeManager;

BungeeManager bungee = API.getInstance().getBungeeManager();
bungee.connectToServer(player, "Rush-01");
```

### Informations Globales
Récupérer des données en provenance du proxy :
```java
String currentServer = bungee.getServerName(); // Nom du serveur actuel (ex: Hub-01)
int networkOnline = bungee.getGlobalPlayerCount(); // Joueurs sur TOUT le réseau

player.sendMessage("Il y a " + networkOnline + " joueurs sur le réseau CubixMC !");
```
