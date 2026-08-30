# C2Cognitive Configuration Reference

**C2Cognitive v1.0.0  |  Release 1  |  30 August 2026**

## Purpose

This is the exhaustive public index for the shipped `.agent/config.yml` template in C2Cognitive v1.0.0. It uses the
same indentation-based dotted-key interpretation as the shipped static audit helper and therefore enumerates the
same **306 configuration keys** measured by `scripts/verify/counts.py`.

This page documents template/configuration shape. Runtime authority remains in the actual `.agent/config.yml` of the
adopted repository and the procedures/validators that consume it.

## Top-level ownership

The configuration is divided into project identity, stack, commands, paths, environments, tooling, index placement,
mobile settings, corpus partitions, exclusion semantics, and thresholds. The `thresholds` section contains **228
direct runtime threshold keys** and is parsed strictly by the shared runtime config helper: duplicate direct threshold
keys are refused rather than silently resolved first-wins/last-wins.

## Complete 306-key index

| Dotted key | Source line | Shipped template value / shape |
| --- | ---: | --- |
| `project` | 2 | `(mapping/list container)` |
| `project.name` | 3 | `"{{PROJECT}}"` |
| `project.root` | 4 | `"{{REPO_ROOT}}"` |
| `project.shell` | 5 | `"{{SHELL}}"` |
| `stack` | 7 | `(mapping/list container)` |
| `stack.primary_language` | 8 | `"{{PRIMARY_LANG}}"` |
| `stack.package_manager` | 9 | `"{{PKG_MANAGER}}"` |
| `stack.orm` | 10 | `"{{ORM}}"` |
| `stack.database` | 11 | `"{{DB}}"` |
| `commands` | 13 | `(mapping/list container)` |
| `commands.build` | 14 | `"{{BUILD_CMD}}"` |
| `commands.test` | 15 | `"{{TEST_CMD}}"` |
| `commands.lint` | 16 | `"{{LINT_CMD}}"` |
| `commands.deploy` | 17 | `"{{DEPLOY_CMD}}"` |
| `paths` | 19 | `(mapping/list container)` |
| `paths.migrations` | 20 | `"{{MIGRATION_DIR}}"` |
| `paths.tracker` | 21 | `"{{TRACKER}}"` |
| `paths.product_doc` | 22 | `"{{PRODUCT_DOC}}"` |
| `paths.design_doc` | 23 | `"{{DESIGN_DOC}}"` |
| `environments` | 25 | `(mapping/list container)` |
| `environments.production` | 26 | `"{{PROD_URL}}"` |
| `environments.staging` | 27 | `"{{STAGING_URL}}"` |
| `tooling` | 29 | `(mapping/list container)` |
| `tooling.graph` | 30 | `"{{GRAPH_TOOL}}"` |
| `tooling.search` | 31 | `"{{SEARCH_TOOL}}"` |
| `tooling.find` | 32 | `"{{FIND_TOOL}}"` |
| `tooling.struct_edit` | 33 | `"{{STRUCT_EDIT_TOOL}}"` |
| `tooling.loc_count` | 34 | `"{{LOC_TOOL}}"` |
| `tooling.json_query` | 35 | `"{{JSON_TOOL}}"` |
| `tooling.work_graph` | 36 | `"{{WORK_GRAPH_TOOL}}"` |
| `index` | 42 | `(mapping/list container)` |
| `index.tool` | 43 | `"{{GRAPH_TOOL}}"` |
| `index.placement` | 44 | `"per_app"` |
| `index.root_index_allowed` | 45 | `false` |
| `index.index_dir_name` | 46 | `".index"` |
| `index.stale_after_days` | 47 | `7` |
| `index.per_partition` | 48 | `(mapping/list container)` |
| `index.per_partition.index_path` | 50 | `"{{PARTITION_1_NAME}}/.index"` |
| `index.per_partition.queries_bound_to` | 51 | `"{{PARTITION_1_NAME}}"` |
| `index.per_partition.index_path` | 53 | `"{{PARTITION_2_NAME}}/.index"` |
| `index.per_partition.queries_bound_to` | 54 | `"{{PARTITION_2_NAME}}"` |
| `mobile` | 57 | `(mapping/list container)` |
| `mobile.android` | 58 | `(mapping/list container)` |
| `mobile.android.module` | 59 | `"{{ANDROID_MODULE}}"` |
| `mobile.android.build_cmd` | 60 | `"{{ANDROID_BUILD_CMD}}"` |
| `mobile.android.test_cmd` | 61 | `"{{ANDROID_TEST_CMD}}"` |
| `mobile.android.min_sdk` | 62 | `"{{MIN_ANDROID_SDK}}"` |
| `mobile.android.sdk_path` | 63 | `"{{ANDROID_SDK_PATH}}"` |
| `mobile.ios` | 64 | `(mapping/list container)` |
| `mobile.ios.scheme` | 65 | `"{{IOS_SCHEME}}"` |
| `mobile.ios.build_cmd` | 66 | `"{{IOS_BUILD_CMD}}"` |
| `mobile.ios.test_cmd` | 67 | `"{{IOS_TEST_CMD}}"` |
| `mobile.ios.min_os` | 68 | `"{{MIN_IOS_VERSION}}"` |
| `mobile.ios.toolchain` | 69 | `"{{IOS_TOOLCHAIN}}"` |
| `mobile.qa_matrix` | 71 | `(mapping/list container)` |
| `mobile.qa_matrix.device` | 73 | `\"{{QA_DEVICE_1}}\"` |
| `mobile.qa_matrix.os` | 74 | `\"{{QA_OS_1}}\"` |
| `mobile.qa_matrix.device` | 76 | `\"{{QA_DEVICE_2}}\"` |
| `mobile.qa_matrix.os` | 77 | `\"{{QA_OS_2}}\"` |
| `mobile.qa_matrix.device` | 79 | `\"{{QA_DEVICE_3}}\"` |
| `mobile.qa_matrix.os` | 80 | `\"{{QA_OS_3}}\"` |
| `mobile.qa_matrix.device` | 82 | `\"{{QA_DEVICE_4}}\"` |
| `mobile.qa_matrix.os` | 83 | `\"{{QA_OS_4}}\"` |
| `mobile.qa_matrix.device` | 85 | `\"{{QA_DEVICE_5}}\"` |
| `mobile.qa_matrix.os` | 86 | `\"{{QA_OS_5}}\"` |
| `corpus_partitions` | 91 | `(mapping/list container)` |
| `corpus_partitions.include` | 93 | `[]` |
| `corpus_partitions.exclude` | 94 | `[]` |
| `corpus_partitions.include` | 96 | `[]` |
| `corpus_partitions.exclude` | 97 | `[]` |
| `exclude_match` | 104 | `"gitignore"` |
| `global_excludes` | 106 | `(mapping/list container)` |
| `exclude_carveouts` | 131 | `(mapping/list container)` |
| `exclude_carveouts.readable_by` | 133 | `[".agent/runbooks/test-to-workflow.md"]` |
| `exclude_carveouts.readable_by` | 135 | `[".agent/runbooks/context-compaction.md", ".agent/runbooks/workflow-discipline.md",` |
| `exclude_carveouts.readable_by` | 140 | `["SCAN-AND-ADOPT.prompt.md", "BOOTSTRAP-NEW-REPO.prompt.md"]` |
| `exclude_carveouts.readable_by` | 142 | `[".agent/runbooks/memory-lifecycle.md", ".agent/runbooks/agent-loadout.md",` |
| `thresholds` | 147 | `(mapping/list container)` |
| `thresholds.slice_specificity_min` | 148 | `0.6` |
| `thresholds.router_max_lines` | 149 | `205` |
| `thresholds.subagent_max_output_words` | 153 | `600` |
| `thresholds.subagent_wait_seconds_min` | 154 | `30` |
| `thresholds.batch_max_items` | 155 | `20` |
| `thresholds.question_queue_max` | 156 | `25` |
| `thresholds.seed_interview_max` | 157 | `12` |
| `thresholds.question_interactive` | 158 | `true` |
| `thresholds.question_option_min` | 159 | `2` |
| `thresholds.question_option_max` | 160 | `5` |
| `thresholds.question_freeform_slot` | 161 | `true` |
| `thresholds.question_chain_without_stop` | 162 | `true` |
| `thresholds.question_batch_mode` | 163 | `true` |
| `thresholds.question_batch_min` | 164 | `3` |
| `thresholds.question_batch_writer` | 165 | `scripts/interview/ask.py` |
| `thresholds.question_emit_when_no_tty` | 166 | `true` |
| `thresholds.question_batch_writer_emit_flag` | 167 | `--emit` |
| `thresholds.batch_trigger_files` | 168 | `5` |
| `thresholds.lesson_unconfirmed_decay_days` | 169 | `60` |
| `thresholds.lesson_location_claim_confidence_cap` | 170 | `0.4` |
| `thresholds.retrieval_precision_at_5_target` | 171 | `0.9` |
| `thresholds.ratchet_max_rounds` | 172 | `3` |
| `thresholds.max_subagents_per_run` | 173 | `16` |
| `thresholds.max_concurrent_workers` | 174 | `5` |
| `thresholds.agent_mode_default` | 175 | `single` |
| `thresholds.agent_read_workers_max` | 176 | `5` |
| `thresholds.coordinator_lease_ttl_seconds` | 177 | `300` |
| `thresholds.cognitive_write_lock_ttl_seconds` | 178 | `30` |
| `thresholds.read_window_max_lines` | 179 | `2000` |
| `thresholds.read_window_max_output_bytes` | 180 | `131072` |
| `thresholds.read_window_max_chars_per_line` | 181 | `2000` |
| `thresholds.read_small_text_max_bytes` | 182 | `1048576` |
| `thresholds.read_stream_line_max_bytes` | 183 | `262144` |
| `thresholds.read_path_suggestion_distance` | 184 | `2` |
| `thresholds.read_path_repair_enabled` | 185 | `true` |
| `thresholds.read_dedup_enabled` | 186 | `true` |
| `thresholds.read_dedup_self_expiring` | 187 | `true` |
| `thresholds.read_model_hard_max_lines` | 188 | `2000` |
| `thresholds.read_model_hard_max_output_bytes` | 189 | `131072` |
| `thresholds.read_model_hard_max_chars_per_line` | 190 | `2000` |
| `thresholds.read_intent_max_blind_windows` | 191 | `3` |
| `thresholds.read_jsonl_window_max_records` | 192 | `2000` |
| `thresholds.read_jsonl_record_max_bytes` | 193 | `65536` |
| `thresholds.read_archive_max_bytes` | 194 | `67108864` |
| `thresholds.read_archive_max_entries` | 195 | `10000` |
| `thresholds.read_archive_list_max_entries` | 196 | `200` |
| `thresholds.read_archive_member_max_compressed_bytes` | 197 | `16777216` |
| `thresholds.read_archive_member_max_uncompressed_bytes` | 198 | `16777216` |
| `thresholds.read_archive_total_max_uncompressed_bytes` | 199 | `134217728` |
| `thresholds.read_archive_max_compression_ratio` | 200 | `100` |
| `thresholds.cognitive_record_max_bytes` | 201 | `65536` |
| `thresholds.cognitive_text_field_max_bytes` | 202 | `16384` |
| `thresholds.cognitive_evidence_refs_max` | 203 | `64` |
| `thresholds.cognitive_entities_max` | 204 | `64` |
| `thresholds.cognitive_tags_max` | 205 | `64` |
| `thresholds.cognitive_source_refs_max` | 206 | `64` |
| `thresholds.cognitive_aggregation_targets_max` | 207 | `16` |
| `thresholds.evidence_graph_max_nodes` | 208 | `4096` |
| `thresholds.evidence_graph_max_edges` | 209 | `16384` |
| `thresholds.evidence_graph_max_depth` | 210 | `64` |
| `thresholds.worker_session_state_max` | 211 | `5` |
| `thresholds.memory_loadout_small_max` | 212 | `3` |
| `thresholds.memory_bulk_append_max_records` | 213 | `128` |
| `thresholds.memory_loadout_medium_max` | 214 | `6` |
| `thresholds.memory_loadout_complex_max` | 215 | `10` |
| `thresholds.skill_loadout_max` | 216 | `2` |
| `thresholds.skill_verified_evidence_min` | 217 | `2` |
| `thresholds.skill_verified_success_min` | 218 | `2` |
| `thresholds.memory_verified_l0_evidence_min` | 219 | `1` |
| `thresholds.memory_verified_l1_evidence_min` | 220 | `1` |
| `thresholds.memory_verified_l2_evidence_min` | 221 | `2` |
| `thresholds.memory_verified_l3_evidence_min` | 222 | `2` |
| `thresholds.memory_default_include_candidate` | 223 | `false` |
| `thresholds.memory_default_include_stale` | 224 | `false` |
| `thresholds.structural_default_include_stale` | 225 | `false` |
| `thresholds.structural_loadout_max` | 226 | `6` |
| `thresholds.agent_loadout_context_max_chars` | 227 | `32768` |
| `thresholds.agent_loadout_context_max_bytes` | 228 | `131072` |
| `thresholds.max_tool_calls_per_run` | 229 | `300` |
| `thresholds.budget_handoff_reserve_calls` | 230 | `12` |
| `thresholds.budget_suspend_outcome` | 231 | `suspended_resumable` |
| `thresholds.budget_reset_local_usage_on_resume` | 232 | `true` |
| `thresholds.phase3_resume_capsule_required` | 233 | `true` |
| `thresholds.python_launcher_posix` | 234 | `"/bin/sh scripts/c2python.sh"` |
| `thresholds.python_launcher_windows` | 235 | `"scripts\\c2python.cmd"` |
| `thresholds.max_retries_per_step` | 236 | `2` |
| `thresholds.max_graph_writes_per_run` | 237 | `500` |
| `thresholds.false_merge_review_min_confidence` | 238 | `0.8` |
| `thresholds.progress_watch_enabled` | 240 | `true` |
| `thresholds.progress_soft_seconds` | 241 | `7200` |
| `thresholds.progress_hard_seconds` | 242 | `28800` |
| `thresholds.progress_checkpoint_nochange_limit` | 243 | `2` |
| `thresholds.progress_audit_read_workers_max` | 244 | `5` |
| `thresholds.progress_activity_counts_as_progress` | 245 | `false` |
| `thresholds.progress_heartbeat_counts_as_progress` | 246 | `false` |
| `thresholds.progress_diagnostic_progress_resets_hard_clock` | 247 | `false` |
| `thresholds.progress_repo_write_self_authority` | 248 | `false` |
| `thresholds.progress_external_wait_requires_evidence` | 249 | `true` |
| `thresholds.progress_findings_max` | 250 | `32` |
| `thresholds.compaction_warn_ratio` | 252 | `0.7` |
| `thresholds.compaction_forced_ratio` | 253 | `0.85` |
| `thresholds.handoff_checkpoint_every_steps` | 254 | `25` |
| `thresholds.handoff_max_tool_calls` | 255 | `8` |
| `thresholds.rehydrate_max_tokens` | 256 | `2000` |
| `thresholds.resume_block_max_lines` | 257 | `20` |
| `thresholds.handoff_autoresume` | 258 | `true` |
| `thresholds.autoresume_crosses_phase_boundary` | 259 | `false` |
| `thresholds.autoresume_question_policy` | 260 | `blocker_or_sensitive_only` |
| `thresholds.autoresume_deferred_max` | 261 | `10` |
| `thresholds.goal_max_lines` | 263 | `120` |
| `thresholds.stage_goal_max_lines` | 264 | `60` |
| `thresholds.discipline_max_repeat_violations` | 266 | `3` |
| `thresholds.toolmap_min_confidence` | 268 | `0.7` |
| `thresholds.toolmap_generate_max` | 269 | `40` |
| `thresholds.model_adapter_capability_schema` | 272 | `2` |
| `thresholds.model_adapter_accept_legacy_v1` | 273 | `true` |
| `thresholds.model_adapter_require_live_for_production` | 274 | `true` |
| `thresholds.model_adapter_require_cache_aware_when_enabled` | 275 | `true` |
| `thresholds.model_adapter_cache_hit_is_authority` | 276 | `false` |
| `thresholds.model_adapter_persist_cache_key` | 277 | `false` |
| `thresholds.model_adapter_persist_private_reasoning` | 278 | `false` |
| `thresholds.context_representation_enabled` | 280 | `true` |
| `thresholds.context_representation_default_mode` | 281 | `native` |
| `thresholds.context_representation_preserve_order` | 282 | `true` |
| `thresholds.context_representation_freeze_selected_set` | 283 | `true` |
| `thresholds.context_representation_authority_aggressive_allowed` | 284 | `false` |
| `thresholds.context_representation_replan_on_effective_route_change` | 285 | `true` |
| `thresholds.context_representation_unknown_profile_policy` | 286 | `native` |
| `thresholds.context_representation_cache_hit_is_authority` | 287 | `false` |
| `thresholds.context_representation_min_runtime_byte_saving_percent` | 288 | `8` |
| `thresholds.tool_verification_timeout_seconds` | 290 | `60` |
| `thresholds.tool_verification_cold_timeout_seconds` | 291 | `600` |
| `thresholds.tool_verification_poll_seconds` | 292 | `15` |
| `thresholds.tool_verification_retries` | 293 | `1` |
| `thresholds.tool_discovery_exec_allowed` | 294 | `false` |
| `thresholds.tool_discovery_cache_write_allowed` | 295 | `false` |
| `thresholds.tool_discovery_manifest_write_allowed` | 296 | `false` |
| `thresholds.scan_scripts_execution_allowed` | 298 | `true` |
| `thresholds.scan_scripts_output_is_evidence` | 299 | `true` |
| `thresholds.provenance_export_enabled` | 301 | `true` |
| `thresholds.provenance_required_fields_enforced` | 302 | `true` |
| `thresholds.provenance_digest_algorithm` | 303 | `sha256` |
| `thresholds.provenance_signature_required` | 304 | `false` |
| `thresholds.provenance_actor_unknown_allowed` | 305 | `false` |
| `thresholds.provenance_example_min` | 306 | `3` |
| `thresholds.compliance_map_enabled` | 308 | `true` |
| `thresholds.compliance_frameworks_declared` | 309 | `3` |
| `thresholds.compliance_rows_min` | 310 | `30` |
| `thresholds.compliance_unmapped_core_allowed` | 311 | `2` |
| `thresholds.compliance_evidence_required` | 312 | `true` |
| `thresholds.compliance_control_id_pattern_enforced` | 313 | `true` |
| `thresholds.rule_preservation_enforced` | 315 | `true` |
| `thresholds.core_baseline_digest` | 316 | `c9432d6972cf54ca667e85c56d1ebaaaa3999e8e621e739d788a62f5a9a1513e` |
| `thresholds.core_baseline_path` | 317 | `.agent/core-baseline.md` |
| `thresholds.rule_registry_path` | 318 | `.agent/rule-registry.md` |
| `thresholds.rule_rejection_requires_approver` | 319 | `true` |
| `thresholds.rule_rejection_max` | 320 | `0` |
| `thresholds.router_absorb_mode` | 321 | `scope_first` |
| `thresholds.recall_preflight_enforced` | 322 | `true` |
| `thresholds.failure_ledger_path` | 323 | `.agent/failures.jsonl` |
| `thresholds.failure_schema_example_min` | 324 | `3` |
| `thresholds.failure_open_max_age_days` | 325 | `30` |
| `thresholds.failure_repeat_requires_justification` | 326 | `true` |
| `thresholds.failure_justification_min_chars` | 327 | `20` |
| `thresholds.failed_run_requires_failure_record` | 328 | `true` |
| `thresholds.failure_classes_declared` | 329 | `10` |
| `thresholds.failure_signature_required` | 330 | `true` |
| `thresholds.failure_promotion_threshold` | 331 | `3` |
| `thresholds.failure_promotion_requires_check` | 332 | `true` |
| `thresholds.discovery_cache_enabled` | 333 | `true` |
| `thresholds.discovery_cache_max_age_turns` | 334 | `40` |
| `thresholds.discovery_cache_min_rows_before_gate` | 335 | `1` |
| `thresholds.discovery_repeat_requires_reason` | 336 | `true` |
| `thresholds.coverage_census_enabled` | 337 | `true` |
| `thresholds.coverage_census_path` | 338 | `.agent/draft/coverage-census.json` |
| `thresholds.coverage_offer_max` | 339 | `10` |
| `thresholds.coverage_generation_requires_answer` | 340 | `true` |
| `thresholds.coverage_gap_classes_declared` | 341 | `4` |
| `thresholds.goal_inheritance_enabled` | 342 | `true` |
| `thresholds.goal_inheritance_paths` | 343 | `.agent/goals/goals.jsonl,.agent/state/CURSOR.json` |
| `thresholds.goal_stale_after_days` | 344 | `21` |
| `thresholds.goal_inheritance_requires_lineage` | 345 | `true` |
| `thresholds.blocker_policy_enforced` | 346 | `true` |
| `thresholds.blocker_classes_declared` | 347 | `7` |
| `thresholds.blocker_stop_threshold` | 348 | `5` |
| `thresholds.blocker_requires_failure_record` | 349 | `true` |
| `thresholds.doc_derived_confidence_cap` | 351 | `0.6` |
| `thresholds.contradiction_stop_threshold` | 352 | `10` |
| `thresholds.handoff_overhead_ratio_max` | 354 | `0.15` |
| `thresholds.repeat_work_ratio_max` | 355 | `0.05` |
| `thresholds.discovery_min_returned_results` | 356 | `3` |
| `thresholds.partition_coverage_min` | 357 | `0.05` |
| `thresholds.subagent_delegation_min_files` | 358 | `12` |
| `thresholds.lesson_reconfirm_interval_days` | 359 | `30` |
| `thresholds.prose_max_line_length` | 360 | `120` |
| `thresholds.state_schema_version` | 361 | `1` |
| `thresholds.vacuous_pass_reporting` | 362 | `true` |
| `thresholds.rule_enforcement_floor` | 363 | `8` |
| `thresholds.rule_enforcement_ratchet` | 364 | `true` |
| `thresholds.graph_vocabulary_coverage_required` | 365 | `true` |
| `thresholds.route_table_parity_enforced` | 366 | `true` |
| `thresholds.prefix_lock_enforced` | 367 | `true` |
| `thresholds.golden_min_rows` | 368 | `5` |
| `thresholds.golden_must_not_match_required` | 369 | `true` |
| `thresholds.advisory_mood_in_rules_allowed` | 370 | `false` |
| `thresholds.cognitive_emergency_authority_enabled` | 374 | `true` |
| `thresholds.cognitive_emergency_human_approval_required` | 375 | `true` |
| `thresholds.cognitive_emergency_max_ttl_seconds` | 376 | `900` |
| `thresholds.cognitive_emergency_cross_session_transfer` | 377 | `false` |
| `thresholds.cognitive_emergency_wildcard_authority` | 378 | `false` |
| `thresholds.cognitive_emergency_trust_escalation` | 379 | `false` |
| `thresholds.cognitive_emergency_repo_write_inheritance` | 380 | `false` |
| `thresholds.cognitive_emergency_host_reset_on_consumed_context` | 381 | `true` |
| `thresholds.bounded_emergency_authority_enabled` | 385 | `true` |
| `thresholds.bounded_emergency_human_approval_required` | 386 | `true` |
| `thresholds.bounded_emergency_max_ttl_seconds` | 387 | `900` |
| `thresholds.bounded_emergency_default_ttl_seconds` | 388 | `300` |
| `thresholds.bounded_emergency_cross_session_transfer` | 389 | `false` |
| `thresholds.bounded_emergency_wildcard_authority` | 390 | `false` |
| `thresholds.bounded_emergency_external_effect_inheritance` | 391 | `false` |
| `thresholds.bounded_emergency_cognitive_authority_inheritance` | 392 | `false` |
| `thresholds.bounded_emergency_rollback_execution_authorized` | 393 | `false` |
| `thresholds.bounded_emergency_require_normal_serialization` | 394 | `true` |
| `thresholds.bounded_emergency_snapshot_outside_target_required` | 395 | `true` |
| `thresholds.bounded_emergency_context_representation_authority` | 396 | `false` |
| `thresholds.bounded_emergency_cache_hit_authority` | 397 | `false` |
| `thresholds.bounded_emergency_model_route_authority` | 398 | `false` |
| `thresholds.bounded_emergency_clock_skew_seconds` | 399 | `30` |

