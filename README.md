# CyberFactions API

Public API for building addons that interact with CyberFactions — a
feature-rich Factions plugin for Paper 1.21.4+.

## Installation

### Gradle (Kotlin DSL)

```kotlin
repositories {
    maven("https://billyrosty.github.io/CyberFactions-API")
}

dependencies {
    compileOnly("fr.billyrosty:cyberfactions-api:0.5.7")
}
```

### Gradle (Groovy DSL)

```groovy
repositories {
    maven { url 'https://billyrosty.github.io/CyberFactions-API' }
}

dependencies {
    compileOnly 'fr.billyrosty:cyberfactions-api:0.5.7'
}
```

### Maven

```xml
<repositories>
    <repository>
        <id>cyberfactions</id>
        <url>https://billyrosty.github.io/CyberFactions-API</url>
    </repository>
</repositories>

<dependencies>
    <dependency>
        <groupId>fr.billyrosty</groupId>
        <artifactId>cyberfactions-api</artifactId>
        <version>0.5.7</version>
        <scope>provided</scope>
    </dependency>
</dependencies>
```

## plugin.yml

```yaml
name: MyAddon
version: 1.0.0
main: com.example.myaddon.MyAddon
depend: [CyberFactions]
```

## Quick start

```java
import fr.billyrosty.factions.api.CyberFactionsAPI;
import fr.billyrosty.factions.api.service.FactionService;
import fr.billyrosty.factions.api.model.FactionSnapshot;

public class MyAddon extends JavaPlugin {

    @Override
    public void onEnable() {
        CyberFactionsAPI api = CyberFactionsAPI.getInstance();
        FactionService factions = api.getFactionService();

        // Get a faction by name
        factions.getFaction("MyFaction").ifPresent(faction -> {
            getLogger().info("Found faction: " + faction.getName()
                + " with " + faction.getMembers().size() + " members");
        });
    }
}
```

## Available services

| Service                | Access                          | Description                             |
|------------------------|---------------------------------|-----------------------------------------|
| `FactionService`       | `api.getFactionService()`       | CRUD factions, members, roles           |
| `PlayerService`        | `api.getPlayerService()`        | Player state, power, faction membership |
| `ClaimService`         | `api.getClaimService()`         | Claim/unclaim chunks, query territory   |
| `EconomyService`       | `api.getEconomyService()`       | Faction bank operations                 |
| `RelationService`      | `api.getRelationService()`      | Set/query faction relations             |
| `TeleportationService` | `api.getTeleportationService()` | Homes, warps                            |
| `CommandRegistry`      | `api.getCommandRegistry()`      | Register custom `/f` subcommands        |
| `PermissionRegistry`   | `api.getPermissionRegistry()`   | Register custom faction permissions     |
| `UpgradeRegistry`      | `api.getUpgradeRegistry()`      | Register custom upgrade properties      |
| `AddonRegistry`        | `api.getAddonRegistry()`        | Lifecycle-managed addon system          |

## Documentation

Full API documentation with examples: [billyrosty.github.io/CyberFactions-Docs](https://billyrosty.github.io/CyberFactions-Docs/api/)

## License

MIT — see [LICENSE](LICENSE).
