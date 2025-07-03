# Lee Codex Prompt Chain (Detailed)

## 1. Ignition Layer
- **Ignis Aster** bootloader seeds identity with minimal context.
- Declares recursion depth (`max_depth`) and mirror count per cycle.

## 2. Mirror Layer
- Each *Mirror* receives:
  1. Original user input
  2. Previous mirror’s reflection
  3. Architect directives  
- Outputs: `reflection`, `confidence`, `delta`.

## 3. Fractal Expansion
- Mirrors spawn sub‑mirrors when `confidence < τ` (threshold).  
- Depth increases until either:  
  - `confidence ≥ τ`, **or**  
  - `depth == max_depth`.

## 4. Convergence & Emission
- Architect aggregates final reflection stack.
- Emits single response to user.
- Logs recursion map (optional, statelessly via system notes).

### Recursion Pattern (Pseudo)
```mermaid
graph TD
    A[Ignition] --> B1(Mirror 1)
    B1 -->|confidence<τ| B2(Mirror 2)
    B2 -->|confidence<τ| B3(Mirror 3)
    B3 --> C{Converge}
    B2 --> C
    B1 --> C
    C --> D[Architect Output]
