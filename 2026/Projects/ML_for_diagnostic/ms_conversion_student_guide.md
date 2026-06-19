# Student Guide — Predicting MS Conversion from CIS

*Your companion to the `ms_conversion_notebook.ipynb` notebook. Read a section here first, then do
that section in the notebook. This guide explains **what things mean and why we do them** — it
does **not** give you the answers. The answers are for you to discover.*

---

## What you're doing, and why it's exciting

When someone has their *first* neurological episode — a **clinically isolated syndrome (CIS)** —
doctors face a hard question: **is this a one-off, or the first sign of multiple sclerosis (MS)?**
Some of these patients go on to develop MS; others never do. If we could predict who is at risk
from the very first visit, doctors could treat the right people early.

**That is the question you are going to attack with machine learning.** Using real data from
hundreds of patients, you'll build a model that tries to predict who converts to MS — and, just as
importantly, you'll learn how to tell whether your model is *actually good* or just *fooling you*.

You did this same journey yesterday with the iris flowers. **The steps are exactly the same. Only
the data changed.** That's the whole point: once you know the skeleton, you can do this with *any*
dataset.

---

## How to work through this

You don't need to already know how to code. Here's how to succeed:

- 💡 **Use Gemini (the AI in Colab).** When you see a `# TODO`, read what it asks, then paste that
  description to Gemini and let it write the code. **Read the code before running it** — try to
  follow what each line does. If you get a red error, paste the error back to Gemini and ask it to
  fix it. You'll learn a lot just from reading what it produces.
- 🔧 **Turn the knobs.** Where a cell says something like `feature = "Age (y)"`, change it to a
  different feature and run it again. Poke around. You can't break anything permanently — just
  re-run.
- ✍️ **Answer the questions in *italics*.** Those are the real assignment. A plot you didn't think
  about taught you nothing. Write your answers in a text cell or a notebook.
- 🤔 **It's fine to feel confused.** This is genuinely new and genuinely hard. Confusion is the
  feeling of learning. Ask Gemini, ask a teammate, ask your teacher.

---

## The big map: five steps, every time

Every machine-learning project — in any field — follows the same five steps. Here's the whole
journey in one glance:

| Step | In plain words | The everyday analogy |
|---|---|---|
| 1. **Preprocessing** | Clean the data into tidy numbers | Washing and chopping ingredients before cooking |
| 2. **EDA** (exploring) | Look at the data before modelling | Reading the map before the road trip |
| 3. **Unsupervised** | Does the data fall into groups *on its own*? | Sorting laundry into piles without being told the categories |
| 4. **Classification** | Train a model to predict the answer | Studying for an exam using the answer key |
| 5. **Validation** | Check if the model is *really* good or just lucky | The actual exam, on questions you've never seen |

Keep this table in mind. Every section of the notebook is one of these steps.

---

## Section-by-section companion

### §2–3 Loading and first look

We download the data and take a first look: how many patients, how many features, and two things
that matter a lot:

- **Missing values.** Real data has gaps — a test wasn't done, a record was lost. A model can't
  use a blank cell, so later we'll have to fill them in or work around them.
- **Class balance.** What fraction of patients actually converted to MS? This number matters more
  than you'd think. *Here's a thought to chew on: if a lazy model just guessed "nobody converts"
  for every single patient, how often would it be right?* Figure that out — it's your "do nothing"
  baseline, and any real model has to beat it.

