# Key Learnings: Western vs Chinese Open Models and Distillation

Evidence-based summary from discussion.

## Key Points

- Chinese open models outperform most Western open models of similar class (see Reflection Beam as a recent Western open attempt: https://reflection.ai/blog/introducing-beam), even though Western open labs can freely distill from the Chinese open models. This shows the gap is not explained by distillation access alone.

- Distillation is powerful but incomplete. The DeepSeek-R1 paper (https://arxiv.org/abs/2501.12948) shows that SFT on ~800k traces from the large R1 teacher produced smaller models that were dramatically stronger than their bases and often beat much larger non-reasoning models (e.g., Distill-Qwen-32B at 72.6 on AIME 2024 vs R1’s 79.8). However, full parity was not reached.

- Distillation transfers reasoning patterns more efficiently than small models discovering them via RL alone. In the same paper, pure RL on a 32B base underperformed the distilled version of that same base.

- Stronger teachers do not automatically produce stronger students. Capacity-gap results show that beyond a point, students cannot fully model a much stronger teacher’s distribution; gains saturate or reverse. Very small students (e.g., 0.6B) get large relative gains but remain far from large teachers (e.g., ~44% vs ~91% on MATH-500).

- Matching a Chinese open model of performance X requires more than distilling it. A competitive pretraining base, sufficient student capacity, architecture efficiency (especially MoE designs), and heavy post-training/RL are still needed. Pure distillation on teacher outputs does not erase those differences.

- Western open-releasing labs (Meta, Reflection, Mistral, NVIDIA, etc.) have not closed the gap primarily because they allocate less priority, compute, and post-training intensity to their open models as flagship products compared with Chinese labs that treat strong open releases as the main product.

- The practical result is a persistent open-weight gap driven more by differences in training scale, post-training focus (especially coding/agentic), and strategic priority than by who can distill whom.

## Key References

- DeepSeek-R1 paper: https://arxiv.org/abs/2501.12948
- Reflection Beam announcement: https://reflection.ai/blog/introducing-beam
