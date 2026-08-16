# claude-plugins — marketplace `roman-dev`

Hub único de los plugins de Claude Code de Roman Martini (ADR-009 de agent-studio). Este repo **solo cataloga**: cada plugin vive y se desarrolla en su propio repo, referenciado con source `git-subdir`/`github`.

## Uso

```
/plugin marketplace add roman-martini/claude-plugins   # una sola vez
/plugin install as@roman-dev
```

Actualizaciones: `/plugin update as@roman-dev` (hay update cuando el plugin bumpea la `version` de su `plugin.json`). Refrescar el catálogo: `/plugin marketplace update roman-dev`.

## Catálogo

| Plugin | Repo fuente | Qué es |
|---|---|---|
| `as` | [agent-studio](https://github.com/roman-martini/agent-studio) (`plugins/as/`) | Meta-agentes: construir, revisar y mejorar agentes, skills y blueprints + catálogo de blueprints |

Pendiente de sumar: `cfg` (agent-configs).

## Migración desde el paquete npm (`@roman-agents/agent-studio`)

El paquete npm está deprecado. Una vez por máquina, limpiar los restos de la instalación global y pasar al plugin:

1. Eliminar de `~/.claude/`: `agents/as-*.md`, `skills/as-*/`, `commands/as/`, `knowledge/as-*.md` y `blueprints/` (si su único origen era agent-studio).
2. Desinstalar el paquete donde estuviera como dependencia: `npm uninstall @roman-agents/agent-studio`.
3. `/plugin marketplace add roman-martini/claude-plugins` + `/plugin install as@roman-dev`.
4. Verificar: `/as:claude-expert hola` responde y los sub-agents `as-*` aparecen en `/context`.

## Agregar un plugin nuevo al catálogo

Una entrada más en `plugins[]` de [.claude-plugin/marketplace.json](.claude-plugin/marketplace.json) con source `git-subdir` (subdirectorio de otro repo) o `github` (repo entero = plugin). No duplicar `version` acá: la resuelve el `plugin.json` del plugin.