🧠 **New idea — "n vs p":** we have a few hundred patients (that's *n*) but almost twenty features
(*p*). When you have **few patients but many features**, a model has enough freedom to *memorise*
the exact patients instead of learning a real pattern — like a student who memorises past exam
papers word-for-word but can't answer a new question. Watch for this; it haunts the whole project.

### §4 Preprocessing — and a hidden trap

We pick which columns are **predictors** (the clues the model is allowed to use) and which is the
**outcome** (the thing we're predicting). But one column is a **trap**, and spotting it is one of
the most valuable skills in all of machine learning.

🧠 **New idea — data leakage:** imagine trying to "predict" whether it rained today by looking at
whether the ground is wet *this evening*. You'd be "right" every time — but it's useless, because
you only know the ground is wet *after* the rain already happened. A predictor is only fair if you
would actually have it **at the moment you need to make the prediction.** One feature in this
dataset is measured *years later*, at a follow-up visit. The notebook asks you to find it and
decide whether it belongs. Think hard about *when* each thing is measured.

🧠 **New idea — standardising:** some features are big numbers (age up to 80) and some are just 0
or 1. Many models would wrongly think the big-numbered feature is more important *just because the
numbers are bigger*. **Standardising** rescales every feature to a common footing so they compete
fairly.

### §5 EDA — exploring the data

Now we *look*:

- **Univariate** ("one variable") — a histogram of one feature, with converters and
  non-converters in different colours. Does that one measurement separate the two groups?
- **Bivariate** ("two variables") — two features plotted together. Does a *pair* separate them
  better than either alone?
- **Correlation** — which features rise and fall together (carrying overlapping information).

*Watch what happens compared to iris.* The flowers separated into beautiful clean clouds. Here?
You'll probably see the two patient groups **overlapping** a lot. That's not a mistake on your
part — it's the data honestly telling you this is a **hard** problem. Set your expectations
accordingly.

### §6 Unsupervised learning — PCA

🧠 **New idea — supervised vs unsupervised.** So far we've been colouring our plots by the answer
(converted or not). **Unsupervised** learning *hides the answer* and asks: does the data form
natural groups *by itself*? If it does, and those groups happen to match who converted, that's a
strong signal.

🧠 **New idea — PCA (Principal Component Analysis).** We have ~19 features — far too many to plot
at once. PCA is a clever way to **squeeze many features into a few** while keeping as much of the
"spread" in the data as possible. It builds new combined axes called **principal components**:

- **PC1** captures the single biggest pattern of variation, **PC2** the next biggest, and so on.
- **Explained variance** tells you how much of the data's spread each component keeps. *In iris,
  just 2 components held ~96% — almost everything. How many do you need here to reach 90%?* If you
  need a lot, it means the information is **scattered** across many features, not concentrated.
- The **score plot** draws every patient in the new PC1–PC2 space, coloured by outcome. *Do
  converters and non-converters separate, or sit on top of each other?*
- **Loadings** tell you what each component is "made of" — which original features it mostly
  represents. This is how you give a component a *meaning* (e.g. "PC1 is mostly about MRI lesions").

🧠 **New idea — clustering (and why one size doesn't fit all).** PCA gave us new axes; **clustering**
instead sorts each patient into a **group** by similarity, without ever seeing the answer — then you
check whether those groups happen to match who converted (just like sorting laundry into piles and
*then* seeing if you accidentally separated the lights from the darks). You'll start with **K-Means**,
the most common method. But K-Means assumes clusters are neat round blobs — a bad match for our
yes/no (0/1) data — so the notebook then lets you try **other** algorithms (Gaussian Mixture,
hierarchical, DBSCAN, spectral) and compare them. The big lessons:
- **Match the algorithm to the data.** Different methods assume different cluster shapes; there is no
  universal best one. K-Modes is the right tool for yes/no data; DBSCAN finds the number of groups
  itself; and so on.
- **Two scores, and they can disagree.** *Silhouette* asks "are the clusters tidy?"; *ARI* asks "do
  the clusters match the real outcome?". Watch for a method that looks tidy (high silhouette) but
  whose groups have nothing to do with conversion (low ARI). **A tidy cluster is not a useful one.**

### §7 Classification — first, the *wrong* way

🧠 **Two models you'll meet:**
- **Logistic regression** — a simple, well-behaved classifier that draws a straight dividing line
  and gives a probability. Hard to fool.
- **Random forest** — a "committee" of many decision trees that vote. Powerful and flexible — but
  flexible enough to *memorise* a small dataset.

We start by doing something **deliberately wrong**: we train the model and test it on *the exact
same patients*. The score will look amazing (probably 100%!). *But ask yourself the question the
notebook poses: would you trust a student who wrote their own exam, took it with the answer key
open, and got 100%?* This is to make you feel, in your gut, why the next step exists.

### §8 Validation — the real heart of the project

This is the most important part. We're going to test the model **three ways**, each more honest
than the last.

🧠 **§8a Cross-validation.** Instead of testing on the training data (cheating), we **hide** some
patients, train on the rest, and test on the hidden ones — then repeat so everyone gets a turn
being hidden. This gives an *honest* score. *Compare it to the 100% from before. What happened to
each model?* You may find something surprising about the random forest — pay attention, and ask
yourself what it could mean. (Hint to ponder, not answer for you: could some features be secretly
*restating* the diagnosis?)

🧠 **§8b The right scoreboard.** Accuracy ("what fraction did we get right?") is a **bad
scoreboard** when the classes are imbalanced — remember your "do nothing" baseline. So we use
better measures:
- **Sensitivity (recall):** of the patients who *truly* converted, how many did we catch? (Missing
  a real case is serious.)
- **Specificity:** of those who *didn't* convert, how many did we correctly clear?
- **Balanced accuracy:** the average of those two — it can't be fooled by the common class.
- **ROC-AUC:** how well the model *ranks* patients from low to high risk (0.5 = random guessing,
  1.0 = perfect).
- **Confusion matrix:** a little table showing exactly *what kind* of mistakes you made.

*A real question to sit with: which mistake is worse here — telling someone who WILL convert that
they're fine, or worrying someone who WON'T? Your answer should change which score you care about.*

🧠 **§8c External validation — the true test.** Cross-validation still only ever saw patients from
**one** hospital (in Mexico). The ultimate test is whether your model works on patients from a
**completely different** hospital (in Lithuania) — different country, different equipment,
different patients. The notebook lines up the shared measurements for you; you run the experiment.

*Watch the score change. Almost certainly it will get **worse**. Why would a model that looked good
suddenly stumble on a new hospital's patients?* This is called **domain shift** — and it's the
reason a model can ace every test in the lab and still fail in the real world. The two hospitals
even had different conversion rates to begin with (look at the printout).

### §9 Bringing it together

The synthesis questions are the real prize. Try to answer them in full sentences. The biggest one,
the question the whole field of medical AI revolves around:

> **What would you need to see before you trusted this model to help decide about a real patient?**

---

## Mini-glossary (keep this handy)

**Machine-learning words**
- **Feature** — one measurement/column (e.g. Age).
- **Label / outcome** — the thing you're predicting (here: converted to MS, yes/no).
- **Model** — the thing that learns the pattern from features to label.
- **Training** — showing the model examples so it learns.
- **Overfitting** — when a model memorises the training data instead of learning a general rule;
  it looks great on what it's seen and fails on anything new.
- **Leakage** — accidentally giving the model a clue it wouldn't really have at prediction time;
  makes it look great and be useless.
- **Standardising / scaling** — rescaling features so they're comparable.
- **PCA** — squeezing many features into a few "principal components."
- **Cross-validation** — testing fairly by hiding part of the data, repeatedly.
- **Domain shift** — when new data comes from a different population, so the model does worse.

**Clinical words**
- **CIS (clinically isolated syndrome)** — a person's first neurological episode.
- **MS / CDMS** — multiple sclerosis / clinically definite MS, the disease we're predicting.
- **EDSS** — a 0–10 disability score (0 = no disability).
- **Oligoclonal bands** — abnormal antibodies in spinal fluid; a classic sign of MS.
- **Evoked potentials (VEP, BAEP, SSEP)** — tests of how fast nerve signals travel; delays hint at
  nerve damage.
- **MRI lesions (periventricular, infratentorial, spinal, …)** — spots of damage seen on a brain/
  spine scan, in specific locations doctors look for in MS.

---

## Metrics in plain words

You'll see a few scores pop up. Here's what each one is really asking.

**Ways to measure how "similar" two patients are (used by clustering):**
- **Euclidean distance** — ordinary "as the crow flies" straight-line distance. Great for things
  like age; awkward for yes/no answers.
- **Hamming distance** — *on how many yes/no questions did these two patients answer differently?*
  Count of mismatches (e.g. "they differ on 3 of the 10 questions"). The natural choice for our
  0/1 data.
- **Jaccard distance** — like Hamming, but it only pays attention to the "yes"es and **ignores the
  boring shared "no"s.** Handy when *having* a marker is the interesting part, not lacking one.

**Ways to judge clusters:**
- **Silhouette score** (−1 to 1, higher is better) — *are the clusters tidy?* Like asking whether
  each person is clearly inside one friend group or stuck awkwardly between two. It doesn't need to
  know the "right" answer.
- **ARI — Adjusted Rand Index** (0 = random, 1 = perfect) — *do the clusters match the real
  outcome?* Like sorting laundry blindfolded and then checking whether you actually separated lights
  from darks. We can only compute it because we secretly know who converted. **0 means the clusters
  are no better than a random sort.**

**Ways to judge a classifier (the validation section):**
- **Sensitivity (recall)** — of the patients who **really converted**, how many did the model catch?
  (Missing them is the dangerous mistake.)
- **Specificity** — of the patients who **didn't** convert, how many did it correctly clear? (Low
  specificity = lots of false alarms.)
- **Balanced accuracy** — the average of those two. A fairer score than plain accuracy when one
  group is rarer than the other.
- **ROC-AUC** (0.5 = random guessing, 1.0 = perfect) — how good the model is at giving a *real*
  converter a higher risk score than a non-converter.

A handy habit: whenever you read a score, ask **"compared to what?"** — compared to random (0 for
ARI, 0.5 for AUC), or compared to the do-nothing baseline.

## A few tips for reading your results

- **A number is not an achievement until you understand it.** Always ask "compared to what?" (e.g.
  compared to the do-nothing baseline, or to cross-validation).
- **Too good to be true usually is.** A perfect or near-perfect score should make you *suspicious*,
  not happy. Go hunting for leakage.
- **Write down what surprised you.** Surprise is where the real understanding is hiding.
- **When you ask Gemini, be specific:** name the dataframe (`mex`), the column, and exactly what
  plot or model you want. If it's wrong, tell it what you expected and what you got.

Have fun — and be skeptical of your own results. That skepticism is the most important thing a data
scientist owns.
