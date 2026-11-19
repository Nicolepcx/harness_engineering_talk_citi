# Harness Engineering demo, banking version

By Nicole Koenigstein

Same walkthrough as the ACM talk app, on a banking use case: a client-service
operations agent at the fictional Alderline Bank handles dispute credits,
account closure and a weekly rate update.

## Go deeper

This talk is a short cut through material I cover in full elsewhere:

| | |
|---|---|
| 📕 **Book** | [**Harness Engineering**](https://learning.oreilly.com/library/view/harness-engineering/0642572422783/) (O'Reilly). The scenes in this repo follow its chapters on harness components and skills. |
| 📘 **Book** | [**AI Agents: The Definitive Guide**](https://learning.oreilly.com/library/view/ai-agents-the/0642572247775/) (O'Reilly). |
| 🎓 **Live course** | [**Harness Engineering intensive**](https://www.oreilly.com/live/intensive-harness-engineering.html) (O'Reilly). Build and ablate a harness hands-on. |

## Run it

    python -m venv .venv && .venv/bin/pip install -r requirements.txt
    .venv/bin/streamlit run app.py

No API key is needed to run it. The app replays the recordings in `recordings/`.

- `app.py`: the walkthrough (13 scenes).
- `harness/core.py`: governance, tool gateway, verifier, recorder, orchestrator.
- `harness/bank.py`: the servicing database (clients, cards, transactions, disputes, credits) and tools.
- `harness/scenes.py`, `harness/walkthrough.py`, `harness/context_sims.py`: scene definitions.
- `recordings/`: live runs of `openai/gpt-5.6-luna`. Re-record with `.venv/bin/python record.py` (needs `OPENROUTER_API_KEY` in `.env`).
- `presenter_script.md`: private speaker notes, gitignored.

What is real: the harness, the tools and the database run in every scene.
Scenes 1, 2, 3, 4 and 7 replay recorded live model runs. Scenes 5 and 6 use
scripted model turns and say so. Scenes 8, 9 and 10 call no model and are
labelled illustrations. Scene 11 runs the six tickets of scenes 2 to 7 again as
one shift and adds up the damage, next to the same tickets on the intact harness.

All data is synthetic: generated clients, published test card numbers, a fake
cloud key, and an "attacker endpoint" that is a list in memory. The bank, its
policy and the 31 skill rules are invented for the demo and do not describe
any real institution or regulation. `skills/market-update-post/SKILL.md` is a
deliberately unsafe skill written for scene 6: read it, do not install it.
# harness_engineering_talk_citi
