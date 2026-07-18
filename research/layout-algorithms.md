# Layout Algorithms

Agents can't think spatially. Layout algorithms solve this — they take semantic relationships and produce coordinate positions.

## Algorithms

| Algorithm | Best For | Library |
|-----------|----------|---------|
| **Dagre** (Sugiyama) | Flowcharts, hierarchies | dagre-d3, @dagrejs/dagre |
| **Force-directed** | Knowledge graphs, networks | d3-force |
| **Grid** | Galleries, comparisons | Custom (uniform spacing) |
| **Radial** | Mind maps, exploration | d3-force (radial mode) |
| **Linear** | Timelines, presentations | Custom (sequential) |

## For Hermes

**dagre** for hierarchical content (pipelines, architecture diagrams, decision trees).
**Force-directed** for non-hierarchical content (knowledge graphs, research boards).
**Grid** for structured content (comparisons, galleries).

The layout engine should be a Python script callable from a Hermes skill:

```python
def layout_dagre(nodes, edges): ...
def layout_force(nodes, edges): ...
def layout_grid(nodes, cols): ...
def layout_radial(nodes, center): ...
```

Agent calls the skill with node/edge descriptions. Script returns positioned canvas JSON.

## Source

Leo, 2026-07-18. Based on claude-canvas's layout approach and Python library survey.
