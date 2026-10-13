# Future Industrialization

An independent Modern Industrialization (MI) addon bringing selected machines and quality-of-life features from GregTech and GT New Horizons into modern Minecraft.

**Initial target:** Minecraft 1.21.1, NeoForge, MI and Applied Energistics 2; intended to support FTB Evolution 1.43.1 after testing.

## Module 1: ME Hatches

| Hatch | Planned behavior |
| --- | --- |
| ME Item Input | Physical buffered item input accepted by MI multiblocks; externally accessible from AE2 pattern providers and logistics |
| ME Fluid Input | Physical buffered fluid input accepted by MI multiblocks; externally accessible from AE2 fluid automation |
| ME Stocking Item Input | Virtual inventory of up to 16 configured item types in ME storage; items consumed on recipe start |
| ME Stocking Fluid Input | Virtual inventory of up to 16 configured fluid types in ME storage; fluids consumed on recipe start |

### Non-negotiable correctness rules

- Use the existing MI ITEM_INPUT and FLUID_INPUT hatch types so existing multiblocks recognize the blocks.
- Respect AE2 connection, channels, power, ownership and security checks.
- Never consume resources during simulated recipe matching.
- A successful real recipe start must debit the AE2 network **exactly once**.
- Never present virtual stock as physical resources to external pipes or hoppers.
- On disconnect, unload, or insufficient inventory, refuse the recipe; no phantom inventory.
- Preserve filters and node state across server restart and world unload.
- Test pattern-provider automation, parallel crafting, zero-stock and mid-craft disconnection.

## Status

**Work in progress. No release has been built or verified yet.** The first implementation lives on a feature branch for review. The stocking variants require special treatment because MI's recipe logic simulates inventories by copying the input slots before starting a recipe; blindly overriding slots would risk resource duplication or partial consumption.

## Licensing and attribution

Future Industrialization is an independent project and is not affiliated with Modern Industrialization, Applied Energistics 2, GregTech or GT New Horizons. Preserve source licenses and attribution when adapting upstream code or assets.
