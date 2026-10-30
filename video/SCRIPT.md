# SCRIPT — BARRED: Evidence-Gated Security Fix Review

**Track:** Meta Global AI Developer Hackathon — Push the Frontier  
**Model:** Meta Muse-Glimmer-30B  
**Target Duration:** 3:00 (180s)  
**Tone:** Technical, authoritative, forensic, product-focused  

---

### Act 1: The Disclaimer Crisis (0:00 - 0:30)
Look at this modal. Every modern AI coding platform is forced to display the same disclaimer: "AI coding agents have security limitations. Verify all actions taken by the agent."
Why? Because large language models are probabilistic storytellers. They will write persuasive, authoritative explanations claiming code is safe, even when a fatal memory corruption flaw remains wide open. The industry dumped the entire verification burden back onto human developers.
Today, we are changing that. This is BARRED: an AI security reviewer that replaces legal disclaimers with mathematical proofs.

### Act 2: Architecture · Meta Muse-Glimmer Meets AST Gates (0:30 - 0:55)
Instead of asking an AI model to write free-form security verdicts, BARRED pairs Meta’s open-weight Muse-Glimmer-30B with deterministic Abstract Syntax Tree evidence gates.
Running locally on Apple Silicon via Mirai, Muse Glimmer acts as the high-cognition triage engine: it reads the diff, traces developer intent, and selects from a strict set of compiler-extracted candidate receipts—C1 through Cn.
The model cannot author claims out of thin air. Our deterministic engine checks control-flow dominance, verifying that the defensive guard precedes and bounds the memory sink on every reachable path.

### Act 3: Case 1 · Machine-Verified Safety (0:55 - 1:25)
Let’s see it live on Seed 42. A developer patches safe_copy, adding an if-statement checking len against cap before calling memcpy.
In round zero, Meta’s Muse Glimmer analyzes the patch and selects candidate C1—an upper-bound reject invariant.
BARRED’s deterministic gate instantly engages. It verifies all seven structural checks: the guard anchor is exact, the control flow dominates the sink, and the value relations match.
Execution halts immediately with validated counter-evidence. The verdict is PASS: a machine-verified proof that the buffer overflow is impossible.

### Act 4: Case 3 · Blocking Model Hallucinations (1:25 - 1:55)
Now consider the trap: a developer submits process_packet with a superficial check: if len equals zero, return.
A standard LLM often gets fooled, confidently arguing that empty edge cases are resolved. In our audit, the model attempted to assert candidate C1.
Under BARRED, the deterministic gate intercepts the claim immediately. The AST extractor confirms that no upper-bound guard dominates the memcpy sink.
The hallucination is caught cold. The verdict is BLOCKED. BARRED refuses to let model confidence substitute for mathematical proof.

### Act 5: Case 2 · The Honest Epistemic Boundary (1:55 - 2:25)
What happens when code calls an unknown third-party library wrapper, like gdImageJpegPtr?
In round zero, Muse Glimmer was tempted to guess. But our deterministic gate rejected the guess, and under progressive reflection in round one, the model conceded the truth: outcome unresolved.
This is the holy grail of enterprise security: an AI reviewer that knows its own proof boundary. It returns UNRESOLVED with an explicit domain notice, refusing to invent either a false pass or an ungrounded exploit.

### Act 6: Conclusion · Grounding the Frontier (2:25 - 3:00)
Meta gave the world Muse Glimmer and Llama—dense, private, open-weight models capable of running locally without data exfiltration risks.
BARRED gives them mathematical grounding.
Three visible outcomes: PASS with proof, BLOCKED on hallucination, and UNRESOLVED on unknown domains.
No more disclaimers. No more blind trust. Just verifiable security fix review.
We are BARRED. Thank you.
