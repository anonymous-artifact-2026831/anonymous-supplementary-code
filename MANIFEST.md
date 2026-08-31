# Code Manifest

The following requested source files are included without omission:

- `scripts/evaluate_trajectory_quality.py`
- `scripts/exp_oracle_v1/rewrite_entity_ambiguous_queries_with_llm.py`
- `scripts/exp_oracle_v1/rewrite_non_ambiguous_queries_with_disturb_llm.py`
- `scripts/exp_oracle_v1/run_first_round_disturb_rewrite_experiment_all_sources.py`
- `scripts/exp_oracle_v1/run_first_round_oracle_rewrite_experiment.py`
- `flashrag/pipeline/iigcr_pipeline.py`
- `flashrag/pipeline/omni_pipeline.py`
- `flashrag/pipeline/amb_rewrite_pipeline.py`

One direct dependency is also included:

- `scripts/exp_oracle_v1/run_first_round_disturb_rewrite_experiment.py`

All original absolute local paths have been replaced with generic `data/` paths
or the `FLASHRAG_ROOT` and `REFAMB_DATA_ROOT` environment variables. No dataset,
model weight, result, credential, or personal configuration file is included.
