# Audit: `tcm-doctor` skill

**Date:** 2026-11-17
**Scope:** `SKILL.md` (394 lines) + 6 reference files (2,490 lines). `herbal-medicine.md` and `SKILL.md` were read in full. The other five files were spot-read in their safety, evidence and protocol sections, plus a keyword sweep. The skill was not edited.

**Verdict:** The structure and clinical scaffolding are strong: the framework table, the Four Examinations, root/branch workflow, the output template and the quality checklist. There are three kinds of problem:
1. **Factual errors** in places where a mistake is costly: herb identity, emergency rules and organ pattern tables.
2. **Safety gaps** around toxic herbs and stacked protocols.
3. **Evidence claims** that are stronger than the literature supports. That goes against the skill's own "intellectually honest" rule.

---

## P1: Fix first (factual errors / safety)

| # | Location | Issue | Fix |
|---|---|---|---|
| 1 | `herbal-medicine.md` §3 Heat-clearing | **"Huang Qi (Scutellaria baicalensis)"**: wrong pinyin. Scutellaria is **Huang Qin (黃芩)**. The note that follows ("distinguished from Huang Qi… despite similar pinyin") then repeats the confusion. Mixing up Astragalus and Scutellaria is a real prescribing error. | Rename to Huang Qin and fix the note. |
| 2 | `herbal-medicine.md` §5 | "Berberine (from Huang Lian, Huang Bai, **Huang Qi**)". Astragalus has no berberine, and neither does Scutellaria (its main actives are baicalin/baicalein). | Sources: Huang Lian, Huang Bai (add San Ke Zhen if wanted). |
| 3 | `herbal-medicine.md` Orifice-opening "Clinical rule" | "**Open** = strong pulse, clenched jaw, closed fists… Open = Bi pattern." This is reversed and contradicts itself. Clenched jaw and strong pulse are **Closed (Bi 閉)**. Open hands and profuse sweat are **Collapse (Tuo 脫)**. In an unconscious patient this is the most important distinction in the section. | Rewrite: "Closed (Bi) = … open the orifices; Collapse (Tuo) = … do NOT open, rescue Yang." |
| 4 | `SKILL.md` Zang-Fu table, Kidney row | Kidney Yang deficiency sits in the **"Excess/Stagnation"** column. Classically the Kidney has no excess patterns. | Move it to the deficiency column (Yin / Yang / Jing) and mark the excess cell "— (Kidney: deficiency only, classically)". |
| 5 | **Aconite (Fu Zi)**: all files | Fu Zi appears in Jin Gui Shen Qi Wan, You Gui Wan, Fu Zi Li Zhong Wan, Shen Fu Tang and Zhen Wu Tang, and **cardiotoxicity is never mentioned**. This is the biggest toxicity gap in the skill. | Add a materia medica entry: processed form only (Zhi Fu Zi), prolonged pre-decoction, arrhythmia risk, contraindicated in pregnancy. |
| 6 | Mineral/animal toxins | An Gong Niu Huang Wan and Zi Xue Dan contain **cinnabar (mercury)** and, for An Gong, **realgar (arsenic)**. Neither is flagged. Xi Xin (in Dang Gui Si Ni Tang) has an aristolochic-acid issue and the classical dose ceiling, and is not flagged either. | Add a "Toxic / restricted substances" block to §4 of `herbal-medicine.md`. |
| 7 | Emergency boundary contradiction | `SKILL.md` says "stroke… altered consciousness → do not apply TCM". `herbal-medicine.md` then gives An Gong Niu Huang Wan for "**Stroke (ischaemic, early)**" and Su He Xiang Wan for "**cardiac events**". Huang Lian Jie Du Tang is listed for "**sepsis support**" and Yin Qiao San for "early COVID". | Recast these as historical/hospital-setting indications only. Add "never in place of emergency care" at the point of use. |
| 8 | Crisis handling | The skill triggers on anxiety and depression, and `modern-integration.md` has a depression section, but **no file mentions suicidal ideation or self-harm**. The emergency list also leaves out: high fever in infants, pregnancy bleeding, acute abdomen, sepsis signs, and red flags such as unexplained weight loss. | Expand the emergency redirect in `SKILL.md`. For SA, the SADAG helpline is a natural default (*check the current number before hard-coding it*). |
| 9 | `longevity-protocols.md` "Modern longevity pharmacology… (**not contraindicated**)" | Berberine 500 mg twice daily is called "not contraindicated". In fact it has CYP3A4/2D6 inhibition, adds hypoglycaemia risk on top of diabetes drugs, and is contraindicated in pregnancy and in neonates. The same protocol stacks Dan Shen + San Qi + Gou Qi Zi + Ren Shen + Wu Wei Zi + berberine and gives no combined bleeding or CYP warning. Gou Qi Zi + warfarin interaction case reports are not mentioned at all. | Remove "not contraindicated" and add a stacking warning. |
| 10 | `longevity-protocols.md` He Shou Wu | The skill presents it as a "powerful Jing-level anti-ageing" herb for long-term use and implies the processed form (Zhi He Shou Wu) is safe. Liver injury has also been reported with processed products (*fairly confident, though I haven't checked the current case literature here*). Zi He Che (human placenta) is credited with "IGF-1, EPO" without support, and its infection/sourcing risk is not mentioned. Gui Ban Jiao (tortoise) is not flagged for CITES/sourcing. | Reduce the claims and add sourcing/legal notes. |

## P2: Evidence calibration (overclaims)

These conflict with the skill's own "Evidence Note" requirement. They are my reading of the Cochrane/major RCT literature as of my training. Please verify before relying on them.

- **Acupuncture for fertility/IVF**: `SKILL.md` says "moderate". The large RCTs (e.g. Smith et al., JAMA 2018) were null. `modern-integration.md` already says "Contested", so `SKILL.md` contradicts its own reference file.
- **Chronic low back pain "Strong (multiple Cochrane)"**: the Cochrane 2020 review found a small effect over sham at low-to-moderate certainty, possibly below clinical importance. Downgrade to Moderate.
- **Chronic pain "strong" in general (`SKILL.md`)**: the Vickers IPD meta-analysis supports a modest effect over sham. "Strong" overstates it.
- **Depression: "comparable to antidepressants"**: Cochrane rates the evidence low certainty. Downgrade.
- **Hepatitis herbal support "moderate to strong"**, **Liu Wei for menopause "good evidence"**, and **Cistanche for Alzheimer's**: these rest on small trials, mostly single-country. Mark them low certainty.
- **Telomerase / sirtuin / "stem cell maintenance"** claims (Astragalus/TA-65, Rg1, He Shou Wu) are preclinical or commercially sponsored. "Kidney Jing ↔ telomere… both preserve with the same interventions" is presented as fact but has no support.
- **"Weak evidence ≠ ineffective, just understudied"** (`SKILL.md`): true in some cases, but stated as a blanket rule. Some interventions *have* been studied well and come out null. Ask the skill to say which case applies.
- **"1 month of treatment per year of illness"** and the organ-clock windows (e.g. "Kidney regeneration 5–7 pm"): label these as traditional heuristics, not clinical facts.
- **"HRT… the two work well together"**: there is no evidence for this, and phyto-oestrogenic herbs (e.g. Dang Gui) argue for caution.

## P3: Internal consistency / content accuracy

- **Dan Shen + warfarin** has two different severities: "near-contraindicated" (§3) and "HIGH — contraindicated" (§4 table, which also lists Dan Shen in two rows). Pick one.
- **Five Elements "Insulting (Wu 侮)"** is defined wrongly. Insulting means the *controlled* element counter-attacks its controller (e.g. Wood insults Metal: Liver Fire → cough). The example given, "Metal fails to control Wood", describes under-control, not insulting. The ASCII cycle diagram is also hard to read.
- **Pulse block**: "Wiry" is listed under *Width* (it is a quality), and "Depth" repeats "Location".
- **San Qi, "the only herb that does both"** (move and stop bleeding) is overstated. Pu Huang and Qian Cao are classically described the same way.
- **Yunnan Baiyao** is called a "classical formula". It is an early-20th-century proprietary formula.
- **Xue Fu Zhu Yu Tang**: "Si Wu Tang + Chai Hu Shu Gan structure" is imprecise. More exactly it is Tao Hong Si Wu Tang (with Sheng Di/Chi Shao) + Si Ni San + Jie Geng, Niu Xi.
- **Chai Hu "Drug interaction: hepatotoxicity"**: hepatotoxicity is not an interaction. The documented interaction is Xiao Chai Hu Tang + interferon-α → interstitial pneumonitis.
- **Huang Qi + cyclophosphamide "may potentiate"**: I'm not certain this has any basis. Cite it or remove it.
- **Mu Tong note**: name **Guan Mu Tong** (Aristolochia manshuriensis) as the banned species, so the substitutes (Chuan Mu Tong, Tong Cao) make sense.

## P4: Prompt engineering / mechanics

1. **Broken reference paths.** `SKILL.md` points to `/mnt/skills/user/tcm-doctor/references/...` (a claude.ai path). In this environment the files are at `~/.claude/skills/synced/<id>/tcm-doctor/references/`. Several in-body links use `/references/x.md`, which resolves to the filesystem root. **The model may never load the reference files.** Use relative paths: `references/herbal-medicine.md`.
2. **Over-broad trigger.** The description fires on "chronic fatigue, insomnia, hormonal imbalance, anxiety, digestive issues". Your `medical-diagnostician`, `sleep-expert`, `psychologist`, `clinical-nutritionist` and `longevity-expert` skills claim the same queries, so routing will be unpredictable. Narrow it to "when the user mentions TCM/Chinese medicine/acupuncture/herbs, or asks for a TCM perspective".
3. **Fabricated credentials** ("Board-certified… multiple lineage transmissions"). Persona text like this makes the model sound more authoritative than it is, and it clashes with your own preference for flagging uncertainty. Keep the voice, drop the claimed credentials. For example: "Respond with the depth of a senior clinician."
4. **"Always search for"** systematic reviews, interaction databases and trials, combined with search triggers on *any* herb, means a web search on almost every turn. Also, Natural Medicines Database is paywalled. Limit it to: any specific herb-drug pair, a safety concern, or an evidence question.
5. **Medication/pregnancy intake is not in the workflow.** "Always ask about all concurrent medications" appears only at the bottom of `herbal-medicine.md`. Add it as Step 0 of the Clinical Workflow in `SKILL.md`: meds, pregnancy/breastfeeding, liver/kidney disease, age.
6. **No dosing policy.** Formulas have no doses, but the longevity file gives specific grams and mg. Decide whether the skill gives doses. If it does, add the caveat that doses are indicative and must be confirmed by a practitioner.
7. **SA layer is thin.** Your SA-first preference is reduced to "SA-specific availability". Worth adding: practitioner registration (I believe TCM and acupuncture fall under the **Allied Health Professions Council of SA**, but *verify*), **SAHPRA** complementary-medicines regulation, and import/sourcing limits (placenta, CITES animal products).
8. **The output template is mandatory and long.** A full 9-section template for every pattern question will pad simple questions. Allow a short form.

---

## Suggested fix order
P1 items 1–3 (one-line text fixes) → P4.1 (paths; it decides whether the references load at all) → P1 items 5–9 (safety blocks) → P4.2 (trigger) → P2 recalibration → the rest.
