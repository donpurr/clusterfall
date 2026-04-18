# CLUSTERFALL

> A hidden-role multiplayer game where LLM agents race to stabilize (or secretly corrupt) a cascading prompt graph before the cluster collapses.

🎮 **Play now**: https://donpurr.github.io/clusterfall/

Built for **VibeJam 2026**.

---

## Premise

A recursive prompt tree is being processed across a distributed cluster. Most players are **Honest Agents** — their job is to stabilize every node before corruption takes over. But one player is secretly a **Hallucinator**: they must poison the graph without being caught.

Three rounds. One traitor. Trust no one.

---

## Roles

| Role | Goal |
|---|---|
| **Honest Agent** | Complete tasks at stations to reduce corruption. Vote out the Hallucinator between rounds. |
| **Hallucinator** | Sabotage stations, poison the prompt graph, avoid being voted out. |
| **NPC Hallucinator** | Spawns automatically when only 2 human players are connected. Wanders and poisons passively. |

Your role is shown only to you at the start of each round via a flash toast. The **Hidden Layer** panel is visible only to the Hallucinator.

---

## Controls

| Key | Action |
|---|---|
| `W A S D` | Move |
| `Mouse` | Look around |
| `E` | Interact with a station / confirm action |
| `R` | Spike (used in Anneal task) |
| `Escape` | Release mouse / open menu |
| `Click` | Lock mouse pointer |

---

## Task Types

When you reach a glowing station and press `E`, you get one of seven mini-games:

| Task | How to complete |
|---|---|
| **Hold** | Hold `E` until the progress bar fills. |
| **Sequence** | Match the displayed `W A S D` key sequence exactly. |
| **Gradient** | Move the cursor with `WASD`, press `E` to commit each step toward the target. |
| **Packer** | `W/S` cycles chunks, `Q` toggles selection, hold `E` when budget and relevance are both valid. |
| **Beam** | `WASD` moves between branches, `E` locks the highest-scoring beam. |
| **Embed** | `WASD` moves the selector, `E` picks the embedding nearest to the target. |
| **Anneal** | Hold `E` to cool the temperature, tap `R` to spike it — fill both target bands. |

Tasks scale in complexity with player count.

---

## Multiplayer

The game uses **PeerJS** (WebRTC) for peer-to-peer connections with no server required.

- On load the game automatically tries to claim one of 5 fixed room slots (`clusterfall-0` … `clusterfall-4`).
- The first player in a slot becomes the **authority** (assigns roles, drives round state).
- If all 5 slots are taken you join as overflow and connect to the existing cluster.
- Up to **5 players** per session. Works cross-browser and cross-device.

No accounts, no sign-up — just open the link and play.

---

## Winning

**Honest Agents win** if they stabilize the graph across all 3 rounds (corruption stays below 100%) and/or successfully vote out the Hallucinator.

**The Hallucinator wins** if corruption reaches 100% in any round, or survives all 3 rounds without being voted out.

---

## Tech

- Vanilla JS + Three.js (3D scene)
- PeerJS (WebRTC P2P mesh networking)
- Single `index.html`, zero build step
