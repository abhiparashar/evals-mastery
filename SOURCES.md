# Sources: check every claim yourself

Every claim in these docs comes from a public engineering blog, paper, doc page or source file. To check one: open the link, press **Cmd+F**, and search for the phrase in the "Search for" column.

On **2026-10-15** a script downloaded every link below and searched for the phrase. All 47 checks passed. Four Ramp pages load their text with JavaScript, so they were checked through a text reader instead.

Anything marked **[INFERENCE]** in the other docs is my own suggestion and has no source. Treat those as ideas to test, not facts.

## Engineering blogs and papers: how companies run evals

| Company | What it proves | Link | Search for |
|---|---|---|---|
| Nubank | An LLM auditor scores 100% of conversations | [blog](https://building.nu.com/building-ai-agents-for-131-million-customers/) | `every single conversation` |
| Nubank | Judge prompts tuned with GEPA; κ, golden-set sizes | [KDD '26 paper](https://arxiv.org/html/2606.08867) | `GEPA` |
| Nubank | Simulated customers screen versions before the A/B test | [paper](https://arxiv.org/html/2609.30137v1) | `250` |
| Monzo | 100-conversation golden set approved by experts | [blog](https://monzo.com/blog/engineering-the-future-of-customer-operations-the-monzo-ops-agent) | `approved by subject matter experts` |
| Monzo | Stateful tool simulator | same | `blocking a card updates its status` |
| Ramp | Approve / Reject / Needs review instead of confidence scores | [blog](https://builders.ramp.com/post/how-to-build-agents-users-can-trust) | `Confidence scores are hallucinations` |
| Ramp | User actions are not ground truth; team-reviewed golden sets | same | `frequently lenient` |
| Ramp | Paired metrics that pull in opposite directions | [blog](https://builders.ramp.com/post/financial-benchmarks) | `Unsure rate` |
| Ramp | Tests assert on tool calls, not only the final answer | [blog](https://builders.ramp.com/post/meet-ramp-research) | `query shape` |
| Airbnb | Golden set must include bad examples | [blog](https://airbnb.tech/ai-ml/eval-driven-development-lessons-from-evaluating-genai-at-scale) | `include bad examples` |
| Airbnb | Daily sample of live traffic | same | `5% of live` |
| Airbnb | Judges are noisy across runs | [blog](https://airbnb.tech/ai-ml/from-weeks-to-a-day-how-we-made-llm-evaluation-fast-enough-to-iterate-on/) | `drifts about one percent` |
| GitHub | 4,000+ offline tests for Copilot | [blog](https://github.blog/ai-and-ml/generative-ai/how-we-evaluate-models-for-github-copilot/) | `4,000 offline tests` |
| GitHub | Tool calls scored with a confusion matrix | [blog](https://github.blog/ai-and-ml/generative-ai/measuring-what-matters-how-offline-evaluation-of-github-mcp-server-works/) | `confusion matrix` |
| LinkedIn | Humans grade a daily slice of conversations | [blog](https://www.linkedin.com/blog/engineering/generative-ai/musings-on-building-a-generative-ai-product) | `500 daily conversations` |
| Stripe | Deterministic graders on real API objects | [blog](https://stripe.com/blog/can-ai-agents-build-real-stripe-integrations) | `grader` |
| Anthropic | pass@k vs pass^k, grader types | [blog](https://www.anthropic.com/engineering/demystifying-evals-for-ai-agents) | `pass^k` |
| Sierra | Voice tasks identical to text tasks | [blog](https://sierra.ai/blog/tau-voice-benchmarking-real-time-voice-agents-on-real-world-tasks) | `byte-for-byte` |
| Hamel & Shreya | Judge validation with TPR/TNR | [FAQ](https://hamel.dev/blog/posts/evals-faq/) | `TNR` |
| Eugene Yan | Sample size and confidence intervals | [blog](https://eugeneyan.com/writing/product-evals/) | `2.4%` |

## OSS code: real implementations you can read

| What | Project | File | Search for |
|---|---|---|---|
| pass^k function | τ-bench (Sierra) | [`src/tau2/metrics/agent_metrics.py`](https://github.com/sierra-research/tau2-bench/blob/main/src/tau2/metrics/agent_metrics.py) | `def pass_hat_k` |
| Database end-state grader | τ-bench | [`src/tau2/evaluator/evaluator_env.py`](https://github.com/sierra-research/tau2-bench/blob/main/src/tau2/evaluator/evaluator_env.py) | `class` |
| Simulated user | τ-bench | [`src/tau2/user/user_simulator.py`](https://github.com/sierra-research/tau2-bench/blob/main/src/tau2/user/user_simulator.py) | `class UserSimulator` |
| How rewards are combined | τ-bench | [`docs/evaluation.md`](https://github.com/sierra-research/tau2-bench/blob/main/docs/evaluation.md) | `reward_basis` |
| Banking domain | τ-bench | [`src/tau2/domains/banking_knowledge/environment.py`](https://github.com/sierra-research/tau2-bench/blob/main/src/tau2/domains/banking_knowledge/environment.py) | `def get_environment` |
| Agent test results + judge | LiveKit Agents | [`voice/run_result.py`](https://github.com/livekit/agents/blob/main/livekit-agents/livekit/agents/voice/run_result.py) | `class RunResult` |
| Per-call session report | LiveKit Agents | [`voice/report.py`](https://github.com/livekit/agents/blob/main/livekit-agents/livekit/agents/voice/report.py) | `SessionReport` |
| OpenTelemetry tracing | LiveKit Agents | [`telemetry/traces.py`](https://github.com/livekit/agents/blob/main/livekit-agents/livekit/agents/telemetry/traces.py) | `def set_tracer_provider` |
| Mock tools in tests | LiveKit Agents | [`__init__.py`](https://github.com/livekit/agents/blob/main/livekit-agents/livekit/agents/__init__.py) | `mock_tools` |
| Tracing example | LiveKit Agents | [`examples/voice_agents/otel_trace.py`](https://github.com/livekit/agents/blob/main/examples/voice_agents/otel_trace.py) | `set_tracer_provider` |
| Agent test example | LiveKit Agents | [`examples/frontdesk/test_agent.py`](https://github.com/livekit/agents/blob/main/examples/frontdesk/test_agent.py) | `judge` |
| Evals in CI | LiveKit Agents | [`.github/workflows/evals.yml`](https://github.com/livekit/agents/blob/main/.github/workflows/evals.yml) | `pytest` |
| Voice eval judge | Pipecat | [`src/pipecat/evals/judge.py`](https://github.com/pipecat-ai/pipecat/blob/main/src/pipecat/evals/judge.py) | `class EvalJudge` |
| Semantic WER | Pipecat stt-benchmark | [`evaluation/semantic_wer.py`](https://github.com/pipecat-ai/stt-benchmark/blob/main/src/stt_benchmark/evaluation/semantic_wer.py) | `calculate_wer` |
| Hidden grader rule | Stripe | [`benchmarks/checkout-gym/README.md`](https://github.com/stripe/ai/blob/main/benchmarks/checkout-gym/README.md) | `trivially` |
| Best of 3 runs | Stripe | [`benchmarks/README.md`](https://github.com/stripe/ai/blob/main/benchmarks/README.md) | `best score of 3` |
| Voice agent harness | OpenAI cookbook | [`duplex_voice_agent_evaluation/README.md`](https://github.com/openai/openai-cookbook/blob/main/examples/audio/duplex_voice_agent_evaluation/README.md) | `walk` |
| Error analysis skill | evals-skills | [`skills/error-discovery/SKILL.md`](https://github.com/ai-evals-course/evals-skills/blob/main/skills/error-discovery/SKILL.md) | `error` |
| pytest-style criteria | Intuit fasteval | [`README.md`](https://github.com/intuit/fasteval/blob/main/README.md) | `fe.criteria` |

## Docs: LiveKit and Langfuse facts for our self-hosted setup

| Fact | Link | Search for |
|---|---|---|
| Simulations need LiveKit Cloud | [LiveKit simulations](https://docs.livekit.io/testing/simulations.md) | `LiveKit Cloud project` |
| Session report works self-hosted | [LiveKit data hooks](https://docs.livekit.io/agents/observability/data.md) | `self-hosted deployments` |
| OpenTelemetry tracing | [LiveKit tracing](https://docs.livekit.io/deploy/observability/tracing.md) | `set_tracer_provider` |
| Mocking tools in tests | [LiveKit unit tests](https://docs.livekit.io/testing/unit-tests.md) | `mock_tools` |
| Judges on live traces | [Langfuse LLM-as-a-judge](https://langfuse.com/docs/evaluation/evaluation-methods/llm-as-a-judge) | `observation` |
| LiveKit → Langfuse | [Langfuse LiveKit integration](https://langfuse.com/integrations/frameworks/livekit) | `LiveKit` |

## Mistakes already caught and fixed

- `ROADMAP.md` cited a Pipecat `scripts/evals/` folder. It does not exist, so it was removed.
- `ROADMAP.md` cited `hamelsmu/evals-skills`. It is deprecated, so it was replaced with `ai-evals-course/evals-skills`.
- A LiveKit page links to `examples/voice_agents/langfuse_trace.py`, but that file returns 404, so the docs cite `otel_trace.py` instead.
