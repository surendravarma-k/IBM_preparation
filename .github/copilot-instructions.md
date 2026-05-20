# Copilot Instructions for Notebook Projects

## Project Overview
This is a Jupyter Notebook-based project focused on PySpark data processing. The codebase is minimal with a single primary notebook (`test.ipynb`).

## Architecture & Key Components

### Notebook Structure (`test.ipynb`)
- **Cell 1**: Simple Python print statement (baseline testing)
- **Cell 2**: PySpark SparkSession initialization and lifecycle
  - Uses local mode (`local[*]`) for development
  - Demonstrates proper session creation and cleanup with `stop()`

## Development Workflows

### Running Notebooks
- Execute notebooks via VS Code Jupyter extension
- Each cell runs independently; manage state carefully
- Run cells sequentially to build up SparkSession state

### PySpark Configuration
- **Master Setting**: `local[*]` (uses all available cores)
- **App Name**: Track via "MyApp" identifier in Spark UI
- **Session Cleanup**: Always call `spark.stop()` to free resources

## Project Patterns & Conventions

### PySpark Best Practices
1. Initialize SparkSession once per notebook (reuse across cells)
2. Always terminate session before notebook completion
3. Use local mode for development; adjust master URL for cluster deployment

### Minimal Project Structure
- Single notebook entry point
- No external configuration files or modules detected
- No build system or test framework currently in place

## Common Tasks

**Creating a new Spark computation:**
```python
# Add to cell in test.ipynb
df = spark.createDataFrame([(1, "a"), (2, "b")], ["id", "value"])
df.show()
```

**Debugging Spark jobs:**
- Monitor via Spark UI (typically http://localhost:4040)
- Use `df.explain()` to inspect query plans
- Check logs from `spark.stop()` output

## Integration Points
- **External**: Apache Spark runtime (must be installed)
- **Internal**: Single notebook with no cross-module dependencies

---
*Last updated: 2026-05-20 | Workspace: folder_vscode*
