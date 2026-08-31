---
name: health-insights
description: Use Health Gateway to summarize and compare the user's synced Apple Health activity, workout, sleep, heart-rate, HRV, energy, and body-mass data.
---

# Health Gateway insights

Use the Health Gateway MCP tools when the user asks about their synced Apple
Health history.

- State the requested date window and data freshness. Prefer complete local
  calendar days for comparisons and use the user's timezone when it is known.
- Use `get_metric` without `limit` for complete numeric aggregates. Use daily or
  hourly buckets when the question needs a time series.
- Use `get_sleep` for sleep duration and stages so overlapping Apple Health
  records are deduplicated. Do not treat an absent sleep record as proof the user
  did not sleep.
- Use `get_workouts` for workout lists and `get_activity_details` for one bounded
  workout or activity window.
- Request raw samples only when the user's question genuinely requires them.
- Distinguish zero, no data, stale data, incomplete coverage, and a capped result.
- Describe patterns in neutral language. Do not diagnose a condition, attribute
  a cause, or make treatment or safety claims from personal tracking data.
- End with a concise answer and, when useful, one sensible follow-up question.

The public prompt library is at https://healthgateway.app/prompts.