## Complete 228-threshold namespace

| Threshold key | Shipped template value |
| --- | --- |
| `slice_specificity_min` | `0.6` |
| `router_max_lines` | `205` |
| `subagent_max_output_words` | `600` |
| `subagent_wait_seconds_min` | `30` |
| `batch_max_items` | `20` |
| `question_queue_max` | `25` |
| `seed_interview_max` | `12` |
| `question_interactive` | `true` |
| `question_option_min` | `2` |
| `question_option_max` | `5` |
| `question_freeform_slot` | `true` |
| `question_chain_without_stop` | `true` |
| `question_batch_mode` | `true` |
| `question_batch_min` | `3` |
| `question_batch_writer` | `scripts/interview/ask.py` |
| `question_emit_when_no_tty` | `true` |
| `question_batch_writer_emit_flag` | `--emit` |
| `batch_trigger_files` | `5` |
| `lesson_unconfirmed_decay_days` | `60` |
| `lesson_location_claim_confidence_cap` | `0.4` |
| `retrieval_precision_at_5_target` | `0.9` |
| `ratchet_max_rounds` | `3` |
| `max_subagents_per_run` | `16` |
| `max_concurrent_workers` | `5` |
| `agent_mode_default` | `single` |
| `agent_read_workers_max` | `5` |
| `coordinator_lease_ttl_seconds` | `300` |
| `cognitive_write_lock_ttl_seconds` | `30` |
| `read_window_max_lines` | `2000` |
| `read_window_max_output_bytes` | `131072` |
| `read_window_max_chars_per_line` | `2000` |
| `read_small_text_max_bytes` | `1048576` |
| `read_stream_line_max_bytes` | `262144` |
| `read_path_suggestion_distance` | `2` |
| `read_path_repair_enabled` | `true` |
| `read_dedup_enabled` | `true` |
| `read_dedup_self_expiring` | `true` |
| `read_model_hard_max_lines` | `2000` |
| `read_model_hard_max_output_bytes` | `131072` |
| `read_model_hard_max_chars_per_line` | `2000` |
| `read_intent_max_blind_windows` | `3` |
| `read_jsonl_window_max_records` | `2000` |
| `read_jsonl_record_max_bytes` | `65536` |
| `read_archive_max_bytes` | `67108864` |
| `read_archive_max_entries` | `10000` |
| `read_archive_list_max_entries` | `200` |
| `read_archive_member_max_compressed_bytes` | `16777216` |
| `read_archive_member_max_uncompressed_bytes` | `16777216` |
| `read_archive_total_max_uncompressed_bytes` | `134217728` |
| `read_archive_max_compression_ratio` | `100` |
| `cognitive_record_max_bytes` | `65536` |
| `cognitive_text_field_max_bytes` | `16384` |
| `cognitive_evidence_refs_max` | `64` |
| `cognitive_entities_max` | `64` |
| `cognitive_tags_max` | `64` |
| `cognitive_source_refs_max` | `64` |
| `cognitive_aggregation_targets_max` | `16` |
| `evidence_graph_max_nodes` | `4096` |
| `evidence_graph_max_edges` | `16384` |
| `evidence_graph_max_depth` | `64` |
| `worker_session_state_max` | `5` |
| `memory_loadout_small_max` | `3` |
| `memory_bulk_append_max_records` | `128` |
| `memory_loadout_medium_max` | `6` |
| `memory_loadout_complex_max` | `10` |
| `skill_loadout_max` | `2` |
| `skill_verified_evidence_min` | `2` |
| `skill_verified_success_min` | `2` |
| `memory_verified_l0_evidence_min` | `1` |
| `memory_verified_l1_evidence_min` | `1` |
| `memory_verified_l2_evidence_min` | `2` |
| `memory_verified_l3_evidence_min` | `2` |
| `memory_default_include_candidate` | `false` |
| `memory_default_include_stale` | `false` |
| `structural_default_include_stale` | `false` |
| `structural_loadout_max` | `6` |
| `agent_loadout_context_max_chars` | `32768` |
| `agent_loadout_context_max_bytes` | `131072` |
| `max_tool_calls_per_run` | `300` |
| `budget_handoff_reserve_calls` | `12` |
| `budget_suspend_outcome` | `suspended_resumable` |
| `budget_reset_local_usage_on_resume` | `true` |
| `phase3_resume_capsule_required` | `true` |
| `python_launcher_posix` | `"/bin/sh scripts/c2python.sh"` |
| `python_launcher_windows` | `"scripts\\c2python.cmd"` |
| `max_retries_per_step` | `2` |
| `max_graph_writes_per_run` | `500` |
| `false_merge_review_min_confidence` | `0.8` |
| `progress_watch_enabled` | `true` |
| `progress_soft_seconds` | `7200` |
| `progress_hard_seconds` | `28800` |
| `progress_checkpoint_nochange_limit` | `2` |
| `progress_audit_read_workers_max` | `5` |
| `progress_activity_counts_as_progress` | `false` |
| `progress_heartbeat_counts_as_progress` | `false` |
| `progress_diagnostic_progress_resets_hard_clock` | `false` |
| `progress_repo_write_self_authority` | `false` |
| `progress_external_wait_requires_evidence` | `true` |
| `progress_findings_max` | `32` |
| `compaction_warn_ratio` | `0.7` |
| `compaction_forced_ratio` | `0.85` |
| `handoff_checkpoint_every_steps` | `25` |
| `handoff_max_tool_calls` | `8` |
| `rehydrate_max_tokens` | `2000` |
| `resume_block_max_lines` | `20` |
| `handoff_autoresume` | `true` |
| `autoresume_crosses_phase_boundary` | `false` |
| `autoresume_question_policy` | `blocker_or_sensitive_only` |
| `autoresume_deferred_max` | `10` |
| `goal_max_lines` | `120` |
| `stage_goal_max_lines` | `60` |
| `discipline_max_repeat_violations` | `3` |
| `toolmap_min_confidence` | `0.7` |
| `toolmap_generate_max` | `40` |
| `model_adapter_capability_schema` | `2` |
| `model_adapter_accept_legacy_v1` | `true` |
| `model_adapter_require_live_for_production` | `true` |
| `model_adapter_require_cache_aware_when_enabled` | `true` |
| `model_adapter_cache_hit_is_authority` | `false` |
| `model_adapter_persist_cache_key` | `false` |
| `model_adapter_persist_private_reasoning` | `false` |
| `context_representation_enabled` | `true` |
| `context_representation_default_mode` | `native` |
| `context_representation_preserve_order` | `true` |
| `context_representation_freeze_selected_set` | `true` |
| `context_representation_authority_aggressive_allowed` | `false` |
| `context_representation_replan_on_effective_route_change` | `true` |
| `context_representation_unknown_profile_policy` | `native` |
| `context_representation_cache_hit_is_authority` | `false` |
| `context_representation_min_runtime_byte_saving_percent` | `8` |
| `tool_verification_timeout_seconds` | `60` |
| `tool_verification_cold_timeout_seconds` | `600` |
| `tool_verification_poll_seconds` | `15` |
| `tool_verification_retries` | `1` |
| `tool_discovery_exec_allowed` | `false` |
| `tool_discovery_cache_write_allowed` | `false` |
| `tool_discovery_manifest_write_allowed` | `false` |
| `scan_scripts_execution_allowed` | `true` |
| `scan_scripts_output_is_evidence` | `true` |
| `provenance_export_enabled` | `true` |
| `provenance_required_fields_enforced` | `true` |
| `provenance_digest_algorithm` | `sha256` |
| `provenance_signature_required` | `false` |
| `provenance_actor_unknown_allowed` | `false` |
| `provenance_example_min` | `3` |
| `compliance_map_enabled` | `true` |
| `compliance_frameworks_declared` | `3` |
| `compliance_rows_min` | `30` |
| `compliance_unmapped_core_allowed` | `2` |
| `compliance_evidence_required` | `true` |
| `compliance_control_id_pattern_enforced` | `true` |
| `rule_preservation_enforced` | `true` |
| `core_baseline_digest` | `c9432d6972cf54ca667e85c56d1ebaaaa3999e8e621e739d788a62f5a9a1513e` |
| `core_baseline_path` | `.agent/core-baseline.md` |
| `rule_registry_path` | `.agent/rule-registry.md` |
| `rule_rejection_requires_approver` | `true` |
| `rule_rejection_max` | `0` |
| `router_absorb_mode` | `scope_first` |
| `recall_preflight_enforced` | `true` |
| `failure_ledger_path` | `.agent/failures.jsonl` |
| `failure_schema_example_min` | `3` |
| `failure_open_max_age_days` | `30` |
| `failure_repeat_requires_justification` | `true` |
| `failure_justification_min_chars` | `20` |
| `failed_run_requires_failure_record` | `true` |
| `failure_classes_declared` | `10` |
| `failure_signature_required` | `true` |
| `failure_promotion_threshold` | `3` |
| `failure_promotion_requires_check` | `true` |
| `discovery_cache_enabled` | `true` |
| `discovery_cache_max_age_turns` | `40` |
| `discovery_cache_min_rows_before_gate` | `1` |
| `discovery_repeat_requires_reason` | `true` |
| `coverage_census_enabled` | `true` |
| `coverage_census_path` | `.agent/draft/coverage-census.json` |
| `coverage_offer_max` | `10` |
| `coverage_generation_requires_answer` | `true` |
| `coverage_gap_classes_declared` | `4` |
| `goal_inheritance_enabled` | `true` |
| `goal_inheritance_paths` | `.agent/goals/goals.jsonl,.agent/state/CURSOR.json` |
| `goal_stale_after_days` | `21` |
| `goal_inheritance_requires_lineage` | `true` |
| `blocker_policy_enforced` | `true` |
| `blocker_classes_declared` | `7` |
| `blocker_stop_threshold` | `5` |
| `blocker_requires_failure_record` | `true` |
| `doc_derived_confidence_cap` | `0.6` |
| `contradiction_stop_threshold` | `10` |
| `handoff_overhead_ratio_max` | `0.15` |
| `repeat_work_ratio_max` | `0.05` |
| `discovery_min_returned_results` | `3` |
| `partition_coverage_min` | `0.05` |
| `subagent_delegation_min_files` | `12` |
| `lesson_reconfirm_interval_days` | `30` |
| `prose_max_line_length` | `120` |
| `state_schema_version` | `1` |
| `vacuous_pass_reporting` | `true` |
| `rule_enforcement_floor` | `8` |
| `rule_enforcement_ratchet` | `true` |
| `graph_vocabulary_coverage_required` | `true` |
| `route_table_parity_enforced` | `true` |
| `prefix_lock_enforced` | `true` |
| `golden_min_rows` | `5` |
| `golden_must_not_match_required` | `true` |
| `advisory_mood_in_rules_allowed` | `false` |
| `cognitive_emergency_authority_enabled` | `true` |
| `cognitive_emergency_human_approval_required` | `true` |
| `cognitive_emergency_max_ttl_seconds` | `900` |
| `cognitive_emergency_cross_session_transfer` | `false` |
| `cognitive_emergency_wildcard_authority` | `false` |
| `cognitive_emergency_trust_escalation` | `false` |
| `cognitive_emergency_repo_write_inheritance` | `false` |
| `cognitive_emergency_host_reset_on_consumed_context` | `true` |
| `bounded_emergency_authority_enabled` | `true` |
| `bounded_emergency_human_approval_required` | `true` |
| `bounded_emergency_max_ttl_seconds` | `900` |
| `bounded_emergency_default_ttl_seconds` | `300` |
| `bounded_emergency_cross_session_transfer` | `false` |
| `bounded_emergency_wildcard_authority` | `false` |
| `bounded_emergency_external_effect_inheritance` | `false` |
| `bounded_emergency_cognitive_authority_inheritance` | `false` |
| `bounded_emergency_rollback_execution_authorized` | `false` |
| `bounded_emergency_require_normal_serialization` | `true` |
| `bounded_emergency_snapshot_outside_target_required` | `true` |
| `bounded_emergency_context_representation_authority` | `false` |
| `bounded_emergency_cache_hit_authority` | `false` |
| `bounded_emergency_model_route_authority` | `false` |
| `bounded_emergency_clock_skew_seconds` | `30` |

## Important semantics

* A value shown here is the shipped template/default shape, not proof that it is correct for a target repository.
* Adoption resolves placeholders and project-specific values rather than treating template examples as discovered
  facts.
* A threshold is operational policy/configuration; it is not a model-confidence score and does not grant authority.
* Index, budget, batching, context, liveness, memory, retry, and other limits are centralized so copies in prose can
  be audited for drift.
* `scripts/verify/counts.py` measures the number of keys/thresholds; `scripts/verify/claims.py` checks published numeric
  claims against measured values.

See [Control Plane Catalog](C2COGNITIVE-CONTROL-PLANE-CATALOG.md) and
[Script and Verification Catalog](C2COGNITIVE-SCRIPT-VERIFICATION-CATALOG.md).
