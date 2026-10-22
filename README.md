<div align="center">

# AgentDreamer

### Agentic 3D Motion Reasoning for Text-Controllable Physics Simulation

<p>
  <a href="https://mjmjeong.github.io/research_projects/agentdreamer/index.html"><b>🌐 Project Page</b></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="https://github.com/mjmjeong/AgentDreamer"><b>💻 Code</b></a>
  &nbsp;&nbsp;|&nbsp;&nbsp;
  <a href="#citation"><b>📄 Citation</b></a>
</p>

<p>
  <img src="https://img.shields.io/badge/status-under%20review-orange" alt="Under review">
  <img src="https://img.shields.io/badge/code-coming%20soon-lightgrey" alt="Code coming soon">
  <img src="https://img.shields.io/badge/physics-differentiable%20MPM-6f42c1" alt="Differentiable MPM">
</p>

<br>

<img src="https://mjmjeong.github.io/research_projects/agentdreamer/assets/supple_presentation_33-55.gif" alt="AgentDreamer qualitative comparison" width="820">

<br>
<sub>AgentDreamer aligns simulated motion with a natural-language instruction by planning motion explicitly in 3D.</sub>

</div>

<br>

Mijeong Kim<sup>1,*</sup> · Suho Park<sup>2,*</sup> · Junha Park<sup>2</sup> · Bohyung Han<sup>1,2</sup>

<sup>1</sup>Department of Electrical and Computer Engineering · <sup>2</sup>IPAI, Seoul National University  
<sup>*</sup>Equal contribution

## ✨ What is AgentDreamer?

AgentDreamer is an agent-guided framework for turning text instructions into physically plausible 3D motion.

Instead of using a video model as an indirect motion reference, AgentDreamer first reasons about **what should move, how it should move, and when it should move**. That explicit 3D motion plan then guides a differentiable Material Point Method (MPM) simulation.

<div align="center">

| Text instruction | 3D motion plan | Physics simulation |
|:---:|:---:|:---:|
| “Make the flower bow toward the pot.” | Structured, temporal, scene-aware trajectories | Physically constrained rollout |

</div>

## 🔥 Why 3D motion planning?

Visually plausible guidance can still miss the instruction—for example, sliding instead of rolling or moving the wrong object part. AgentDreamer grounds language in scene geometry before optimization.

<div align="center">

<img src="https://mjmjeong.github.io/research_projects/agentdreamer/assets/figure1_motivation_v3.png" alt="Motivation: video guidance can miss the requested motion" width="820">

</div>

## 🧠 Method

<div align="center">

<img src="https://mjmjeong.github.io/research_projects/agentdreamer/assets/overall_architecture.png" alt="AgentDreamer method overview" width="900">

</div>

1. **Scene-aware input.** Sampled 3D control points are projected into multiple views with consistent indices, allowing the agent to connect visible object parts to scene geometry.
2. **Agent-generated motion prior.** The agent predicts a piecewise-parametric 3D motion plan over temporal segments. The resulting motion field can be evaluated at arbitrary points in the scene.
3. **Differentiable physics optimization.** The planned trajectories supervise a differentiable MPM rollout while the simulator preserves physically plausible dynamics.

```text
Text + 3D scene  ──▶  Agent  ──▶  Parametric 3D motion  ──▶  Differentiable MPM  ──▶  Simulation
```

## 📊 Results

AgentDreamer is evaluated on 20 instructions across eight scenes. Higher is better.

<div align="center">

| Method | Open-weight Motion-IG ↑ | API-based Motion-IG ↑ | Human first rank ↑ |
|:---|---:|---:|---:|
| PhysFlow | 0.52 | −0.22 | 14.0% |
| MotionPhysics | 0.52 | −0.63 | 12.4% |
| **AgentDreamer** | **0.71** | **+0.48** | **73.6%** |

<br>

<img src="https://mjmjeong.github.io/research_projects/agentdreamer/assets/qualitative_result.png" alt="Qualitative comparison" width="900">

</div>

**Motion-IG** measures text–motion alignment through masked motion-word recovery. See the [project page](https://mjmjeong.github.io/research_projects/agentdreamer/index.html) for animations and additional qualitative results.

## 🚧 Code release

The code is currently being prepared for public release. The repository will be updated soon with environment setup, scene preparation, agent-based motion planning, differentiable MPM optimization, Motion-IG evaluation, and reproduction scripts.

Until then, please see the [project page](https://mjmjeong.github.io/research_projects/agentdreamer/index.html) for the project overview and results.

## 📚 Citation

```bibtex
@misc{agentdreamer2027,
  title  = {AgentDreamer: Agentic 3D Motion Reasoning for Text-Controllable Physics Simulation},
  author = {Kim, Mijeong and Park, Suho and Park, Junha and Han, Bohyung},
  year   = {2027},
  note   = {Under review}
}
```

## Acknowledgements

AgentDreamer builds on differentiable MPM simulation, 3D Gaussian scene representations, and multimodal foundation models. Complete dependency acknowledgements and third-party notices will be added with the code release.

## License

The license will be added together with the public code release.
