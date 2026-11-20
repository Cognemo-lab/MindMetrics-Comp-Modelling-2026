# Batch 3 (B3): time-stamped analysis plan — draft v0.3

**Project:** Tracing reliability through a multi-task computational phenotyping pipeline (cascade paper)
**Author:** Pamina Laessing, Povilas Karvelis, Andreea Diaconescu, Peter Dayan  
**Date of this version:** November 20, 2026
**Status:** Time-stamped analysis plan deposited in a public GitHub repository (https://github.com/Cognemo-lab/MindMetrics-Comp-Modelling-2026). It is **not** a registered report or a preregistration filed with a registry. Its purpose is to document and fix our analysis decisions before we examine the B3 data.
**Data-access statement:** B3 data not yet collected


---



## 1. Why we are collecting a third deployment (B3)

Batch 1 (B1) and batch 2 (B2) were the discovery deployments of the MindMetrics task battery in help-seeking populations recruited through Prolific. The common samples comprised 111 participants in B1 and 77 in B2. Both deployments included four tasks, two sessions per participant, and the HiTOP/INQ clinical battery. Across these deployments, we found that:

- Clinical self-report is reliable and forms stable subgroups across deployments.
- Behavioural reliability is moderate (task medians ICC ≈ .40–.61). Parameter reliability is lower and depends on the task and on the fitting method.
- Within-task subgroups (K = 2) appear in BART and Fish only. Their T1–T2 agreement (κ = .22–.53) sits well below the prevalence-limited ceiling (.69–.82).
- Change variance between sessions exceeds estimation noise (median ratio 1.2–7.4), but change does not co-fluctuate across tasks.
- Cross-task associations do not replicate across deployments: a bounded null.
- Task–clinical correlations sit at or below the attenuation ceiling (max |ρ| ≈ .2), with low power at these sample sizes (power at r_true = .2 of .12–.35).

Taken together, these findings do not tell us whether the null results and lack of replication reflect **insufficient data** (too few participants or trials) or **limitations of the method** (task design, modelling, or estimation). B1 and B2 also lacked a **positive control**. We therefore could not establish that the pipeline would detect shared structure in cases where we had reason to expect it, making the cross-task null results difficult to interpret.

B3 is a confirmatory deployment intended to address these limitations. It has three aims:

1. **Replicate** B1 conditions (identical tasks to B1, with Fish matching B2's three-block version and mirrored demographic distribution) at N ≈ 600. This will allow us to replicate the B1 results using the same task versions; comparisons between B1 and B2 were previously complicated by changes to the tasks.
2. **Add two tasks** with published reliability and designed construct overlap with the existing battery:
  - a Pavlovian Go/NoGo task ("Robot", following Zorowitz et al. 2025), which overlaps with Space Explorer on Pavlovian bias and learning;
  - a prospect-theory gambling task (following Mkrtchian et al. 2023), with a weaker overlap with BART on risk preference.
  These tasks provide (i) a reliability benchmark against published estimates and (ii) a test of convergent and discriminant validity, which serves as the paper’s positive control.
3. **Test data volume against method.** We will specify the predictions from B1/B2 in advance (Appendix A), then use the larger B3 sample to assess whether each limitation is primarily due to data volume or to the method.

---



## 2. Design


| Item                   | Specification                                                                                                                                                                                                                                                                     |
| ---------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Platform / recruitment | Prolific; same screening as B1/B2; forced demographic distribution to match B1 deployment                                                                                                                                                                                         |
| N                      | 600 participants recruited at T1. The analysable sample will be smaller after retest attrition and exclusions; we anticipate an analysable N of 400–600.                                                                                                                                                          |
| Sessions               | T1 and T2, two-week retest interval; all questionnaires and six tasks at both sessions                                                                                                                                                                                            |
| Tasks                  | BART, Fish (3 blocks, as in B2), Jungle, Space Explorer (reversal after trial 50), Robot Go/NoGo (240 trials, rewarding and punishing states), prospect-theory gambling (calibration phase (50 mixed and 40 gain-only trials) and second phase (64 mixed and 56 gain-only trials) |
| Task order             | randomised                                                                                                                                                                                                                                                |
| Clinical measures      | HiTOP , INQ, GCSQ                                                                                                                                                                                                                                                                 |
| State measures         | same as B2, collected at T1 and T2 before game play.                                                                                                                                                                                                                  |
| Exclusions             | Frozen B1/B2 rules (§2.1)                                                                                                                                                                                                                                                         |




### 2.1 Exclusions and analysis sample

We will apply task-quality exclusion criteria separately to each task and session (B3T1 and B3T2), using the same rules as in B1/B2 wherever applicable. These criteria do not depend on the model being fitted and are specified before we inspect the B3 data.

**BART.** We will exclude a participant if their longest run of identical pump counts exceeds the deployment mean by more than two standard deviations (sample SD). The mean and SD are computed within the deployment over pooled T1 and T2 participant–session rows. The cut was 9.20 in B1 (mean 4.20, SD 2.50; a streak of 10 or more excludes) and 21.78 in B2 (mean 9.14, SD 6.32). The B2 cut lies above the maximum possible streak in a 20-trial session, so no B2 participant was excluded by this rule. The cut is recomputed on B3 by the same rule and reported.

**Fish.** We will exclude a session if any of the following conditions are met:
1. the continuous lake-A probability slider was left unmoved (start position equal to final position) on more than 80% of trials;
2. the mean lake-A probability rating, expressed as a proportion of the response scale (0–100), falls outside [0.1, 0.9] (bounds inclusive);
3. more than 40% of probability ratings are missing.

The binary commit responses are not used for these criteria.

**Jungle.** We will apply three fixed criteria:
1. the wager slider was left unmoved (start position equal to final position) on more than 80% of trials;
2. the mean wager, expressed as a proportion of the response scale (wagers range from 1 to 10), falls outside [0.1, 0.9] (bounds inclusive);
3. more than 40% of wagers are missing.

As in Fish, these criteria apply to the continuous response and not to the binary path choice. Among participants passing them, a session is additionally excluded if either advice-taking during the stable-advice phase or the average wager lies more than two standard deviations from the mean for that session. The SD is the sample SD, computed on the participants who passed the fixed criteria, separately for each session.

**Space Explorer.** A run is excluded if any of the following hold:
1. neither block exceeds the accuracy gate (before-reversal accuracy > 0.443 or after-reversal accuracy > 0.443 is required);
2. before-reversal accuracy is at or below 0.1;
3. after-reversal accuracy is present and at or below 0.1 (a missing post-reversal block does not trigger this rule);
4. the longest streak of identical Go or NoGo responses exceeds 69.

In B1/B2, the two data-derived thresholds came from a cross-deployment two-SD screen on the screened participant–session rows: the mean of the better block's accuracy minus 2 SD (≈ 0.443), and the mean longest streak plus 2 SD (≈ 69.3, rounded down to the integer cap of 69). We will apply these performance criteria first. Of the runs that pass, we will retain only the first run associated with each Prolific ID and remove any later runs as duplicates. [[DECISION: B3 uses the same fixed thresholds (0.443, 69), or recomputes them on B3 as for BART?]]

**New tasks.** Exclusion criteria will be adapted from the respective publications, to reproduce the reliability results as closely as possible: 
Robot (starting point for exclusion based on Zorowitz et al. 2025): making either all Go or all No-Go responses on >90% of trials, or exhibiting chance-level performance on go-to-win trials. 
Prospective Gambling Task (starting point for exclusion based on Mkrtchian et al. 2023): exclusion of participants if the second session is failed. For data quality, we will consider exclusion of participants who choose the same gamble option on >90% of trials in either block.

**Analysis samples.** A participant will be included in the relevant analysis sample only if they pass the required task screens at both sessions. For replication analyses, we retain participants who pass the four replication tasks at both sessions. For convergent analyses, we keep a separate sample of participants who pass all six tasks at both sessions, provided this sample has more than 10 participants. We will report participant flow at each stage (recruited, T1, T2, task-level pass counts, and final analysis samples), along with the number of exclusions attributable to each rule.


### 2.2 Clinical factor scores

We will project B3 responses onto the pooled B1/B2 EFA loadings. 

---



## 3. Models (frozen before B3 analysis)


| Task           | Model carried into B3                                                                                                                            | Status at time of writing |
| -------------- | ------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------- |
| BART           | Single-δ model                                                                                                                                   | Locked                   |
| Fish           | Leaky integrator (HGF fails recovery: sa0_l2 ICC = .46)                                                                                          | Locked                    |
| Jungle         | Kalman filter with free omega, fixed ze=2 and linear regression for choice with b1 and b2                                                        | Locked                      |
| Space Explorer | RL-Pf model                                                                                                                                      | Locked                      |
| Robot          | Published winning model (Zorowitz et al., 2025), recovery check only, no selection ladder                                                        | Locked                |
| Gambling       | Prospect-theory model as in Mkrtchian et al., 2023. Recovery check only                                                                          | Locked                |


**Selection rule for the B3 model-comparison rerun:** We will consider only candidate models for which all free parameters achieve recovery ICC > .5, and select the candidate with the lowest iBIC. If no candidate meets this criterion, we will select the model with the best parameter recovery and report the recovery level it achieves.

**Fitting conventions:** We will use eHBI with 20 outer initialisations. Parameters will be analysed on the unconstrained fitting scale; analyses on the native scale will be reported as a sensitivity check. iBIC will be the primary model-comparison measure.

**Statistical conventions:** ICC(3,1) will be the primary reliability estimate, with ICC(A,1) also reported. Confidence intervals will be based on 2,000 participant-level bootstrap draws and percentile intervals. For exploratory analyses, we will control the false discovery rate using the Benjamini–Hochberg procedure within each deployment × measure family × session. The confirmatory family in §6 is treated separately. We will record one random seed for each analysis.

---



## 4. Hypotheses and planned analyses

The analyses are organised around the paper’s guiding questions (Q0–Q6). Questions Q0–Q4 were first examined in B1/B2; B3 will revisit them using the same task versions. Questions Q5 and Q6 address the issues that motivated the third deployment. Analysis identifiers (for example, H1.2) correspond to the analysis list in the manuscript. We mark **confirmatory** hypotheses as **[C]**. All other analyses are marked **[E]**: they are planned in advance and will be reported in full, but will be interpreted primarily as estimation rather than hypothesis testing.

The following conventions apply across analyses:
- **Sample:** the B3 analysis samples defined in §2.1.
- **Reliability:** We will report both ICC(3,1) and ICC(A,1), fitting T1 and T2 separately.
- **Uncertainty:** We will use 2,000 participant-level bootstrap resamples to calculate percentile 95% confidence intervals. Medians and differences will be recalculated within each resample.
- **Parameters:** We will analyse the free parameters of the retained model on the unconstrained fitting scale. Unless stated otherwise, “hierarchical” refers to K = 1 eHBI.
- **Correlations:** Spearman correlations will be used unless noted otherwise.
- **Multiplicity:** For exploratory analyses, we will apply Benjamini–Hochberg FDR correction within deployment × measure family × session. Confirmatory tests are described in §6.

### Q0. Do the tasks reveal the computations they were designed to elicit?

- **H0.1 [E] Model ranking at larger.** Fit the candidate set per task with K = 1 eHBI (20 outer starts) on B3T1, and repeat the ranking at B3T2. Report iBIC and predictive fit. *Prediction:* the B1-selected model remains preferred.
  - If a richer candidate now wins and passes recovery, we take this as evidence that the B1/B2 selection was partly limited by data volume.
  - Regardless of outcome, the B1-locked model stays the model for all downstream B3 analyses, so comparisons with B1/B2 remain valid. The B3-preferred model is reported as sensitivity.
- **H0.2 [E] Parameter recovery.** For each candidate:
  - draw parameters from each participant's fitted posterior;
  - simulate on that participant's trial schedule;
  - refit with the same hierarchical pipeline;
  - compute ICC(3,1) between generating and recovered values per free parameter.

  Model recovery (simulate from each candidate and refit all) is reported in the SI.
- **H0.3 [E] New tasks.** Fit the published models with K = 1 eHBI and check parameter recovery as in H0.2, without a selection ladder:
  - Robot: the Pavlovian Go/NoGo model of Zorowitz et al., 2025;
  - Gambling: the prospect-theory model with loss aversion, risk aversion and choice sensitivity, as in Mkrtchian et al., 2023

### Q1. How reliable is each stage, and how much of the unreliability is estimation noise?

- **H1.1 [E] Cascade.** Compute T1–T2 ICCs for:
  - the clinical stage: 8 clinical factor scores, INQ-15 and GCSQ subscales ;
  - behavioural summary measures derived from the model inputs, using the locked list ;
  - retained-model parameters from individual MAP and hierarchical fits, with each parameter's mean posterior SD .

  Report task medians with CIs, including the new tasks. *Expectation:* the B1/B2 ordering replicates: clinical > behaviour > parameters.
- **H1.2 [C] Unreliability exceeds estimation noise.**
  - *Method:* compute the model-implied ceiling for each participant. Simulate two sessions from their own fitted parameters on their own trial schedule, refit both with the identical pipeline, and take the ICC between the two refits (20 replicates for individual fits; 10 for hierarchical).
  - *Prediction:* for the replication tasks, the median ICC_obs / ceiling ratio across retained parameters is < 1, with the bootstrap CI excluding 1, replicating B1/B2.

### Q2. Do within-task subgroups exist, and are they stable across sessions and deployments?

- **H2.1 [C] Subgroups replicate.**
  - *Method:* per task × session, run eHBI with K = 1 and K = 2 (same model, separate group priors) and 20 outer starts. A basin is a set of starts with pairwise ARI > .9 on hard labels. K = 2 is accepted only if iBIC prefers it and the best-EL basin holds ≥ 3/20 starts.
  - *Prediction:* K ≥ 2 is accepted for BART and Fish, and K = 1 for Jungle and Space Explorer.
- **H2.2 [C] Cross-deployment stability.**
  - *Method:* fix B1's K = 2 group-level priors and weights per splitting task, and compute responsibilities for B3 participants. Compare these with B3's own K = 2 labels (κ after Hungarian matching), and correlate B1 and B3 component means.
  - *Prediction:* κ exceeds a null from 5,000 shuffles, and matched component means correlate positively.
  - subgroup stability is only tested across batches that split into clusters and have the same task design across batches
- **H2.3 [E] Subgroup-informed reliability.** Compute responsibility-weighted parameters θ̄ = Σ_k r_k θ_k and their T1–T2 ICC. Report the difference from the K = 1 hierarchical ICC with a bootstrap CI.
- **H2.4 [E] Clinical benchmark.**
  - Run k-means on z-scored T1 clinical features, with k chosen by the gap statistic. Assign T2 to the T1 centroids and compute ARI against 5,000 permutations.
  - Also assign B3 participants to the B1/B2 centroids.

### Q3. Do tasks share latent structure beyond what their reliability permits us to detect?

**Replication of the B1/B2 bounded null [C].**

- **H3.1 [C].** compares between-task correlations of behavioural measures and hierarchical parameters, at T1 and T2.
  - *Bounded null:* per pair, TOST against ±SESOI (see §5 for the bound). Also report BF01 per pair.
  - *Omnibus:* S = Σ r² over between-task pairs, against a null from 5,000 within-block permutations of participant IDs. *Prediction:* S does not exceed the null.
  - *Pattern replication:* correlate the B1 and B3 vectors of between-task r on identically defined measures. Read this against a B1 split-half ceiling (200 splits).
- **H3.2 [E] Cross-task subgroup association.** φ between BART and Fish hard labels at T1 (Fisher exact test). Expected φ_obs = φ_true √(κ_BART κ_Fish). Power is reported for φ_true ∈ {.1, .2, .3, .5}.

**Positive control: designed construct overlap.**

- *Measures:* Pavlovian bias is measured in two ways:
  - **Model parameter:** the fitted per-participant Pavlovian bias parameter in each task's model, on the unconstrained scale.
  - **Behavioural index:** for each state (cue), accuracy on Pavlovian-congruent trials minus accuracy on Pavlovian-incongruent trials, aggregated within condition.
- *Primary pairing:* Robot punishment conditions with Space Explorer avoid conditions, which share aversive valence.
- *Testing:* correlations are computed at T1. T2 serves as replication and the T1/T2 average as sensitivity. For each pair we report r, the reliability bound √(ICC_a × ICC_b), r / bound, and the disattenuated estimate.

Primary convergent hypotheses [C] (one-sided, Holm within the family of three):

| ID | Pair | Prediction |
|---|---|---|
| H3.5a | Pavlovian bias parameter: Robot (punishment) ↔ Space Explorer (avoid) | r > 0 |
| H3.5b | Pavlovian bias behavioural index: Robot punishment ↔ Space Explorer avoid | r > 0 |
| H3.5c | Learning rate/Reward sensitivity: Robot ↔ Space Explorer α | r > 0 (expected smaller than H3.5a; Space Explorer includes a reversal after trial 50 and forgetting) |


Secondary convergent hypotheses [C, secondary family, Holm]:

| ID | Pair | Prediction |
|---|---|---|
| H3.5d | Pavlovian bias across valence: Robot reward (win) conditions ↔ Space Explorer escape conditions (parameter and behavioural index) | r > 0, and smaller than H3.5a/b |
| H3.5e | Risk preference: gambling-task risk aversion ↔ BART δ | r > 0 if the risk-aversion parameter is coded so that higher = more risk averse. Expected modest: BART risk preference is learned under uncertainty, so the construct match is weaker. |

Discriminant hypotheses [C]:

- **H3.5f** The same parameters across non-matched tasks (Robot ↔ BART δ; gambling ↔ Space Explorer): |r| inside the equivalence bound (TOST; §5).
- **H3.5g** Each primary convergent correlation exceeds its matched discriminant correlations.

**Method-variance control [E].** Robot and Space Explorer are both Go/NoGo formats, so some convergence may come from shared format or engagement rather than the construct. We report:
- go-bias convergence alongside Pavlovian-bias convergence;

If Pavlovian-bias convergence does not exceed go-bias convergence, or disappears after partialling, we attribute it to shared format or engagement rather than to the construct.

*Interpretation rule:* if the convergent r is significant and near its reliability bound, with discriminant pairs inside their bounds, the pipeline detects shared structure when it is designed in. The B1/B2 cross-task nulls then become interpretable as absence of detectable shared structure among the original tasks.

### Q4. Do task measures capture self-reported clinical dimensions beyond demographics, and what could this design detect?

This question examines whether task measures converge with self-reported clinical dimensions, providing a validity check. 

- **H4.1 [E] Task–clinical correlations.** Correlate behavioural measures and hierarchical parameters with the 8 clinical factors, INQ-15 and GCSQ subscales at T1 (FDR). The largest |ρ| is tested against a null from 5,000 permutations of clinical rows.
- **H4.2 [E] Detectability.**
  - r_obs = r_true √(ρ_task ρ_clin), with ρ taken from Q1.
  - Report the required N for 80% power at r_true ∈ {.1, .2, .3}, at α = .05 and at the Bonferroni α for the number of task–clinical correlation tests, plus power at the realised N.
  - The B1/B2 values are the frozen predictions for Q5.
- **H4.3 [C] Information beyond demographics, B1 → B3 transfer.**
  - *Targets:* each clinical score (8 HiTOP-derived factors, INQ, GCSQ).
  - *Models:* demographics (age, sex and treatment status), behaviour, parameters and subgroup responsibilities.
  - *Fitting:* ridge regression; 5 × 5 nested cross-validation × 10 repeats within B1; the B1-trained models are then tested on B3.
  - *Metric:* out-of-sample R² of (ii) minus (i), against a null from 1,000 label permutations run through the whole procedure.
  - *Prediction:*  B1/B2 imply ΔR² ≈ 0. At the B1 training N, an optimistic in-sample test needs an incremental R² of about .20 or larger for 80% power once the behavioural measures, parameters, and responsibilities are entered together; we will state the exact predictor count and complete-case training N. A B3 estimate below that range will be reported as a null bounded by the training sample.
- **H4.4 [E] Subgroups and self-report.**
  - Compute clinical differences between BART and Fish subgroups at T1.

### Q5. Where a link fails, is it limited by data volume or by method?

B3 retains the B1 design while increasing the target sample to approximately 600 participants. The limitations observed in B1/B2 therefore lead to different predictions for B3. We will finalise the predictions from Q1 and Q4, together with the bounds from Q3, before analysing B3 (Appendix A).

- **H5.1 [C] Per-person reliability does not improve with N.**
  - *Method:* for each identical task, measure and parameter, compute ICC_B3 − ICC_B1 with a bootstrap CI (each deployment resampled separately). Do the same for the H1.4 ceiling.
  - *Test:* equivalence (TOST, 90% CI) at the bound detectable with 80% power (§5). The bound is set mainly by B1's n = 111, so we also report ΔICC with its CI as an estimate.
  - *Reading:* no change points to a method limit; a change means the B1 estimate was noise.
  - *Caveat:* hierarchical ICCs can rise with N through better group priors. For hierarchical stages this is therefore a two-sided estimation question [E].
- **H5.2 [C] Predicted vs observed associations.**
  - *Method:* compare B3 observed task–clinical (H4.1) and cross-task (H3.1) correlations with the r_obs predicted from B1 reliabilities. Report the proportion inside the predicted interval.
  - *Bound:* check whether B3's TOST bounds exclude an attenuated r_true = .2.
  - *Reading:* effects appearing near their predicted size → the B1/B2 null reflected low power (data-volume limit). Effects excluded at the bound → the effect is absent at that size.
- **H5.3 [C] New tasks reach published reliability.**
  - *Method:* compare ICCs of the new tasks' published measures and parameters with the published retest values (Zorowitz et al. 2025; Mkrtchian et al. 2023).
  - *Prediction:* the B3 95% CI includes the published estimate.
  - *Reading:* new tasks reach published values but the original battery stays low → the limit is the original task design. Both fall short → the limit is the population, setting or approach.
- The B3 rerun of model selection (H0.1) also feeds Q5.

| Prediction (from B1/B2) | B3 outcome | Interpretation |
|---|---|---|
| ICCs and ceilings per task × stage | Unchanged at larger N | Method limit |
| Expected observed task–clinical r and required N | Associations appear near the predicted size | Data-volume limit |
| Equivalence bounds (§5) | Associations inside the bounds | Informative (bounded) null |
| Model ranking | Richer model preferred at N ≈ 600 | Q0 partly data-volume limited |
| New-task ICCs vs published values | See H5.3 | Task design vs population/setting |
| Convergent r vs reliability bound | Overlapping tasks correlate up to their bound | Shared mechanism supported |

### Q6. Is within-person change between sessions shared across tasks, and does it track state?

B1/B2 served as the discovery deployments. In neither deployment did raw change scores co-vary across tasks. In B2 only, behavioural change exceeded the null after engagement-related change was removed (p = .017). B3 will provide the confirmatory test of this pattern.

- **H6.1 [C] Shared change.** Δ = T2 − T1 per person for each behavioural measure (primary) and parameter (secondary). Omnibus S = Σ r² over between-task pairs of Δ, against a null from 5,000 within-block permutations of participant IDs.
- **H6.2 [E] Change tracks clinical change or state.**
  - Regress each Δ measure on Δ of the 8 clinical factors and, where collected, on Δ state-questionnaire scores (sleep, rest, motivation, substance use).
  - Report the mean R² across measures against a null from 1,000 person shuffles applied to the predictors.
- **H6.3 [E] Practice effects.** Mean T2 − T1 per measure and parameter as Cohen's d_z with bootstrap CI (FDR). This quantifies the systematic session shift that separates ICC(A,1) from ICC(3,1).
- **H6.4 [E] Reliability of the co-change pattern.**
  - *Method:* split participants at random into two halves (200 splits). In each half, compute the vector of between-task correlations of Δ, and correlate the two halves' vectors. Report the mean and 95% interval over splits.
  - Compare with the same split-half statistic for T1 levels (H3.3). T1-vs-T2 comparisons on the same people are not used, because they share sampling error.
  - *Expectation:* a shared occasion state predicts a reproducible co-change pattern; independent noise predicts none. Given B1/B2, we expect pattern reliability near zero and below that of T1 levels.


---

## 5. Power and bounds for null results

**Fixed sample.** We will recruit 600 participants at T1 and will not recruit replacements. The final analysable sample will depend on attrition between sessions and task-level exclusions. We therefore present power and bounds across an analysable N of 400–600. The decision not to replace participants who drop out is a limitation (§8).

**How we will interpret null results.** We will report each null result in relation to the smallest effect that the design can detect with 80% power at the realised analysable N. We will recalculate this bound using the final sample size and report it in the paper. The current estimates (Fisher z; α = .05) are:


| Analysable N | Smallest detectable r, two-sided | Smallest detectable r, one-sided | Equivalence bound (TOST, 80% power, true r = 0) |
| ------------ | -------------------------------- | -------------------------------- | ----------------------------------------------- |
| 400          | .14                              | .12                              | ±.15                                            |
| 500          | .13                              | .11                              | ±.13                                            |
| 600          | .11                              | .10                              | ±.12                                            |


These bounds apply to observed correlations: cross-task matrices (A6), co-fluctuation of change (H6.1a), discriminant pairs (H3.5f) and task–clinical correlations (H5.2).

**Cross-task pairs (H3.2).** For comparability with B1/B2, each pair keeps the SESOI = .3 × √(ρ_a ρ_b), where ρ are the two measures' B3 ICCs. A pair's null is called informative only where this SESOI is at least the 80%-power bound above. Otherwise the result is reported as inconclusive at that pair's reliability.

**ΔICC, B1 vs B3 (H5.1).** The equivalence bound is limited by B1's n = 111 and is barely affected by the size of B3:


| ICC level | Bound at B3 N = 400 | Bound at B3 N = 600 |
| --------- | ------------------- | ------------------- |
| ≈ .6      | ±.20                | ±.19                |
| ≈ .5      | ±.24                | ±.23                |
| ≈ .3      | ±.29                | ±.28                |


These use an analytic ICC standard error; the bootstrap is used in the analysis itself.

**Task–clinical associations.** The values below assume r_obs = r_true · √(ρ_task · ρ_clin), with ρ_clin ≈ .90 (this value reproduces the table), Fisher z, two-sided α = .05. ρ_hierarchical = .1-.65.


| Task      | ρ_hierarchical | Power, N = 600, r = .2 | N for 80% | Power, N = 600, r = .3 | Smallest detectable r_true at N = 400 / 600 |
| --------- | -------------- | ---------------------- | --------- | ---------------------- | ------------------------------------------- |
| B1 Fish   | .639           | .96                    | 341       | 1.00                   | .18 / .15                                   |
| B1 BART   | .405           | .84                    | 539       | .99                    | .23 / .19                                   |
| B2 Jungle | .350           | .80                    | 604       | .99                    | —                                           |
| B2 Space  | .334           | .78                    | 633       | .98                    | .26 / .21                                   |
| B2 BART   | .331           | .77                    | 639       | .98                    | —                                           |
| B2 Fish   | .321           | .76                    | 659       | .98                    | —                                           |
| B1 Space  | .259           | .66                    | 842       | .95                    | .29 / .24                                   |
| B1 Jungle | .165           | .47                    | 1324      | .81                    | .36 / .30                                   |


At the expected analysable sample size, a true task–clinical association of approximately r = .2 should be detectable for Fish. It may also be detectable for B1 BART if the final analysable sample is close to 600. For Space Explorer and Jungle, null results will instead place bounds on effects in the approximate range r_true = .25–.35.

**Convergent validity (H3.5a–c; one-sided α = .05).** Attenuation by both tasks' reliabilities. Robot reliability in our sample is unknown, so we tabulate a grid against Space Explorer's B1/B2 hierarchical ICC:


| Space ρ          | Robot ρ | r_true | r_obs | Power N = 400 | Power N = 500 | Power N = 600 |
| ---------------- | ------- | ------ | ----- | ------------- | ------------- | ------------- |
| .334             | .4      | .3     | .110  | .71           | .79           | .85           |
| .334             | .6      | .3     | .134  | .85           | .91           | .95           |
| .334             | .8      | .3     | .155  | .93           | .97           | .99           |
| .259             | .4      | .3     | .097  | .61           | .70           | .76           |
| .259             | .6      | .3     | .118  | .77           | .84           | .90           |
| any of the above |         | .5     | ≥ .16 | ≥ .94         | ≥ .98         | ≥ .99         |


The design has good power to detect construct-level convergence of r_true ≈ .5 across the plausible range of analysable sample sizes. For r_true ≈ .3, power reaches at least .80 only if Robot reliability is ≥ .6 or the analysable sample is close to 600. We expect the cross-valence association (H3.5d) to be smaller and less well powered; the gambling–BART association (H3.5e) is similarly less well powered.

**ICC precision.** For an ICC near .5, the approximate 95% confidence-interval half-width is ±.14 at n = 111, ±.07 at n = 400, and ±.06 at n = 600.

## 6. Inference criteria and multiplicity

- **Confirmatory family:** H1.2, H2.1, H2.2, H3.1, H3.5a–c (primary), H3.5d–e (secondary family), H3.5f–g, H4.3, H5.1–H5.3, H6.1. 
- All other analyses will be treated as exploratory, controlled for FDR within deployment × measure family × session, and reported in full.
- We will conclude equivalence only when the entire 90% confidence interval falls within the prespecified bounds. A non-significant result that does not meet this criterion will be described as inconclusive.


---



## 7. Limitations stated in advance

- The total sample is fixed at N = 600. Attrition between sessions and task exclusions will reduce the analysable sample and, in turn, limit how tightly we can bound null results. 
- Equivalence tests comparing B1 and B3 ICCs are limited by B1's sample size (§5).




---

