# ASHEN — The Ashen Reach

A Fabric 26.3 mod adding a volcanic dimension with custom terrain generation. This milestone is deliberately **terrain-only**.

## Locked scope
- No entity registrations, entity classes, bosses, animals, monsters or NPCs.
- No natural mob spawns: the biome defines no natural-spawn attribute, and noise settings explicitly disable mob generation.
- No spawn targets.
- Basalt terrain, lava in low floor cavities, basalt columns, blackstone outcrops, glowstone, ash ambience and Nether-derived cavern density.
- No portal, ancient ruin structures or boss content in this terrain-only pass; those are separate generation layers.

## Toolchain
- Minecraft 26.3
- Fabric Loader 0.20.1
- Java 25
- Fabric Loom 1.19-SNAPSHOT
- Gradle 9.8.2

This milestone is data-driven and does not require Fabric API at runtime.

## Build
Run `gradle build`. The JAR is written to `build/libs/`. The `verifyTerrainOnly` task fails if mob generation is re-enabled or any spawn targets or natural spawn entries are added. GitHub Actions also builds the JAR and publishes an `ashen-mod` artifact.

## Enter the dimension
Install the JAR in the `mods` folder, create a disposable world, then run:

```mcfunction
/execute in ashen:the_ashen_reach run tp @s 0 90 0
```

No portal is included yet. Use a fresh world when testing world-generation changes.

## Generation design
- Custom biome: `ashen:ashen_wastes`.
- Nether-derived density shape with open sky, basalt as the base block and lava as the default fluid.
- Custom material rule paints basalt surfaces and lava in low floor holes.
- Vanilla basalt-delta features add columns, deltas, blackstone and volcanic details.
- Ash particles, volcanic fog and basalt-delta ambience establish the atmosphere.

The supplied JAR is resource-only: no Java classes or entity code. Its ZIP/JAR structure and JSON syntax have been checked, but a Minecraft 26.3 runtime test is still required to verify registry codecs and actual terrain appearance.
