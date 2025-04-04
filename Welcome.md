```dataviewjs
const file = dv.current().file.path; // Get the current file's path
app.vault.read(app.vault.getAbstractFileByPath(file)).then(content => {
    const matches = content.match(/(^|\s)=====(\s|$)/g); // Match all occurrences of "====="
    const count = matches ? matches.length : 0; // Count matches or default to 0
    dv.paragraph(`Total "=====" count in the current file: ${count}`);
    const matches1 = content.match(/(^|\s)###(\s|$)/g); // Match all occurrences of "###"
    const count1 = matches1 ? matches1.length : 0; // Count matches or default to 0
    dv.paragraph(`Total "###" count in the current file: ${count1}`);
});
```

```dataviewjs
// Define a normalization function that removes emojis, trims whitespace, and lowercases the text.
function normalizeHeading(text) {
    return text.replace(/[\p{Emoji}]/gu, '').trim().toLowerCase();
}
// Get all pages in the vault
const pages = dv.pages();
let allHeadings = [];
// Iterate through each page
for (let page of pages) {
    // Get the cache object for the current page
    const cache = this.app.metadataCache.getCache(page.file.path);
    if (cache && cache.headings) {
        // Map headings to include file information
        const pageHeadings = cache.headings.map(heading => ({
            file: page.file.name,
            path: page.file.path,
            heading: heading.heading,
            level: heading.level,
            position: heading.position
        }));
        allHeadings = allHeadings.concat(pageHeadings);
    }
}
// Create a map to count heading occurrences using normalized headings
const headingCount = {};
allHeadings.forEach(h => {
    const normalized = normalizeHeading(h.heading);
    headingCount[normalized] = (headingCount[normalized] || 0) + 1;
});
// Filter to keep only duplicate headings based on normalized headings
const duplicateHeadings = allHeadings.filter(h => 
    headingCount[normalizeHeading(h.heading)] > 1
);
// Sort duplicates by normalized heading text and then by file
duplicateHeadings.sort((a, b) => {
    const normA = normalizeHeading(a.heading);
    const normB = normalizeHeading(b.heading);
    if (normA !== normB) {
        return normA.localeCompare(normB);
    }
    return a.path.localeCompare(b.path);
});
// Create a markdown table with the results
dv.header(2, "Duplicate Headings Found");
dv.paragraph(`Total number of duplicate headings: ${Object.keys(headingCount).filter(h => headingCount[h] > 1).length}`);
if (duplicateHeadings.length > 0) {
    dv.table(
        ["Heading", "File", "Level", "Position", "Total Occurrences"],
        duplicateHeadings.map(h => [
            h.heading,
            h.file,
            "H" + h.level,
            `Line ${h.position.start.line + 1}`,
            headingCount[normalizeHeading(h.heading)]
        ])
    );
} else {
    dv.paragraph("No duplicate headings found in the vault.");
}
```
---



---
### EXAMINE
@@
**Verb** | हिंदी: जाँच करना / परीक्षण करना; परीक्षा लेना : To inspect (someone or something) thoroughly in order to determine their nature or condition; To test the knowledge or proficiency of (someone) by requiring them to answer questions or perform tasks.
- ***Synonyms***:
    - **Verb:**
        - *Inspect thoroughly:* Inspect, scrutinize, investigate, study, analyze, survey, check, probe, peruse
        - *Test knowledge:* Test, quiz, assess, question, interrogate, catechize
- ***Antonyms***:
    - **Verb:**
        - *Inspect thoroughly:* Ignore, overlook, disregard, neglect, glance, skim
_Example_:
1. The doctor will **examine** the patient to diagnose the illness. *(Verb: inspect thoroughly)*
2. The professor will **examine** the students on the material covered in the semester. *(Verb: test knowledge)*

_Word Form Examples_
1. **EXAMINATION** / **EXAM**: 🌟
   - He passed the final **examination** with high marks. *(Noun: a formal test of knowledge or proficiency)*
   - A close **examination** of the evidence revealed inconsistencies. *(Noun: a detailed inspection or study)*
   - ***Synonyms***: (test) test, assessment, quiz, appraisal; (inspection) inspection, scrutiny, analysis, investigation, study
