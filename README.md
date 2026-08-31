# Supplementary Code

This repository contains the implementation used for query rewriting, multi-step
retrieval pipelines, and trajectory-quality evaluation. It intentionally
excludes datasets, model weights, experiment outputs, credentials, and machine-
specific configuration.

## Contents

| Path | Purpose |
| --- | --- |
| `flashrag/pipeline/omni_pipeline.py` | Multi-modal iterative retrieval pipeline. |
| `flashrag/pipeline/iigcr_pipeline.py` | IIGCR pipeline implementation. |
| `flashrag/pipeline/amb_rewrite_pipeline.py` | Ambiguity-aware query-rewriting baseline. |
| `scripts/evaluate_trajectory_quality.py` | Trajectory-quality metrics and LLM judging. |
| `scripts/exp_oracle_v1/` | Oracle and disturbance rewriting scripts. |

`run_first_round_disturb_rewrite_experiment.py` is included because it is called
directly by `run_first_round_disturb_rewrite_experiment_all_sources.py`.

## Setup

Use Python 3.11 or newer (the scripts use `tomllib`). Start from a compatible
FlashRAG checkout/environment, install its dependencies, then install the
additional dependencies:

```bash
pip install -r requirements.txt
```

Copy the three files in `flashrag/pipeline/` over the matching files in that
FlashRAG checkout. When running either first-round experiment script, set the
checkout location explicitly:

```bash
export FLASHRAG_ROOT=/path/to/flashrag-checkout
export REFAMB_DATA_ROOT=/path/to/data
```

The experiment scripts add `FLASHRAG_ROOT` to `sys.path`; `REFAMB_DATA_ROOT`
defaults to `$FLASHRAG_ROOT/data`. The remaining scripts use paths relative to
this repository's `data/` directory by default, so they should be run from the
repository root or given their explicit command-line paths.

## Data layout and credentials

Place the non-released inputs under `data/` using the paths referenced by the
script arguments (prompt TOML files, task JSONL files, and prior trajectory
outputs). All paths are deliberately generic placeholders; no original local
paths or experimental outputs are included.

Scripts that call a compatible OpenAI API read credentials from environment
variables, most commonly:

```bash
export SILICONFLOW_API_KEY='...'
```

Never commit credentials, local model directories, generated outputs, or
datasets. The included `.gitignore` excludes these materials.

## Example commands

```bash
python scripts/evaluate_trajectory_quality.py \
  --input-parent-dir data/results/example_run \
  --fact-prompt data/prompts/extract_atomic_fact_set.toml \
  --utility-prompt data/prompts/label_iteration_utility.toml

python scripts/exp_oracle_v1/rewrite_entity_ambiguous_queries_with_llm.py \
  --dataset data/datasets/RefAmb/task_balanced.jsonl \
  --prompt data/prompts/rewrite_entity_ambiguous_query.toml
```

The oracle and all-source runners contain source-run lists near the top of
their files. Populate these with the paths to the released or reconstructed
trajectory outputs before executing them.

## License

This repository contains modified files derived from FlashRAG. Its MIT license
notice is retained in `third_party_licenses/FlashRAG-MIT.txt`.