2. **EXAMINER**: 🌟
   - The driving **examiner** assessed her ability to parallel park. *(Noun: a person who tests someone's knowledge or proficiency)*
   - ***Synonyms***: assessor, tester, inspector, investigator, questioner, interrogator
3. **EXAMINED**:
   - The artifacts were carefully **examined** by the archaeologists. *(Adjective/Past Participle: having been inspected or tested)*
   - ***Synonyms***: inspected, scrutinized, tested, assessed, investigated, checked
4. **EXAMINING**:
   - The committee is **examining** the proposal in detail. *(Verb Gerund/Present Participle: the act of inspecting or testing)*
   - ***Synonyms***: inspecting, scrutinizing, testing, assessing, investigating, studying

=====
### FROLIC
@@
**Verb** | हिंदी: खेलना-कूदना; मौज-मस्ती करना : To play and move about cheerfully or energetically; To engage in playful activity.
**Noun** | हिंदी: खेल-कूद; मौज-मस्ती : Playful action or movement; A lively or playful activity or event.
- ***Synonyms***:
    - **Verb:**
        - *Play cheerfully:* Romp, caper, cavort, frisk, gambol, play, disport, revel
    - **Noun:**
        - *Playful activity:* Play, romp, fun, gaiety, merrymaking, amusement, caper, antic
- ***Antonyms***:
    - **Verb:**
        - *Play cheerfully:* Mope, brood, sulk, grieve, mourn
    - **Noun:**
        - *Playful activity:* Seriousness, solemnity, gloom, work, drudgery
_Example_:
1.  Lambs **frolic** in the green fields during springtime. *(Verb: play cheerfully)*
2.  The children had a happy **frolic** on the beach. *(Noun: playful activity)*

_Word Form Examples_
1. **FROLICKING**:
   - We spent the afternoon **frolicking** in the pool. *(Verb/Gerund: engaging in playful activity)*
   - ***Synonyms***: playing, romping, capering, cavorting, sporting
2. **FROLICSOME**: 🌟
   - The **frolicsome** puppy chased its tail endlessly. *(Adjective: playful and lively)*
   - ***Synonyms***: playful, frisky, lively, merry, spirited, coltish
3. **FROLICKED**:
   - The happy children **frolicked** in the park all afternoon. *(Verb: past tense of frolic)*
   - ***Synonyms***: romped, capered, played, cavorted, gamboled

=====



### HID
@@
**Verb (Past Tense, Past Participle of HIDE)** | हिंदी: छुपाया / छिपाया; गुप्त रखा : Concealed or put something out of sight; Kept something secret.
- ***Synonyms***:
    - **Verb (action of hiding):**
        - *Conceal/Keep Secret:* Concealed, secreted, covered, screened, masked, veiled, camouflaged, stowed away, tucked away, obscured.
- ***Antonyms***:
    - **Verb (action of hiding):**
        - *Conceal/Keep Secret:* Revealed, exposed, showed, displayed, uncovered, unveiled, exhibited, found, discovered.
_Example_:
1. She **hid** the gift in the closet so he wouldn't see it. *(Verb Past Tense: concealed)*
2. He **hid** his disappointment behind a forced smile. *(Verb Past Tense: kept secret)*
3. The treasure map lay **hid** (or more commonly: hidden) beneath the floorboards for years. *(Verb Past Participle: concealed - note: 'hidden' is the more common past participle/adjective form)*

_Word Form Examples_
1. **HIDE** (Base Form): 🌟
   - Try not to **hide** your mistakes; learn from them. *(Verb: to conceal)*
   - They watched the deer from a **hide** in the woods. *(Noun: a concealed shelter for observing wildlife)*
   - ***Synonyms***: (Verb) conceal, secrete, cover, screen, mask; (Noun) blind, shelter, lookout, screen
2. **HIDING**: 🌟
   - The cat is **hiding** under the sofa again. *(Verb Present Participle: in the act of concealing oneself)*
   - After the robbery, the thieves went into **hiding**. *(Noun: the state of being concealed)*
   - ***Synonyms***: (Gerund) concealing, secreting, covering; (Noun) concealment, refuge, seclusion, shelter, hideout
3. **HIDDEN**: 🌟
   - The key was **hidden** under the doormat. *(Adjective/Past Participle: concealed, not easily found)*
   - There may be **hidden** fees in the contract. *(Adjective: not immediately obvious)*
   - ***Synonyms***: concealed, secret, unseen, covert, latent, obscure, camouflaged, underlying
4. **HIDER**:
   - In the game of hide-and-seek, the **hider** must find a good spot quickly. *(Noun: a person or animal that hides)*
   - ***Synonyms***: concealer
5. **HIDING PLACE**: 🌟
   - The attic became their favorite **hiding place**. *(Noun Phrase: a location used for concealment)*
   - ***Synonyms***: hideout, refuge, sanctuary, retreat, shelter, hideaway, safe house

=====

### IMPRISON
@@
**Verb** | हिंदी: कैद करना / बंदी बनाना; सीमित करना : To put or keep in prison or jail; To confine or restrain someone or something.
- ***Synonyms***:
    - **Verb:**
        - *Put in jail:* Incarcerate, jail, confine, detain, lock up, immure, hold captive
        - *Confine/Restrain:* Confine, restrain, restrict, trap, enclose
- ***Antonyms***:
    - **Verb:**
        - *Put in jail/Confine:* Release, free, liberate, discharge, emancipate, let go
_Example_:
1. The judge sentenced the defendant and ordered him to be **imprisoned** for five years. *(Verb: put in jail)*
2. Fear can **imprison** the mind, preventing personal growth. *(Verb: confine/restrain metaphorically)*

_Word Form Examples_
1. **IMPRISONMENT**: 🌟
   - He received a sentence of life **imprisonment** for his crimes. *(Noun: the state of being confined in prison; the act of confining)*
   - ***Synonyms***: incarceration, confinement, detention, captivity, custody, internment
2. **IMPRISONED**:
   - The **imprisoned** soldiers planned an escape. *(Adjective/Past Participle: confined in prison)*
   - ***Synonyms***: incarcerated, jailed, confined, detained, captive, locked up
3. **IMPRISONING**:
   - The regime was known for **imprisoning** political dissenters. *(Verb Gerund/Present Participle: the act or process of putting someone in prison)*
   - ***Synonyms***: incarcerating, jailing, confining, detaining, locking up

=====

### INTERN
@@
**Noun** | हिंदी: प्रशिक्षु : Someone, especially a student, working temporarily at a job to get experience.
**Verb** | हिंदी: प्रशिक्षु के रूप में काम करना; नज़रबंद करना : To work as an intern; To confine someone as a prisoner, especially for political or military reasons during wartime.
- ***Synonyms***:
    - **Noun:**
        - *Trainee:* Trainee, apprentice, learner, novice, probationer
    - **Verb:**
        - *Work as trainee:* Train, apprentice
        - *Confine:* Confine, imprison, detain, hold, incarcerate, impound
- ***Antonyms***:
    - **Noun:**
        - *Trainee:* Mentor, expert, professional, master
    - **Verb:**
        - *Confine:* Release, liberate, free, discharge
_Example_:
1. The company hires several **interns** each summer to assist with various projects. *(Noun: trainee)*
2. She plans to **intern** at a graphic design studio after finishing her course. *(Verb: work as trainee)*
3. During World War II, many foreign nationals were **interned** by the government. *(Verb: confine)*

_Word Form Examples_
1. **INTERNSHIP**: 🌟
   - He applied for a summer **internship** at the tech company. *(Noun: a period of working as an intern)*
   - ***Synonyms***: traineeship, apprenticeship, placement, work experience
2. **INTERNEE**:
   - The **internees** were kept in camps for the duration of the conflict. *(Noun: a person confined as a prisoner)*
   - ***Synonyms***: prisoner, detainee, captive, inmate, political prisoner
3. **INTERNMENT**: 🌟
   - The policy of **internment** faced significant legal challenges. *(Noun: the state of being confined as a prisoner)*
   - ***Synonyms***: confinement, imprisonment, detention, captivity, incarceration
4. **INTERNING**:
   - While **interning**, she learned valuable skills relevant to her field. *(Verb Gerund/Present Participle: the act of working as an intern)*
   - ***Synonyms***: training, apprenticing, learning
5. **INTERNED**:
   - He **interned** at the hospital before starting his residency. *(Verb Past Tense: worked as an intern)*
   - Thousands were **interned** without trial during the emergency. *(Verb Past Tense/Past Participle: confined as a prisoner)*
   - ***Synonyms***: (worked as) trained, apprenticed; (confined) confined, imprisoned, detained, incarcerated

=====

### NOTICE
@@
**Noun** | हिंदी: ध्यान / सूचना; सूचना / चेतावनी / विज्ञप्ति; इत्तला : Attention or awareness; A formal warning or announcement (often written); Advance notification of departure (from job/residence).
**Verb** | हिंदी: ध्यान देना / देखना / गौर करना : To become aware of, perceive, or observe.
- ***Synonyms***:
    - **Noun:**
        - *Attention/Awareness:* Attention, observation, awareness, perception, heed, regard
        - *Formal Warning/Announcement:* Announcement, notification, warning, communication, intimation, bulletin, sign
        - *Advance Notification:* Resignation, warning, notification (period)
    - **Verb:**
        - *Become Aware/Observe:* Observe, perceive, note, see, spot, detect, discern, remark, mind
- ***Antonyms***:
    - **Noun:**
        - *Attention/Awareness:* Inattention, disregard, oversight, ignorance, neglect
        - *Formal Warning/Announcement:* Secret, concealment, suppression
    - **Verb:**
        - *Become Aware/Observe:* Overlook, ignore, miss, disregard, neglect
_Example_:
1. His sudden departure came to everyone's **notice**. *(Noun: attention/awareness)*
2. A **notice** regarding the new policy was pinned to the board. *(Noun: formal warning/announcement)*
3. You are required to give one month's **notice** if you wish to terminate the contract. *(Noun: advance notification)*
4. Did you **notice** the change in her hair color? *(Verb: become aware/observe)*
5. He failed to **notice** the warning signs. *(Verb: become aware/observe)*

_Word Form Examples_
1. **NOTICEABLE**: 🌟
   - There was a **noticeable** improvement in his performance after the training. *(Adjective: easily seen or recognized)*
   - ***Synonyms***: perceptible, detectable, observable, visible, apparent, distinct, evident
2. **NOTICEABLY**:
   - The temperature dropped **noticeably** overnight. *(Adverb: in a way that is easily seen or noticed)*
   - ***Synonyms***: perceptibly, visibly, detectably, markedly, significantly, clearly
3. **UNNOTICED**:
   - The small error went **unnoticed** for weeks. *(Adjective: not observed or perceived)*
   - ***Synonyms***: overlooked, ignored, missed, unperceived, unseen, disregarded
4. **NOTICING**:
   - **Noticing** the time, she realized she was late. *(Verb Present Participle: the action of observing or becoming aware)*
   - ***Synonyms***: observing, perceiving, spotting, detecting, seeing, discerning
5. **NOTICED**:
   - The manager **noticed** his potential early on. *(Verb Past Tense: became aware of)*
   - The much-**noticed** event attracted media attention. *(Adjective/Past Participle: having attracted attention)*
   - ***Synonyms***: (verb) observed, perceived, saw, spotted; (adj) observed, perceived, recognized

=====

### OBSERVE
@@
**Verb** | हिंदी: देखना / ध्यान देना; पालन करना; टिप्पणी करना : To notice or perceive (something) and register it as being significant; To fulfill or comply with (a law, rule, or custom); To make a remark or comment.
- ***Synonyms***:
    - **Verb:**
        - *Notice/Perceive:* Watch, view, note, perceive, detect, monitor, scrutinize, witness
        - *Comply with:* Follow, keep, obey, adhere to, honor, respect, uphold, comply with
        - *Remark:* Comment, remark, state, mention, note, declare, say
- ***Antonyms***:
    - **Verb:**
        - *Notice/Perceive:* Ignore, overlook, miss, disregard, neglect
        - *Comply with:* Break, violate, disobey, disregard, flout, ignore
        - *Remark:* Be silent, keep quiet, refrain
_Example_:
1. Scientists **observe** the planet's surface using powerful telescopes. *(Verb: notice/perceive)*
2. It is important to **observe** the rules of the road for everyone's safety. *(Verb: comply with)*
3. "The weather seems to be improving," he **observed**. *(Verb: remark)*

_Word Form Examples_
1. **OBSERVATION**: 🌟
   - Careful **observation** is key to understanding animal behavior. *(Noun: the action or process of observing something carefully)*
   - He shared his insightful **observations** during the meeting. *(Noun: a remark, statement, or comment based on something one has seen, heard, or noticed)*
   - ***Synonyms***: (watching) Scrutiny, monitoring, surveillance, examination, inspection; (remark) Comment, remark, statement, finding, reflection, note
2. **OBSERVANT**: 🌟
   - The **observant** child noticed the tiny flower growing between the cracks. *(Adjective: quick to notice things)*
   - ***Synonyms***: Attentive, perceptive, alert, watchful, sharp-eyed, eagle-eyed, vigilant
3. **OBSERVER**: 🌟
   - She attended the conference as an independent **observer**. *(Noun: a person who watches or notices something)*
   - ***Synonyms***: Watcher, onlooker, spectator, witness, viewer, monitor, commentator
4. **OBSERVANCE**: 🌟
   - Strict **observance** of the safety procedures is mandatory. *(Noun: the action or practice of fulfilling or respecting a law, custom, or rule)*
   - ***Synonyms***: Compliance, adherence, keeping, honoring, fulfillment, respect, following
5. **OBSERVABLE**:
   - The effects of the treatment were clearly **observable** within a week. *(Adjective: able to be noticed or perceived; discernible)*
   - ***Synonyms***: Noticeable, visible, detectable, perceptible, discernible, apparent, evident
6. **OBSERVED**:
   - The **observed** data differed slightly from the expected results. *(Adjective/Past Participle: noticed or perceived through observation)*
   - ***Synonyms***: Noticed, detected, seen, noted, perceived, witnessed
7. **OBSERVATORY**:
   - They visited the astronomical **observatory** to look through the large telescope. *(Noun: a building designed for astronomical or meteorological observation)*
   - ***Synonyms***: Lookout, watchtower, viewing station

=====
### RULE
@@
**Noun** | हिंदी: नियम / सिद्धांत; शासन : An authoritative regulation or principle governing behaviour or procedure; The exercise of political control or authority over an area and its people.
**Verb** | हिंदी: शासन करना; निर्णय देना; रेखा खींचना : To exercise ultimate power or authority over (an area and its people); To pronounce authoritatively and legally to be the case; To make a straight line on paper using a ruler.
- ***Synonyms***:
    - **Noun:**
        - *Regulation/Principle:* Regulation, law, directive, guideline, principle, standard, ordinance, statute, canon
        - *Governance/Control:* Reign, sovereignty, dominion, control, command, authority, jurisdiction, regime
    - **Verb:**
        - *Govern:* Govern, reign, preside over, command, lead, dominate, control, manage
        - *Decide Officially:* Decree, judge, decide, determine, adjudicate, find, pronounce
        - *Draw Line:* Draw, mark
- ***Antonyms***:
    - **Noun:**
        - *Regulation/Principle:* Exception, deviation, irregularity, anomaly
        - *Governance/Control:* Anarchy, chaos, submission, freedom, servitude
    - **Verb:**
        - *Govern:* Obey, submit, follow, serve, comply
        - *Decide Officially:* Waive, reconsider, defer, equivocate
_Example_:
1. Breaking the **rules** can lead to penalties. *(Noun: regulation)*
2. The country prospered under her **rule**. *(Noun: governance)*
3. The monarch **rules** justly and wisely. *(Verb: govern)*
4. The court **ruled** in favour of the plaintiff. *(Verb: decide officially)*
5. Please **rule** two lines beneath the title. *(Verb: draw line)*

_Word Form Examples_
1. **RULER**: 🌟
   - The **ruler** of the ancient kingdom was overthrown. *(Noun: a person exercising government or dominion)*
   - Use a **ruler** to ensure the lines are straight. *(Noun: a straight strip of plastic, wood, metal, etc., used for drawing straight lines or measuring distances)*
   - ***Synonyms***: (governor) sovereign, monarch, leader, head of state, chief; (measuring tool) straightedge, measure, yardstick
2. **RULING**: 🌟
   - The judge's **ruling** set a new precedent. *(Noun: an authoritative decision or pronouncement)*
   - The **ruling** party faced criticism over its economic policies. *(Adjective: currently exercising authority or control)*
   - ***Synonyms***: (noun) decision, judgement, decree, verdict, finding; (adj) governing, reigning, dominant, controlling, incumbent
3. **RULED**:
   - The page was neatly **ruled** with blue lines. *(Adjective/Past Participle: marked with straight parallel lines)*
   - He **ruled** the company for over twenty years. *(Verb Past Tense: governed or decided)*
   - ***Synonyms***: (adj) lined; (verb) governed, presided, judged, decreed
4. **RULES**: 🌟
   - Understanding the basic **rules** is essential before playing. *(Noun Plural: regulations)*
   - He **rules** with fairness. *(Verb 3rd Person Singular: governs)*
   - ***Synonyms***: (noun) regulations, laws, guidelines, principles, statutes, ordinances
5. **UNRULY**: 🌟
   - The teacher struggled to control the **unruly** class. *(Adjective: disorderly and disruptive; not amenable to discipline or control)*
   - ***Synonyms***: disorderly, uncontrollable, disobedient, disruptive, rowdy, wild, chaotic
6. **OVERRULE**:
   - The Supreme Court can **overrule** decisions made by lower courts. *(Verb: to reject or disallow by exercising superior authority)*
   - ***Synonyms***: override, reverse, countermand, cancel, veto, quash, rescind

=====
