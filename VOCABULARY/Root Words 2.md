#root2

```dataviewjs
const file = dv.current().file.path;
app.vault.read(app.vault.getAbstractFileByPath(file)).then(content => {
    const lines = content.split('\n');
    let headerCount = 0, separatorCount = 0;
    let pendingWord = null, lastCorrectWord = null;
    const issues = [];
    
    const addIssue = (word, problem) => issues.push({ word, problem, lastCorrect: lastCorrectWord });
    
    lines.forEach(line => {
        const trimmed = line.trim();
        
        if (trimmed.startsWith('### ')) {
            // Close pending word if exists
            if (pendingWord) addIssue(pendingWord, 'Missing separator');
            
            headerCount++;
            pendingWord = trimmed.slice(4).split(/\s/)[0].replace(/[🪐@@]/g, '');
        }
        else if (/^=+$/.test(trimmed)) {
            if (trimmed === '=====') {
                separatorCount++;
                if (pendingWord) {
                    lastCorrectWord = pendingWord;
                    pendingWord = null;
                } else {
                    addIssue('UNKNOWN', 'Separator without header');
                }
            } else if (pendingWord) {
                addIssue(pendingWord, `Wrong separator: ${trimmed} (${trimmed.length} equals)`);
                pendingWord = null;
            }
        }
    });
    
    // Handle final pending word
    if (pendingWord) addIssue(pendingWord, 'Missing separator (EOF)');
    
    // Results
    dv.paragraph(`📊 Headers: ${headerCount} | Separators: ${separatorCount}`);
    
    if (headerCount === separatorCount && !issues.length) {
        dv.paragraph(`✅ **Perfect formatting!** (${headerCount} words)`);
    } else {
        dv.paragraph(`❌ **${issues.length} issue(s) found:**`);
        issues.forEach(({ word, problem, lastCorrect }) => {
            const ref = lastCorrect ? ` *(after ${lastCorrect})*` : '';
            dv.paragraph(`• **${word}**: ${problem}${ref}`);
        });
    }
});
```
## **31 MOM/ MOB/ MOT/ MOV** = move

### COMMOTION
@@
**Noun** | हिंदी: कोलाहल; हंगामा : A state of confused or noisy disturbance.
- ***Synonyms***: Uproar, tumult, turmoil, disturbance, disorder, agitation
_Example_: The sudden **commotion** outside the classroom disrupted the exam. *(Noun: noisy disturbance)*

=====

### DEMOTE
@@
**Verb** | हिंदी: पदावनत करना : To reduce someone to a lower position or rank.
- ***Synonyms***: Downgrade, relegate, lower, reduce, downrank
_Example_: The company decided to **demote** him after his repeated policy violations. *(Verb: reduce in rank)*

=====

### EMOTION
@@
**Noun** | हिंदी: भावना; जज़्बात : A strong feeling deriving from one's circumstances, mood, or relationships with others.
- ***Synonyms***: Feeling, sentiment, reaction, passion, affection, sensation
_Example_: His voice cracked with **emotion** as he delivered the acceptance speech. *(Noun: strong feeling)*

=====

### MOBILE
@@
**Adjective** | हिंदी: चल; गतिशील : Able to move or be moved freely or easily.
**Noun** | हिंदी: मोबाइल : A portable telephone device.
- ***Synonyms***:
    - **Adjective:**
        - *Movable:* Portable, transportable, movable, unfixed
    - **Noun:**
        - *Phone:* Cell phone, smartphone, wireless phone
_Example_:
1. The artist created a **mobile** sculpture that rotated with the breeze. *(Adjective: movable)*
2. She couldn't find her **mobile** anywhere in the house. *(Noun: cell phone)*

=====

### MOMENTOUS
@@
**Adjective** | हिंदी: महत्वपूर्ण : Of great importance, significance, or consequence.
- ***Synonyms***: Important, significant, major, crucial, consequential, historic
_Example_: The signing of the peace treaty was a **momentous** occasion in the country's history. *(Adjective: highly significant)*

=====

### MOTION
@@
**Noun** | हिंदी: गति; प्रस्ताव : The act or process of moving; a formal proposal in a meeting.
**Verb** | हिंदी: इशारा करना : To signal or direct with a movement.
- ***Synonyms***:
    - **Noun:**
        - *Movement:* Movement, action, activity
        - *Proposal:* Proposal, resolution, measure
    - **Verb:**
        - *Gesture:* Signal, gesture, indicate
_Example_:
1. The **motion** of the waves was hypnotic. *(Noun: movement)*
2. She **motioned** for me to follow her down the hallway. *(Verb: gestured)*
3. The board voted to approve the **motion** to increase the budget. *(Noun: formal proposal)*

=====

### MOTIVE
@@
**Noun** | हिंदी: प्रेरणा; उद्देश्य : A reason for doing something; an emotion, desire, or need that causes a person to act.
**Adjective** | हिंदी: प्रेरक : Causing or capable of causing motion. *(Rare)*
- ***Synonyms***:
    - **Noun:**
        - *Reason:* Reason, cause, purpose, incentive, intention, drive
    - **Adjective:**
        - *Causing movement:* Motivating, driving, impelling
_Example_:
1. The police were unable to establish a clear **motive** for the crime. *(Noun: reason)*
2. Profit was the primary **motive** force behind the company's decision. *(Adjective: motivating)* *(Rare)*

=====

### MOVE
@@
**Verb** | हिंदी: हिलना; स्थानांतरित करना : To change position or place; to change residence.
**Noun** | हिंदी: चाल; कदम : An act of moving; a strategic action in a game or activity.
- ***Synonyms***:
    - **Verb:**
        - *Change position:* Shift, relocate, proceed, advance
        - *Affect emotionally:* Touch, affect, stir, influence
    - **Noun:**
        - *Action:* Step, action, maneuver, tactic
_Example_:
1. We plan to **move** to a new apartment next month. *(Verb: change residence)*
2. His next **move** in the chess game was unexpected. *(Noun: strategic action)*
3. The film was so powerful it **moved** many viewers to tears. *(Verb: affected emotionally)*

=====

### PROMINENT
@@
**Adjective** | हिंदी: प्रमुख; उभरा हुआ : Standing out or projecting beyond other parts; widely and popularly known.
- ***Synonyms***: Notable, distinguished, eminent, conspicuous, leading, outstanding
_Example_: She became a **prominent** figure in local politics after her successful campaign to save the park. *(Adjective: notable or distinguished)*

=====

### REMOVE
@@
**Verb** | हिंदी: हटाना; निकालना : To move from a place or position; to eliminate or get rid of.
- ***Synonyms***: Eliminate, take away, extract, delete, detach
_Example_: Please **remove** your shoes before entering the temple. *(Verb: take off)*

=====
## **32 MUT** = change

### COMMUTE
@@
**Verb** | हिंदी: आना-जाना; परिवर्तित करना : To travel regularly between home and work; To reduce or change a punishment or penalty.
**Noun** | हिंदी: नित्य यात्रा : A regular journey between home and work.
- ***Synonyms***:
    - **Verb:**
        - *Travel regularly:* Travel, journey, shuttle
        - *Reduce penalty:* Reduce, lessen, exchange, substitute
    - **Noun:**
        - *Regular journey:* Journey, trip, travel, ride
_Example_:
1. She **commutes** two hours each day to reach her office. *(Verb: travel regularly)*
2. The governor decided to **commute** his sentence from life imprisonment to 20 years. *(Verb: reduce penalty)*
3. His daily **commute** takes 45 minutes by train. *(Noun: regular journey)*

=====

### IMMUTABLE
@@
**Adjective** | हिंदी: अपरिवर्तनीय : Unable to be changed or altered.
- ***Synonyms***: Unchangeable, unalterable, fixed, permanent, constant, invariable
_Example_: The laws of physics are considered **immutable** principles of nature. *(Adjective: unchangeable)*

=====

### MUTATE
@@
**Verb** | हिंदी: उत्परिवर्तित होना : To undergo a change in form, nature, or structure, especially through genetic mutation.
- ***Synonyms***: Change, transform, alter, modify, evolve, transmute
_Example_: The virus can **mutate** rapidly, making it difficult to develop effective vaccines. *(Verb: undergo genetic change)*

=====
## **33 MIS** = bad, hate, wrong

### MISANTHROPE
@@
**Noun** | हिंदी: मानवद्वेषी : A person who dislikes humankind and avoids human society.
- ***Synonyms***: Hater of mankind, cynic, recluse, hermit, asocial person, loner
_Example_: The old **misanthrope** rarely left his cabin and avoided all social gatherings in the village. *(Noun: person who dislikes humanity)*

=====

### MISAPPREHENSION
@@
**Noun** | हिंदी: गलतफहमी : A mistaken belief or understanding; a failure to comprehend correctly.
- ***Synonyms***: Misconception, misunderstanding, mistake, error, misinterpretation, false impression
_Example_: He operated under the **misapprehension** that the event was casual, so he was embarrassed to arrive in jeans when everyone else wore formal attire. *(Noun: mistaken belief)*

=====

### MISCHIEF
@@
**Noun** | हिंदी: शरारत; उपद्रव : Playful misbehavior or troublemaking; harm or trouble caused by someone.
- ***Synonyms***: Trouble, prank, naughtiness, roguishness, impishness, misbehavior
_Example_: The gleam of **mischief** in the child's eyes warned the teacher that some prank was about to unfold. *(Noun: playful troublemaking)*

=====

### MISCONSTRUE
@@
**Verb** | हिंदी: गलत समझना; गलत अर्थ लगाना : To interpret wrongly; to misunderstand the meaning or intention of something.
- ***Synonyms***: Misinterpret, misunderstand, mistake, misread, misjudge, get wrong
_Example_: Please don't **misconstrue** my comments as criticism - I'm simply offering suggestions for improvement. *(Verb: interpret incorrectly)*

=====

### MISFORTUNE
@@
**Noun** | हिंदी: दुर्भाग्य : Bad luck or an unfortunate event or circumstance.
- ***Synonyms***: Adversity, calamity, catastrophe, tragedy, ill luck, hardship
_Example_: His **misfortune** began when he lost his job and continued with a series of health problems. *(Noun: bad luck or unfortunate circumstance)*

=====

### MISHAP
@@
**Noun** | हिंदी: दुर्घटना; छोटी दुर्घटना : A minor accident or unfortunate occurrence.
- ***Synonyms***: Accident, misadventure, setback, problem, trouble, incident
_Example_: The wedding ceremony proceeded without any **mishap** despite earlier concerns about the weather. *(Noun: minor accident or problem)*

=====

### MISINTERPRET
@@
**Verb** | हिंदी: गलत व्याख्या करना : To understand or explain something incorrectly.
- ***Synonyms***: Misconstrue, misunderstand, mistake, misjudge, get wrong, misread
_Example_: She completely **misinterpreted** his silence as anger when he was actually deep in thought. *(Verb: understand incorrectly)*

=====

### MISLEAD
@@
**Verb** | हिंदी: भ्रमित करना; गुमराह करना : To guide someone in the wrong direction or give false information.
- ***Synonyms***: Deceive, misinform, delude, fool, trick, misdirect
_Example_: The advertisement was designed to **mislead** consumers about the actual ingredients in the product. *(Verb: deceive or give false information)*

=====

### MISOGYNY
@@
**Noun** | हिंदी: स्त्री-द्वेष; नारीद्वेष : Hatred, dislike, or prejudice against women.
- ***Synonyms***: Sexism, chauvinism, antifeminism, woman-hating, gender bias
_Example_: His **misogyny** was evident in the way he consistently undermined and belittled his female colleagues. *(Noun: hatred of women)*

=====

### MISPLACE
@@
**Verb** | हिंदी: गलत जगह रखना : To put something in the wrong place and be unable to find it.
- ***Synonyms***: Lose, displace, mislay, forget location of, be unable to find
_Example_: I've **misplaced** my reading glasses again; I had them just a moment ago. *(Verb: put in wrong place and lose)*

=====

### MISTAKE
@@
**Noun** | हिंदी: गलती; भूल : An error or wrong action or judgment.
**Verb** | हिंदी: गलत समझना; भ्रम होना : To identify or interpret wrongly or incorrectly.
- ***Synonyms***:
    - **Noun:**
        - *Error:* Error, blunder, slip, fault, inaccuracy
    - **Verb:**
        - *Misidentify:* Misidentify, confuse, mix up, misinterpret
_Example_:
1. Everyone makes **mistakes**; it's how we learn and grow. *(Noun: error)*
2. I **mistook** him for his brother since they look so similar. *(Verb: identified incorrectly)*

=====

### MISUNDERSTAND
@@
**Verb** | हिंदी: गलत समझना : To interpret or understand something incorrectly.
- ***Synonyms***: Misconstrue, misinterpret, misapprehend, get wrong, misjudge
_Example_: She completely **misunderstood** my intentions when I offered to help with the project. *(Verb: interpret incorrectly)*

=====

### MISUSE
@@
**Verb** | हिंदी: दुरुपयोग करना : To use something in an incorrect or improper way.
**Noun** | हिंदी: दुरुपयोग : The incorrect or improper use of something.
- ***Synonyms***:
    - **Verb:**
        - *Use improperly:* Abuse, exploit, misapply, misemploy
    - **Noun:**
        - *Improper use:* Abuse, improper use, misapplication
_Example_:
1. It's dangerous to **misuse** prescription medications. *(Verb: use improperly)*
2. The **misuse** of company funds led to the executive's dismissal. *(Noun: improper use)*

=====
## **34 NOC/ NIC/ NEC/ NOX** = hurt, damage, harm, dark night

### EQUINOX
@@
**Noun** | हिंदी: विषुव : Either of the two times in the year when the sun crosses the celestial equator and day and night are of approximately equal length.
- ***Synonyms***: Equilux, day-night equality
_Example_: The spring **equinox** marks the beginning of autumn in the Southern Hemisphere and spring in the Northern Hemisphere. *(Noun: time of equal day and night)*

=====

### INNOCENT
@@
**Adjective** | हिंदी: निर्दोष; मासूम : Not guilty of a crime or offense; free from moral wrong; naive or showing childlike simplicity.
**Noun** | हिंदी: निर्दोष व्यक्ति : A person who is innocent, especially a young child.
- ***Synonyms***:
    - **Adjective:**
        - *Not guilty:* Blameless, guiltless, not responsible
        - *Pure/naive:* Naive, pure, unsophisticated, virtuous, guileless
    - **Noun:**
        - *Innocent person:* Blameless person, victim
_Example_:
1. The jury found him **innocent** of all charges after reviewing the evidence. *(Adjective: not guilty)*
2. Her **innocent** remarks unintentionally offended several people at the meeting. *(Adjective: naive)*
3. The war claimed the lives of many **innocents** who had no part in the conflict. *(Noun: blameless people)*

=====

### INNOCUOUS
@@
**Adjective** | हिंदी: अहानिकारक; निरापद : Not harmful or offensive; harmless.
- ***Synonyms***: Harmless, inoffensive, benign, safe, unobjectionable, innocent
_Example_: What seemed like an **innocuous** comment about her appearance unexpectedly upset her. *(Adjective: harmless)*

=====

### INTERNECINE
@@
**Adjective** | हिंदी: आपसी विनाशकारी : Destructive to both sides in a conflict; relating to conflict within a group.
- ***Synonyms***: Mutually destructive, fratricidal, civil, internal, destructive
_Example_: The political party was weakened by **internecine** struggles between its moderate and radical factions. *(Adjective: internal conflict)* *(Rare)*

=====

### NOCTURNAL
@@
**Adjective** | हिंदी: रात्रिचर : Active at night rather than during the day.
- ***Synonyms***: Night-active, nightly, nighttime, evening, night-loving
_Example_: Bats are **nocturnal** creatures that use echolocation to hunt for insects in the dark. *(Adjective: active at night)*

=====

### NOXIOUS
@@
**Adjective** | हिंदी: हानिकारक; विषैला : Harmful, poisonous, or very unpleasant.
- ***Synonyms***: Harmful, toxic, poisonous, harmful, dangerous, injurious
_Example_: The chemical plant released **noxious** gases that caused respiratory problems in nearby residents. *(Adjective: harmful or toxic)*

=====

### OBNOXIOUS
@@
**Adjective** | हिंदी: अप्रिय; कष्टदायक : Extremely unpleasant, offensive, or annoying.
- ***Synonyms***: Offensive, objectionable, unpleasant, annoying, disagreeable, insufferable
_Example_: His **obnoxious** behavior at the party included loud singing and interrupting conversations. *(Adjective: extremely annoying)*

=====

### PERNICIOUS
@@
**Adjective** | हिंदी: विनाशकारी; अत्यंत हानिकारक : Having a harmful effect, especially in a gradual or subtle way.
- ***Synonyms***: Destructive, harmful, damaging, deadly, malignant, insidious
_Example_: The **pernicious** influence of these stereotypes has shaped society's attitudes for generations. *(Adjective: subtly harmful)*

=====
## **35 NAT/NAS** =birth

### COGNATE
@@
**Adjective** | हिंदी: संबंधित; समजात : Related by birth or origin; having the same linguistic derivation.
- ***Synonyms***: Related, kindred, allied, akin, connected
_Example_:  "Philosophy" and "philanthropy" are **cognate** words as they both derive from Greek roots. *(Adjective: related by origin)*

=====

### INNATE
@@
**Adjective** | हिंदी: जन्मजात; सहज : Existing in someone from birth; inborn or natural.
- ***Synonyms***: Inborn, inherent, natural, congenital, hereditary, inbred
_Example_: Her **innate** musical ability was evident from an early age when she could play melodies by ear. *(Adjective: inborn quality)*

=====

### NASCENT
@@
**Adjective** | हिंदी: नवजात; उदीयमान : Just coming into existence and beginning to display signs of future potential.
- ***Synonyms***: Emerging, developing, budding, dawning, growing, evolving
_Example_: The company invested heavily in **nascent** technologies that could revolutionize the industry. *(Adjective: newly emerging)*

=====

### NATIVE
@@
**Adjective** | हिंदी: देशज; स्थानीय; मूल : Born in or originating from a particular place; belonging to a person by birth.
**Noun** | हिंदी: मूलनिवासी; देशवासी : A person born in a specified place or associated with a place by birth.
- ***Synonyms***:
    - **Adjective:**
        - *Indigenous:* Indigenous, local, original, innate
        - *Natural:* Natural, inherent, intrinsic
    - **Noun:**
        - *Indigenous person:* Local, inhabitant, citizen, indigene
_Example_:
1. She is a **native** Spanish speaker though she has lived in Canada for decades. *(Adjective: born with)*
2. The **natives** welcomed tourists to the island with a traditional dance ceremony. *(Noun: indigenous people)*

=====

### NEONATE
@@
**Noun** | हिंदी: नवजात शिशु : A newborn child, especially one less than four weeks old.
- ***Synonyms***: Newborn, infant, baby, newborn infant
_Example_: The hospital has a specialized unit dedicated to caring for **neonates** with critical health conditions. *(Noun: newborn baby)*

=====

### RENAISSANCE
@@
**Noun** | हिंदी: पुनर्जागरण; नवजागरण : A revival or renewed interest in something; the cultural rebirth that occurred in Europe from the 14th through the 17th centuries.
- ***Synonyms***: Revival, renewal, rebirth, resurgence, reawakening
_Example_: The city experienced a cultural **renaissance** with new art galleries, theaters, and music venues opening throughout the downtown area. *(Noun: revival or rebirth)*

=====
## **36 NOM/ NYM** = name

### COGNOMEN
@@
**Noun** | हिंदी: उपनाम : A name added to a person's given name, especially a family name or a nickname; the third name of a citizen of ancient Rome.
- ***Synonyms***: Surname, nickname, epithet, byname, appellation, title
_Example_: "Cicero" was the **cognomen** that distinguished the famous Roman orator Marcus Tullius Cicero from other members of his family. *(Noun: additional name)* *(Rare)*

=====

### IGNOMINIOUS
@@
**Adjective** | हिंदी: अपमानजनक; लज्जाजनक : Deserving or causing public disgrace or shame; humiliating.
- ***Synonyms***: Shameful, disgraceful, dishonorable, humiliating, embarrassing, degrading
_Example_: His career ended in **ignominious** defeat after the scandal was revealed to the public. *(Adjective: shameful or disgraceful)*

=====

### INNOMINATE
@@
**Adjective** | हिंदी: अनामित; बेनाम : Having no name; unnamed or anonymous.
- ***Synonyms***: Unnamed, nameless, anonymous, untitled, undesignated *(Rare)*
_Example_: The **innominate** bone in the pelvis is formed by the fusion of three separate bones during development. *(Adjective: unnamed)* *(Rare)*

=====

### MISNOMER
@@
**Noun** | हिंदी: गलत नाम : A wrong or inaccurate name or designation.
- ***Synonyms***: Incorrect name, wrong label, inaccurate term, false designation
_Example_: Calling the koala bear a "bear" is a **misnomer** since it is actually a marsupial, not a bear. *(Noun: incorrect name)*

=====

### NOMENCLATURE
@@
**Noun** | हिंदी: नामपद्धति; शब्दावली : A system of names or terms used in a particular field or subject.
- ***Synonyms***: Terminology, naming system, classification, taxonomy, naming convention
_Example_: Scientists follow a standardized **nomenclature** when classifying and naming new species. *(Noun: naming system)*

=====

### NOMINATE
@@
**Verb** | हिंदी: नामांकित करना; नामित करना : To propose or formally enter as a candidate for election or for an honor or award.
- ***Synonyms***: Propose, put forward, suggest, name, recommend, appoint
_Example_: The academy will **nominate** five films in each category for the prestigious awards. *(Verb: formally select as candidate)*

=====
## **37 Out** = to exceed

### OUTGROW
@@
**Verb** | हिंदी: बड़ा हो जाना; पार कर जाना : To grow too large for something; to develop beyond or leave behind a phase, condition, or need.
- ***Synonyms***: Surpass, exceed, transcend, develop beyond, leave behind
_Example_: Children quickly **outgrow** their clothes during growth spurts. *(Verb: become too big for)*

=====

### OUTLAST
@@
**Verb** | हिंदी: से अधिक समय तक चलना : To last longer than something else; to survive or endure beyond.
- ***Synonyms***: Survive, endure, persist, outwear, outlive, exceed in duration
_Example_: The high-quality batteries were designed to **outlast** standard ones by at least three years. *(Verb: last longer than)*

=====

### OUTMANEUVER
@@
**Verb** | हिंदी: चतुराई से हरा देना : To surpass in tactical skill, cleverness, or cunning; to defeat by superior strategy.
- ***Synonyms***: Outsmart, outfox, outwit, outflank, outstrategy
_Example_: The smaller company **outmaneuvered** its larger competitor by quickly securing exclusive rights to the new technology. *(Verb: defeat through superior strategy)*

=====

### OUTNUMBER
@@
**Verb** | हिंदी: संख्या में अधिक होना : To exceed in number; to be more numerous than.
- ***Synonyms***: Surpass in number, exceed numerically, be more numerous than
_Example_: At the conference, women **outnumbered** men by almost two to one. *(Verb: exceed in number)*

=====

### OUTPERFORM
@@
**Verb** | हिंदी: से बेहतर प्रदर्शन करना : To perform better than someone or something else; to surpass in performance.
- ***Synonyms***: Surpass, exceed, outdo, outshine, outclass
_Example_: The new model consistently **outperforms** previous versions in both speed and efficiency. *(Verb: perform better than)*

=====

### OUTPLAY
@@
**Verb** | हिंदी: बेहतर खेलना : To play better than an opponent; to defeat in a game by superior play.
- ***Synonyms***: Outclass, outmatch, beat, defeat, surpass in playing
_Example_: Despite being the underdog, our team managed to **outplay** the defending champions and win the tournament. *(Verb: play better than)*

=====

### OUTRUN
@@
**Verb** | हिंदी: दौड़ में पीछे छोड़ देना : To run faster or farther than someone or something; to escape by running.
- ***Synonyms***: Outdistance, outpace, overtake, leave behind, escape
_Example_: The gazelle can easily **outrun** most predators on the African savanna. *(Verb: run faster than)*

=====

### OUTSHINE
@@
**Verb** | हिंदी: अधिक चमकना; से अधिक प्रतिभाशाली होना : To shine more brightly than; to excel or surpass in qualities or accomplishments.
- ***Synonyms***: Overshadow, surpass, eclipse, excel, outdo, outclass
_Example_: Her brilliant performance in the final act **outshone** all the other contestants in the talent show. *(Verb: excel beyond others)*

=====

### OUTSMART
@@
**Verb** | हिंदी: चालाकी से हरा देना : To defeat or outwit by being more clever or intelligent.
- ***Synonyms***: Outwit, outfox, outthink, trick, deceive cleverly
_Example_: The detective managed to **outsmart** the criminal by anticipating his next move. *(Verb: defeat through superior intelligence)*

=====

### OUTWEIGH
@@
**Verb** | हिंदी: से अधिक महत्वपूर्ण होना : To exceed in weight, value, or importance.
- ***Synonyms***: Exceed, surpass, predominate over, overshadow, be more significant than
_Example_: The benefits of the new policy **outweigh** the initial costs of implementation. *(Verb: exceed in importance)*

=====
## **38 PAC/ PEAC/ PLAC** = calm, silent

### APPEASE
@@
**Verb** | हिंदी: शांत करना; तुष्ट करना : To pacify or satisfy by giving in to demands; to relieve or calm.
- ***Synonyms***: Placate, mollify, pacify, soothe, assuage, conciliate
_Example_: The government tried to **appease** the protesters by promising to review the controversial legislation. *(Verb: pacify by concession)*

=====

### COMPLACENT
@@
**Adjective** | हिंदी: आत्मसंतुष्ट; स्वसंतुष्ट : Showing uncritical satisfaction with oneself or one's achievements; self-satisfied and unaware of potential dangers.
- ***Synonyms***: Self-satisfied, smug, self-content, unconcerned, unworried, unvigilant
_Example_: After years of success, the company became **complacent** and failed to innovate, allowing competitors to gain market share. *(Adjective: self-satisfied)*

=====

### IMPLACABLE
@@
**Adjective** | हिंदी: अटल; अप्रसन्न : Unable to be appeased or placated; showing relentless hostility.
- ***Synonyms***: Unappeasable, unyielding, relentless, inexorable, unforgiving, inflexible
_Example_: Despite numerous apologies, she remained **implacable** in her anger over the betrayal. *(Adjective: unable to be appeased)*

=====

### PACIFIC
@@
**Adjective** | हिंदी: शांतिपूर्ण; शांतिप्रिय : Peaceful in character or intent; tending to lessen or avoid conflict.
- ***Synonyms***: Peaceful, nonviolent, calm, tranquil, nonbelligerent, conciliatory
_Example_: Their **pacific** approach to the negotiations helped resolve what could have been a major international dispute. *(Adjective: peaceful)*

=====

### PACIFIST
@@
**Noun** | हिंदी: शांतिवादी; अहिंसावादी : A person who believes that war and violence are unjustifiable and all disputes should be settled by peaceful means.
- ***Synonyms***: Peace advocate, antiwar activist, conscientious objector, nonviolence proponent
_Example_: As a committed **pacifist**, he refused military service and instead volunteered for humanitarian aid work. *(Noun: person opposed to violence and war)*

=====

### PACIFY
@@
**Verb** | हिंदी: शांत करना : To make peaceful; to calm or soothe someone who is angry or upset.
- ***Synonyms***: Appease, calm, soothe, mollify, quiet, tranquilize
_Example_: The negotiator was sent to **pacify** the angry protesters before the situation escalated further. *(Verb: calm or soothe)*

=====

### PACT
@@
**Noun** | हिंदी: संधि; समझौता : A formal agreement between individuals, groups, or nations.
- ***Synonyms***: Agreement, treaty, accord, covenant, deal, contract
_Example_: The two rival companies signed a **pact** agreeing not to poach each other's employees. *(Noun: formal agreement)*

=====

### PEACE
@@
**Noun** | हिंदी: शांति : Freedom from disturbance; tranquility; absence of war or conflict.
- ***Synonyms***: Tranquility, harmony, calm, amity, concord, serenity
_Example_: After decades of civil war, the country finally experienced **peace** following the signing of the treaty. *(Noun: absence of conflict)*

=====

### PLACATE
@@
**Verb** | हिंदी: शांत करना; मनाना : To make someone less angry or hostile, often by concessions.
- ***Synonyms***: Appease, pacify, mollify, soothe, conciliate, propitiate
_Example_: He brought flowers home to **placate** his wife after their argument. *(Verb: make less angry)*

=====

### PLACEBO
@@
**Noun** | हिंदी: प्लेसिबो; मिथ्या औषधि : A substance with no therapeutic effect used as a control in testing drugs or medical treatments.
- ***Synonyms***: Dummy pill, inactive treatment, sugar pill, mock medication
_Example_: The control group received a **placebo** instead of the actual medication being tested in the clinical trial. *(Noun: inactive substitute)*

=====

### PLACID
@@
**Adjective** | हिंदी: शांत; स्थिर : Calm and peaceful; not easily upset or excited.
- ***Synonyms***: Calm, peaceful, tranquil, serene, unruffled, composed
_Example_: The **placid** surface of the lake perfectly reflected the mountains surrounding it. *(Adjective: calm and peaceful)*

=====
## **39 ROGA/ ROGAT** = ask, beg

### ABROGATE
@@
**Verb** | हिंदी: रद्द करना : To abolish, repeal, or do away with (a law, right, or formal agreement).
- ***Synonyms***: Abolish, repeal, annul, cancel, revoke, nullify
_Example_: The government decided to **abrogate** the treaty after the other party repeatedly violated its terms. *(Verb: to formally cancel)*

=====

### ARROGATE
@@
**Verb** | हिंदी: अनधिकार ग्रहण करना : To take or claim something for oneself without justification; to claim unwarrantably or presumptuously.
- ***Synonyms***: Appropriate, usurp, seize, claim, assume, take over
_Example_: He **arrogated** to himself the power to make decisions that should have been made collectively by the board. *(Verb: claim without right)* *(Rare)*

=====

### DEROGATE
@@
**Verb** | हिंदी: अपमानित करना; कम करना : To detract or take away from; to disparage or belittle; to partially repeal or abolish.
- ***Synonyms***: Disparage, belittle, detract, diminish, demean, depreciate
_Example_: His comments seemed to **derogate** from her achievements and undermine her authority in the department. *(Verb: disparage or diminish)* *(Rare)*

=====

### INTERROGATE
@@
**Verb** | हिंदी: पूछताछ करना : To question formally and systematically, especially in a hostile manner.
- ***Synonyms***: Question, examine, probe, inquire, cross-examine, grill
_Example_: The police will **interrogate** the suspect to determine if they were involved in the crime. *(Verb: question formally)*

=====

### PREROGATIVE
@@
**Noun** | हिंदी: विशेषाधिकार : An exclusive right or privilege belonging to a person or group by virtue of position or authority.
- ***Synonyms***: Right, privilege, entitlement, authority, advantage, claim
_Example_: It is the **prerogative** of the president to appoint Supreme Court justices. *(Noun: exclusive right)*

=====

### SUBROGATE
@@
**Verb** | हिंदी: प्रतिस्थापित करना : To substitute one person or thing for another; in law, to substitute one creditor for another.
- ***Synonyms***: Substitute, replace, stand in for, succeed, take over
_Example_: The insurance company can **subrogate** the claim and pursue legal action against the responsible party. *(Verb: substitute rights)* *(Rare)*

=====

### SURROGATE
@@
**Noun, Adjective** | हिंदी: प्रतिनिधि; प्रतिस्थानी : A substitute or replacement for someone or something. Acting as a substitute.
- ***Synonyms***: Substitute, replacement, proxy, stand-in, deputy
_Example_:
1. The celebrity hired a **surrogate** mother to carry and deliver her baby. *(Noun: substitute)*
2. She served as a **surrogate** parent to her younger siblings after their parents died. *(Adjective: substitute)*

=====
## **42 SACR/ SANCT** = sacred, holy

### CONSECRATE
@@
**Verb** | हिंदी: पवित्र करना : To make or declare sacred; to dedicate to a sacred purpose.
- ***Synonyms***: Sanctify, bless, hallow, dedicate, ordain, anoint
_Example_: The bishop will **consecrate** the new church building during a special ceremony next Sunday. *(Verb: make sacred)*

=====

### DESECRATE
@@
**Verb** | हिंदी: अपवित्र करना : To treat a sacred place or thing with violent disrespect; to violate the sanctity of something.
- ***Synonyms***: Profane, violate, defile, blaspheme, dishonor, debase
_Example_: Vandals broke into the cemetery overnight to **desecrate** the historical monuments and gravestones. *(Verb: violate sanctity)*

=====

### SACRAMENT
@@
**Noun** | हिंदी: संस्कार : A religious ceremony or act considered sacred; a visible sign of inward grace in Christian theology.
- ***Synonyms***: Rite, ceremony, ritual, holy ordinance, communion, eucharist
_Example_: Baptism is considered an important **sacrament** in many Christian denominations. *(Noun: sacred religious ritual)*

=====

### SACRED
@@
**Adjective** | हिंदी: पवित्र : Connected with God or dedicated to a religious purpose and thus deserving veneration; considered worthy of spiritual respect or devotion.
- ***Synonyms***: Holy, blessed, hallowed, consecrated, divine, revered
_Example_: The temple houses **sacred** texts that are thousands of years old and handled only by specially trained priests. *(Adjective: holy or revered)*

=====

### SACRIFICE
@@
**Noun** | हिंदी: बलिदान; त्याग : An act of giving up something valued for the sake of something else regarded as more important.
**Verb** | हिंदी: बलिदान करना; त्याग करना : To give up something valued for the sake of other considerations.
- ***Synonyms***:
    - **Noun:**
        - *Offering:* Offering, surrender, oblation, immolation
    - **Verb:**
        - *Give up:* Surrender, forgo, relinquish, give up
_Example_:
1. She made the **sacrifice** of her career to raise her children full-time. *(Noun: act of giving up something valued)*
2. Parents often **sacrifice** their own comfort and needs for their children's well-being. *(Verb: give up something important)*

=====

### SACRILEGE
@@
**Noun** | हिंदी: धर्मद्रोह : The violation or profanation of something sacred or held to be sacred.
- ***Synonyms***: Desecration, profanation, blasphemy, impiety, violation
_Example_: Stealing the ancient artifacts from the temple was considered a **sacrilege** by the entire community. *(Noun: violation of something sacred)*

=====

### SACROSANCT  🪐
@@
**Adjective** | हिंदी: पवित्र / अत्यंत सम्मानित : Regarded as too important or valuable to be interfered with or criticized.
- ***Synonyms***: Sacred, inviolable, untouchable, revered, hallowed,   
_Example_: The Constitution is considered **sacrosanct** in many democratic nations. *(Adjective: too important or respected to be changed or criticized)*

=====


### SANCTIFY
@@
**Verb** | हिंदी: पवित्र करना : To make holy or sacred; to consecrate or set apart as holy.
- ***Synonyms***: Consecrate, bless, hallow, purify, make holy
_Example_: The ceremony will **sanctify** the ground where the new cathedral will be built. *(Verb: make holy)*

=====

### SANCTIMONY
@@
**Noun** | हिंदी: पाखंड; धार्मिक दिखावा : A show of moral superiority or righteousness, especially a hypocritical one.
- ***Synonyms***: Self-righteousness, hypocrisy, pietism, false piety, pharisaism
_Example_: His speech was full of **sanctimony** as he condemned behaviors that he himself was known to engage in privately. *(Noun: hypocritical righteousness)*

=====

### SANCTION
@@
**Noun** | हिंदी: स्वीकृति; प्रतिबंध : Official approval or permission; a penalty imposed for breaking a law or rule.
**Verb** | हिंदी: अनुमोदित करना; प्रतिबंधित करना : To give official permission; to impose a penalty or restriction on.
- ***Synonyms***:
    - **Noun:**
        - *Approval:* Authorization, permission, approval, endorsement
        - *Penalty:* Penalty, punishment, restriction, embargo
    - **Verb:**
        - *Approve:* Authorize, allow, permit, endorse
        - *Penalize:* Punish, penalize, restrict, ban
_Example_:
1. The committee gave its **sanction** to the research project. *(Noun: official approval)*
2. Economic **sanctions** were imposed on the country after repeated human rights violations. *(Noun: penalties)*
3. The government **sanctioned** the new highway construction project. *(Verb: officially approved)*

=====

### SANCTUARY
@@
**Noun** | हिंदी: अभयारण्य; शरण स्थल : A place of refuge or safety; a holy place such as a church; a nature reserve for wildlife.
- ***Synonyms***: Refuge, haven, asylum, retreat, shelter, holy place
_Example_: The old church offered **sanctuary** to homeless people during the severe winter storm. *(Noun: place of safety or refuge)*

=====
## **43 SCRIB/ SCRIP/ SCRIV** = write

### ASCRIBE
@@
**Verb** | हिंदी: आरोपित करना; जिम्मेदार ठहराना : To attribute or assign something to a cause or source.
- ***Synonyms***: Attribute, credit, assign, impute, associate, pin on
_Example_: Historians **ascribe** the fall of the empire to a combination of economic decline and external invasions. *(Verb: attribute to a cause)*

=====

### INSCRIBE
@@
**Verb** | हिंदी: उत्कीर्ण करना; लिखना : To write, carve, or engrave words or symbols on a surface; to dedicate a book or other work with a brief message.
- ***Synonyms***: Engrave, carve, etch, write, imprint, dedicate
_Example_: The author **inscribed** a personal message on the title page of the book for her longtime fan. *(Verb: write or engrave)*

=====

### MANUSCRIPT
@@
**Noun** | हिंदी: पांडुलिपि; हस्तलिखित : A handwritten or typed document, especially an author's text that has not yet been published; an ancient document written by hand.
- ***Synonyms***: Document, text, script, handwriting, composition, draft
_Example_: The ancient **manuscript** was carefully preserved behind glass in the museum, showing text that was over 1,000 years old. *(Noun: handwritten document)*

=====

### PRESCRIBE
@@
**Verb** | हिंदी: निर्धारित करना; नुस्खा लिखना : To issue a medical prescription; to recommend a rule or method to be followed.
- ***Synonyms***: Order, recommend, advise, establish, set, stipulate, dictate
_Example_: The doctor will **prescribe** antibiotics for the infection. *(Verb: medically order)*

=====

### PROSCRIBE
@@
**Verb** | हिंदी: निषिद्ध करना : To forbid, prohibit, or denounce as dangerous or unacceptable.
- ***Synonyms***: Forbid, ban, prohibit, outlaw, denounce, condemn
_Example_: The university has **proscribed** the use of certain websites on campus networks for security reasons. *(Verb: forbid or prohibit)*

=====

### SCRIBBLE
@@
**Verb** | हिंदी: जल्दबाजी में लिखना : To write or draw hastily or carelessly.
**Noun** | हिंदी: अस्पष्ट लेखन : Hurried, careless writing or drawing.
- ***Synonyms***:
    - **Verb:**
        - *Write hastily:* Jot, scrawl, dash off, scratch, doodle
    - **Noun:**
        - *Careless writing:* Scrawl, doodle, chicken scratch, hasty writing
_Example_:
1. She quickly **scribbled** a note on a napkin before rushing out of the café. *(Verb: write hastily)*
2. His **scribbles** in the margins of the book were difficult for anyone else to decipher. *(Noun: careless writing)*

=====

### SCRIBE
@@
**Noun** | हिंदी: लेखक; लिपिक : A person who copies documents or who writes things for others; a professional copyist.
- ***Synonyms***: Copyist, clerk, secretary, amanuensis, writer
_Example_: In ancient Egypt, **scribes** were highly respected as they were among the few who could read and write. *(Noun: professional writer)*

=====

### SCRIVENER
@@
**Noun** | हिंदी: प्रतिलेखक; विधि लेखक : A professional copyist or writer of legal documents and contracts. *(Rare)*
- ***Synonyms***: Copyist, clerk, notary, transcriber, amanuensis, legal writer
_Example_: Before printing became widespread, a **scrivener** would be hired to create multiple copies of important legal documents by hand. *(Noun: professional document writer)* *(Rare)*

=====

### TRANSCRIBE
@@
**Verb** | हिंदी: प्रतिलिपि बनाना; लिप्यंतरण करना : To make a written copy of something; to convert speech into written or printed form.
- ***Synonyms***: Copy, record, write out, reproduce, convert, transliterate
_Example_: The medical assistant had to **transcribe** the doctor's recorded notes after each patient appointment. *(Verb: convert speech to writing)*

=====
## **44 SED/ SID/ SESS** = sit settle

### ASSIDUOUS
@@
**Adjective** | हिंदी: परिश्रमी; अध्यवसायी : Showing great care, attention, and perseverance; hardworking and persistent.
- ***Synonyms***: Diligent, industrious, sedulous, hardworking, persistent, meticulous
_Example_: Her **assiduous** attention to detail made her an invaluable member of the research team. *(Adjective: diligent or hardworking)*

=====

### INSIDIOUS
@@
**Adjective** | हिंदी: छलपूर्ण; कपटपूर्ण : Proceeding in a gradual, subtle way, but with harmful effects.
- ***Synonyms***: Treacherous, crafty, stealthy, sly, deceptive, underhanded
_Example_: The **insidious** nature of the disease meant symptoms weren't noticed until it had advanced significantly. *(Adjective: gradually harmful)*

=====

### RESIDE
@@
**Verb** | हिंदी: निवास करना; रहना : To live or dwell permanently or for a considerable time in a particular place.
- ***Synonyms***: Live, dwell, inhabit, stay, lodge, abide
_Example_: She currently **resides** in a coastal village after moving from the city last year. *(Verb: live or dwell)*

=====

### SEDATE
@@
**Adjective** | हिंदी: शांत; गंभीर : Calm, quiet, and dignified; composed and unhurried.
**Verb** | हिंदी: शामक देना : To administer a sedative drug to calm or induce sleep.
- ***Synonyms***:
    - **Adjective:**
        - *Calm:* Calm, composed, quiet, tranquil, unruffled
    - **Verb:**
        - *Tranquilize:* Tranquilize, calm, pacify, drug, anesthetize
_Example_:
1. The interview committee was impressed by her **sedate** demeanor throughout the challenging questions. *(Adjective: calm and dignified)*
2. The veterinarian had to **sedate** the anxious animal before performing the examination. *(Verb: administer calming drug)*

=====

### SEDENTARY  🪐
@@
**Adjective** | हिंदी: बैठे रहने वाला; निष्क्रिय : Characterized by much sitting and little physical activity.
- ***Synonyms***: Inactive, stationary, desk-bound, sitting, motionless, immobile
_Example_: Doctors warn that a **sedentary** lifestyle increases the risk of cardiovascular disease and other health problems. *(Adjective: physically inactive)*

=====

### SEDIMENT
@@
**Noun** | हिंदी: तलछट : Matter that settles to the bottom of a liquid; dregs or residue.
- ***Synonyms***: Deposit, dregs, precipitate, residue, silt, lees
_Example_: Years of undisturbed aging caused **sediment** to collect at the bottom of the wine bottle. *(Noun: settled particles)*

=====

### SEDULOUS
@@
**Adjective** | हिंदी: परिश्रमी; लगनशील : Diligent in application or attention; showing dedication and hard work.
- ***Synonyms***: Diligent, assiduous, industrious, attentive, persistent, meticulous
_Example_: The researcher's **sedulous** attention to experimental detail ultimately led to the breakthrough discovery. *(Adjective: diligent and persistent)*

=====

### SESSION
@@
**Noun** | हिंदी: सत्र; अधिवेशन : A meeting or period devoted to a particular activity or purpose.
- ***Synonyms***: Meeting, sitting, period, term, assembly, hearing
_Example_: The therapy **session** lasted for an hour and helped address many of her lingering anxieties. *(Noun: period of activity)*

=====

### SUBSIDIARY
@@
**Noun** | हिंदी: सहायक कंपनी : A company controlled by a holding or parent company.
**Adjective** | हिंदी: सहायक; गौण : Serving to assist or supplement; secondary or subordinate.
- ***Synonyms***:
    - **Noun:**
        - *Controlled company:* Branch, affiliate, division, offshoot
    - **Adjective:**
        - *Secondary:* Subordinate, auxiliary, supportive, supplementary, ancillary
_Example_:
1. The corporation acquired several foreign **subsidiaries** to expand its global presence. *(Noun: controlled company)*
2. These issues are **subsidiary** to the main problem we need to address today. *(Adjective: secondary)*

=====

### SUPERSEDE
@@
**Verb** | हिंदी: स्थान लेना; अधिक्रमण करना : To replace in power, authority, or use; to supplant.
- ***Synonyms***: Replace, supplant, displace, succeed, override, take over
_Example_: The new policy will **supersede** all previous regulations regarding employee benefits. *(Verb: replace or override)*

=====
## **45 SEM** = seed

### DISSEMINATE
@@
**Verb** | हिंदी: फैलाना / प्रसारित करना : To spread or disperse (information, knowledge, etc.) widely.
- ***Synonyms***: Spread, circulate, distribute, disperse, propagate, publish
_Example_ : The agency's primary function is to **disseminate** information about climate change to the public. *(Verb: spreading information)*

=====

### SEMINAL
@@
**Adjective** | हिंदी: मौलिक / प्रभावशाली: Strongly influencing later developments
- ***Synonyms***: Groundbreaking, pioneering, original, formative, influential, major
_Example_: His **seminal** work on chaos theory changed the course of physics. *(Adjective: influential, groundbreaking)*

=====

### SEMINAR
@@
**Noun** | हिंदी: संगोष्ठी / विचार-गोष्ठी: A conference or meeting for discussion or training
- ***Synonyms***: Workshop, conference, symposium, forum, colloquium, discussion group
_Example_: I attended a **seminar** on digital marketing strategies last week. *(Noun: meeting for discussion/training)*

=====

### SEMINARY
@@
**Noun** | हिंदी: धर्मशिक्षाविद्यालय / पादरी-विद्यालय : A college that prepares students to be priests, ministers, or rabbis.
- ***Synonyms***: Theological college, divinity school, rabbinical college, religious college
_Example_: He decided to enter the **seminary** to study theology after college. *(Noun: religious training college)*

=====
## **46 SENS/ SENT** = feel, think

### ASSENT
@@
**Noun** | हिंदी: सहमति / स्वीकृति : The expression of approval or agreement.
**Verb** | हिंदी: सहमत होना / स्वीकृति देना : To express approval or agreement, typically officially.
- ***Synonyms***:
    - **Noun:**
        - *Agreement:* Agreement, approval, acceptance, concurrence, endorsement, accord
    - **Verb:**
        - *Agree:* Agree, concur, accept, approve, endorse, accede
_Example_:
1. The committee gave its **assent** to the proposed changes. *(Noun: expression of approval)*
2. The queen is expected to **assent** to the bill later today. *(Verb: express official agreement)*

=====

### CONSENSUAL
@@
**Adjective** | हिंदी: सहमतिपूर्ण / आपसी सहमति का : Relating to or involving agreement and consent between all parties.

- ***Synonyms***:
    - **Adjective:**
        - *By mutual agreement:* Agreed, voluntary, willing, mutual, unanimous, concordant

- ***Antonyms***:
    - **Adjective:**
        - *Without agreement or forced:* Nonconsensual, forced, coerced, compulsory, involuntary, unwilling

_Example_:
1.  Any romantic or physical relationship between employees must be strictly **consensual**. *(Adjective: involving mutual agreement)*

_Word Form Examples_
1.  **CONSENT** 🌟
    - She gave her **consent** for the medical procedure. *(Noun: permission or agreement)*
    - ***Synonyms***: agreement, permission, approval, assent, authorization
    - He refused to **consent** to the new terms of the contract. *(Verb: to agree or give permission)*
    - ***Synonyms***: agree, assent, approve, permit, allow
2.  **CONSENSUS** 🌟
    - After a long debate, the committee finally reached a **consensus**. *(Noun: general agreement)*
    - ***Synonyms***: agreement, unanimity, harmony, accord, concord
3.  **NONCONSENSUAL**
    - The film depicted a **nonconsensual** encounter, which was highly controversial. *(Adjective: without consent)*
    - ***Synonyms***: forced, coerced, involuntary, unwilling

=====
### CONSENT
@@
**Noun** | हिंदी: सहमति / अनुमति : Permission for something to happen or agreement to do something.
**Verb** | हिंदी: सहमत होना / अनुमति देना : To give permission for something to happen; to agree to do something.
- ***Synonyms***:
    - **Noun:**
        - *Permission/Agreement:* Agreement, permission, assent, approval, authorization, accord
    - **Verb:**
        - *Permit/Agree:* Agree, permit, allow, assent, authorize, yield
_Example_:
1. No changes were made without the patient's informed **consent**. *(Noun: permission/agreement)*
2. He **consented** to the interview only after ensuring his anonymity. *(Verb: gave permission/agreed)*

=====

### DISSENT
@@
**Noun** | हिंदी: असहमति / मतभेद : The holding or expression of opinions at variance with those commonly or officially held.
**Verb** | हिंदी: असहमत होना / मतभेद रखना : To hold or express opinions that are different from those commonly or officially held.
- ***Synonyms***:
    - **Noun:**
        - *Disagreement:* Disagreement, opposition, discord, objection, protest, dissension
    - **Verb:**
        - *Disagree:* Disagree, differ, object, protest, demur, dispute
_Example_:
1. There were few voices of **dissent** against the popular policy. *(Noun: expression of disagreement)*
2. Only two judges **dissented** from the majority opinion. *(Verb: expressed disagreement)*

=====

### NONSENSE
@@
**Noun** | हिंदी: बकवास / निरर्थक बात; मूर्खता : Spoken or written words that have no meaning or make no sense; Foolish or unacceptable behavior.
- ***Synonyms***:
    - **Noun:**
        - *Meaningless Words:* Rubbish, gibberish, drivel, balderdash, claptrap, poppycock
        - *Foolishness:* Absurdity, foolishness, silliness, stupidity, idiocy
_Example_:
1. Stop talking **nonsense** and tell me what really happened. *(Noun: meaningless words)*
2. I won't tolerate any more of this **nonsense**; behave yourselves! *(Noun: foolish behavior)*

=====

### RESENT
@@
**Verb** | हिंदी: नाराज़ होना / बुरा मानना / मन में रखना : To feel bitterness, indignation, or displeasure at (a circumstance, action, or person).
- ***Synonyms***: Begrudge, dislike, feel bitter about, be annoyed at, take offense at, take umbrage at
_Example_: She deeply **resented** being passed over for the promotion. *(Verb: felt bitterness/indignation)*

=====

### SENSATION
@@
**Noun** | हिंदी: संवेदना; सनसनी : A physical feeling or impression; a state of great excitement or interest.
- ***Synonyms***:
    - **Noun:**
        - *Physical feeling:* Feeling, perception, impression, sense
        - *Excitement:* Excitement, thrill, stir, commotion, phenomenon
_Example_:
1. The doctor asked if she felt any **sensation** in her injured leg. *(Noun: physical feeling)*
2. Her debut novel created a **sensation** in literary circles. *(Noun: excitement or strong reaction)*

=====

### SENSIBLE
@@
**Adjective** | हिंदी: समझदार; संवेदनशील : Having or showing good judgment or reason; capable of being perceived by the senses.
- ***Synonyms***:
    - **Adjective:**
        - *Good judgment:* Reasonable, practical, rational, wise, judicious
        - *Perceptible:* Noticeable, detectable, perceptible, appreciable
_Example_:
1. Wearing a coat in cold weather is the **sensible** thing to do. *(Adjective: showing good judgment)*
2. There was a **sensible** difference in temperature between the two rooms. *(Adjective: perceptible to the senses)*

=====

### SENSITIVE
@@
**Adjective** | हिंदी: संवेदनशील; सूक्ष्मग्राही : Quick to detect or respond to slight changes, signals, or influences; easily offended or hurt; requiring tact or careful handling.
- ***Synonyms***:
    - **Adjective:**
        - *Responsive:* Responsive, reactive, receptive, perceptive
        - *Easily hurt:* Touchy, thin-skinned, easily offended, vulnerable
        - *Requiring care:* Delicate, careful, diplomatic, discreet
_Example_:
1. Her skin was **sensitive** to sunlight and would burn easily. *(Adjective: physically responsive)*
2. He's very **sensitive** about his height and doesn't like it mentioned. *(Adjective: emotionally vulnerable)*
3. The peace talks involved **sensitive** negotiations that couldn't be discussed publicly. *(Adjective: requiring careful handling)*

=====

### SENSORY
@@
**Adjective** | हिंदी: संवेदी : Relating to or concerned with the reception and transmission of sensations; of or relating to the senses.
- ***Synonyms***:
    - **Adjective:**
        - *Relating to senses:* Perceptual, perceptive, sensing, sense-related
_Example_:
1. Children with autism often experience **sensory** processing difficulties. *(Adjective: relating to the senses)*

=====

### SENSUAL
@@
**Adjective** | हिंदी: इंद्रिय संबंधी / कामुक : Relating to or involving gratification of the senses and physical, especially sexual, pleasure.
- ***Synonyms***: Physical, carnal, voluptuous, luxurious, hedonistic, tactile
_Example_: The soft lighting and smooth music created a **sensual** atmosphere in the room. *(Adjective: relating to gratification of the senses)*

=====

### SENTIENT
@@
**Adjective** | हिंदी: सचेतन / संवेदनशील : Able to perceive or feel things; conscious.
- ***Synonyms***: Conscious, feeling, living, responsive, aware, perceptive
_Example_: Many ethical debates center around the treatment of **sentient** beings. *(Adjective: able to perceive or feel)*

=====

### SENTIMENT
@@
**Noun** | हिंदी: विचार / मत; भावना / मनोभाव; भावुकता : A view or opinion that is held or expressed; A feeling or emotion; Exaggerated and self-indulgent feelings of tenderness, sadness, or nostalgia.
- ***Synonyms***:
    - **Noun:**
        - *View/Opinion:* Opinion, view, belief, attitude, point of view, feeling
        - *Feeling/Emotion:* Emotion, feeling, sensibility, tenderness
        - *Excessive Emotion:* Sentimentality, emotionalism, mawkishness, slush
_Example_:
1.  The general **sentiment** among the voters was one of cautious optimism. *(Noun: view/opinion)*
2.  Despite his tough exterior, he held deep **sentiments** for his family. *(Noun: feeling/emotion)*
3.  The card expressed a touching **sentiment**, though perhaps a bit overly dramatic. *(Noun: exaggerated emotion/sentimentality)*

=====
## **47 SEQ/ SEC** = follow

### CONSECUTIVE
@@
**Adjective** | हिंदी: लगातार / क्रमिक : Following continuously; in unbroken or logical sequence.
- ***Synonyms***: Successive, sequential, continuous, uninterrupted, following, running
_Example_: She was absent from work for three **consecutive** days due to illness. *(Adjective: following one after another without interruption)*

=====

### OBSEQUIOUS
@@
**Adjective** | हिंदी: चापलूस / खुशामदी : Obedient or attentive to an excessive or servile degree.
- ***Synonyms***: Servile, sycophantic, fawning, subservient, ingratiating, unctuous
_Example_: His **obsequious** behavior towards the manager made his colleagues uncomfortable. *(Adjective: overly attentive or servile)*

=====

### SEQUEL
@@
**Noun** | हिंदी: अगली कड़ी; परिणाम : A published, broadcast, or recorded work that continues the story or develops the theme of an earlier one; Something that takes place after or as a result of an earlier event.
- ***Synonyms***: Follow-up, successor, continuation, next installment, Result, consequence, outcome, aftermath, effect
_Example_:
1.  Many fans found the **sequel** less engaging than the original movie. *(Noun: continuation of a story)*
2.  The investigation was a direct **sequel** to the allegations made earlier. *(Noun: consequence/result)*

=====

### SEQUENCE
@@
**Noun** | हिंदी: क्रम / अनुक्रम; सिलसिला : A particular order in which related things follow each other; A set of related events, movements, or items that follow each other.
**Verb** | हिंदी: क्रम में लगाना : Arrange in a particular order.
- ***Synonyms***:
    - **Noun:**
        - *Order:* Order, succession, progression, series, arrangement, chain, course
        - *Set of events:* Series, succession, run, string
    - **Verb:**
        - *Arrange:* Order, arrange, organize, marshal, string together, prioritize
_Example_:
1.  Please arrange the files in chronological **sequence**. *(Noun: particular order)*
2.  The film contained a long and complex dream **sequence**. *(Noun: set of related events/movements)*
3.  We need to **sequence** the tasks carefully to meet the deadline. *(Verb: arrange in order)*

=====

### SUBSEQUENT
@@
**Adjective** | हिंदी: बाद का / अनुगामी / परवर्ती : Coming after something in time; following.
- ***Synonyms***: Following, later, succeeding, ensuing, consequent, future, next
_Example_: The initial meeting was productive, and **subsequent** discussions led to a final agreement. *(Adjective: coming after in time)*

=====
## **48 SIMI/ SIMU/ SEMBLE** =same together

### ASSEMBLE
@@
**Verb** | हिंदी: इकट्ठा करना; जमा करना : To gather together people or things; to fit together parts to make a whole.
- ***Synonyms***:
    - **Verb:**
        - *Gather together:* Gather, collect, congregate, convene
        - *Put together:* Construct, build, put together, piece together
_Example_:
1. The manager asked all employees to **assemble** in the conference room. *(Verb: gather together)*
2. You need to **assemble** the furniture before you can use it. *(Verb: put together)*

=====

### FACSIMILE
@@
**Noun** | हिंदी: प्रतिलिपि; फैक्स : An exact copy or reproduction of something; a system for transmitting documents via telephone lines (fax).
- ***Synonyms***:
    - **Noun:**
        - *Exact copy:* Replica, reproduction, duplicate, copy
        - *Document transmission:* Fax, telefax
_Example_:
1. The museum displayed a **facsimile** of the ancient manuscript. *(Noun: exact copy)*
2. Before email became common, businesses relied on **facsimile** machines to send urgent documents. *(Noun: fax transmission)*

=====

### RESEMBLE
@@
**Verb** | हिंदी: मिलता-जुलता होना : To look like or be similar to someone or something else.
- ***Synonyms***: Look like, be similar to, take after, mirror, echo
_Example_: The young girl strongly **resembles** her grandmother in both appearance and mannerisms. *(Verb: looks like)*

=====

### SIMILAR
@@
**Adjective** | हिंदी: समान; सदृश : Having characteristics that are alike, but not identical.
- ***Synonyms***: Alike, comparable, resembling, akin, analogous, like
_Example_: The twins wore **similar** dresses to the party, but in different colors. *(Adjective: resembling but not identical)*

=====

### SIMULACRUM
@@
**Noun** | हिंदी: प्रतिकृति / प्रतिरूप : An image or representation of someone or something;
- ***Synonyms***: Image, likeness, replica, effigy, representation
_Example_: The museum displayed a **simulacrum** of the ancient artifact, as the original was too fragile. *(Noun: image/representation)*

=====

### SIMULATE
@@
**Verb** | हिंदी: नकल करना / अनुकरण करना; ढोंग करना / बहाना करना; कंप्यूटर मॉडल बनाना : Imitate the appearance or character of; Pretend to have or feel (an emotion); Produce a computer model of (something, especially for the purpose of study).
- ***Synonyms***:
    - **Verb:**
        - *Imitate:* Imitate, replicate, reproduce, mimic, duplicate, copy
        - *Pretend:* Feign, pretend, fake, affect, put on, sham
        - *Model:* Model, computerize, represent, emulate
_Example_:
1.  Pilots train using machines that **simulate** flight conditions. *(Verb: imitate appearance/character)*
2.  She managed to **simulate** calmness despite her inner turmoil. *(Verb: pretend to feel)*
3.  Researchers **simulate** complex chemical reactions using powerful computers. *(Verb: produce a computer model)*

=====

### SIMULTANEOUS
@@
**Adjective** | हिंदी: समकालिक / एक साथ होने वाला : Occurring, operating, or done at the same time.
- ***Synonyms***: Concurrent, coincident, contemporaneous, synchronous, parallel, coinciding
_Example_: The explosion and the flash of light were **simultaneous**. *(Adjective: occurring at the same time)*

=====
## **49 SOMN/ SOP** = sleep

### INSOMNIA
@@
**Noun** | हिंदी: अनिद्रा : Habitual sleeplessness; inability to sleep.
- ***Synonyms***: Sleeplessness, wakefulness, restlessness, inability to sleep
_Example_: Stress and anxiety are common causes of **insomnia**. *(Noun: inability to sleep)*

=====

### SOMNAMBULIST
@@
**Noun** | हिंदी: नींद में चलनेवाला : A person who walks around while asleep; a sleepwalker.
- ***Synonyms***: Sleepwalker, noctambulist
_Example_: The family installed alarms after discovering their child was a **somnambulist**. *(Noun: sleepwalker)*

=====

### SOMNOLENT
@@
**Adjective** | हिंदी: उनींदा / निद्रालु : Sleepy or drowsy; inducing drowsiness.
- ***Synonyms***: Drowsy, sleepy, lethargic, languid, drowsy-making, soporific
_Example_: The warm room and the monotonous lecture left the students feeling **somnolent**. *(Adjective: sleepy/drowsy)*

=====

### SOPOR
@@
**Noun** | हिंदी: गहरी नींद / तंद्रा / जड़ता *(Rare)* : A state of deep sleep or lethargy; abnormal sleepiness often induced by drugs or illness.
- ***Synonyms***: Sleep, slumber, lethargy, stupor, torpor, drowsiness
_Example_: The medication induced a state of **sopor** in the patient. *(Noun: deep sleep/lethargy)*

=====
## **50 SPEC/ SPIC/ SPECT** = look, see

### EXPECT
@@
**Verb** | हिंदी: आशा करना; उम्मीद करना : To anticipate or look forward to something; to consider something likely to happen; to require something from someone.
- ***Synonyms***:
    - **Verb:**
        - *Anticipate:* Anticipate, await, look forward to, hope for
        - *Consider likely:* Think, believe, assume, presume
        - *Require:* Require, demand, call for, count on
_Example_:
1. We **expect** the package to arrive tomorrow. *(Verb: anticipate)*
2. I **expect** you to complete this assignment by Friday. *(Verb: require)*

=====

### PERSPECTIVE
@@
**Noun** | हिंदी: दृष्टिकोण; परिप्रेक्ष्य : A particular way of viewing things; the art of representing three-dimensional objects on a two-dimensional surface.
- ***Synonyms***:
    - **Noun:**
        - *Viewpoint:* Viewpoint, outlook, standpoint, approach, angle
        - *Visual representation:* Aspect, vista, view, representation
_Example_:
1. Studying history gives us a broader **perspective** on current events. *(Noun: viewpoint or approach)*
2. The artist used linear **perspective** to create depth in the painting. *(Noun: technique of visual representation)*

=====

### PERSPICACIOUS
@@
**Adjective** | हिंदी: तीक्ष्ण बुद्धि वाला; सूक्ष्मदर्शी : Having keen mental perception and understanding; discerning. *(Rare)*
- ***Synonyms***: Astute, insightful, perceptive, discerning, shrewd
_Example_:  The **perspicacious** detective noticed subtle clues that others had missed. *(Adjective: having keen perception)*

=====

### PERSPICUOUS
@@
**Adjective** | हिंदी: स्पष्ट; सुबोध : Clearly expressed and easily understood; lucid. *(Rare)*
- ***Synonyms***:  Clear, lucid, plain, intelligible, comprehensible, transparent
_Example_: Her **perspicuous** explanation of the complex theory made it accessible to everyone. *(Adjective: clearly expressed)*

=====

### RETROSPECTIVE
@@
**Adjective** | हिंदी: पूर्वोन्मुखी; पश्चदर्शी : Looking back on or dealing with past events or situations.
**Noun** | हिंदी: पूर्वावलोकन; प्रदर्शनी : An exhibition or compilation showing the development of an artist's work over time; a survey or review of past events.
- ***Synonyms***:
    - **Adjective:**
        - *Looking back:* Backward-looking, reflective, reminiscent, nostalgic
    - **Noun:**
        - *Exhibition:* Review, survey, exhibition, anthology
_Example_:
1. The book provides a **retrospective** analysis of the political decisions made during the crisis. *(Adjective: looking back at past events)*
2. The museum is hosting a **retrospective** of the famous photographer's work spanning five decades. *(Noun: exhibition reviewing past work)*

=====

### SPECTER
@@
**Noun** | हिंदी: भूत/प्रेत; डरावना विचार : A ghost or apparition; a threatening or ominous thing that causes fear or dread.
- ***Synonyms***:
    - **Noun:**
        - *Ghost:* Ghost, phantom, apparition, wraith
        - *Threat:* Threat, menace, shadow, cloud, foreboding
_Example_:
1. The abandoned house was said to be haunted by the **specter** of its former owner. *(Noun: ghost)*
2. The **specter** of economic collapse loomed over the country during the financial crisis. *(Noun: threatening possibility)*

=====
## **52 SPIR** = breathe, live

### ASPIRE
@@
**Verb** | हिंदी: अभिलाषा करना / आकांक्षा रखना : To direct one's hopes or ambitions towards achieving something.
- ***Synonyms***: Aim, desire, hope for, seek, pursue, strive for
_Example_: Many young athletes **aspire** to compete in the Olympics. *(Verb: aim for/desire)*

=====

### CONSPIRE
@@
**Verb** | हिंदी: षड्यंत्र रचना / साज़िश करना; मिलकर काम करना (प्रतिकूल) : Make secret plans jointly to commit an unlawful or harmful act
- ***Synonyms***: Plot, scheme, intrigue, collude, connive, machinate
_Example_:
1.  The group was accused of **conspiring** to overthrow the government. *(Verb: plot secretly)*
2.  The weather and traffic seemed to **conspire** to make him late for the important interview. *(Verb: act together negatively)*

=====

### EXPIRE
@@
**Verb** | हिंदी: समाप्त होना / अवधि समाप्त होना; मर जाना; साँस छोड़ना : (Of a document, authorization, or agreement) cease to be valid, typically after a fixed period; (Of a person) die; Exhale (air) from the lungs.
- ***Synonyms***:
    - **Verb:**
        - *Cease Validity:* Run out, lapse, become invalid, terminate, finish, end
        - *Die:* Pass away, perish, die, decease, breathe one's last
        - *Exhale:* Breathe out, exhale, blow out
_Example_:
1.  My driver's license will **expire** next month. *(Verb: cease validity)*
2.  The patient **expired** peacefully during the night. *(Verb: die)*
3.  He inhaled deeply and then **expired** slowly. *(Verb: exhale)*

=====

### INSPIRE
@@
**Verb** | हिंदी: प्रेरित करना / प्रोत्साहित करना; जगाना / उत्पन्न करना; साँस लेना : To fill (someone) with the urge or ability to do or feel something, especially something creative; To create (a feeling or emotion) in a person; To breathe in (air); inhale.
- ***Synonyms***:
    - **Verb:**
        - *Motivate/Encourage:* Motivate, encourage, stimulate, arouse, influence, galvanize
        - *Evoke Feeling:* Evoke, induce, kindle, generate, prompt, give rise to
        - *Inhale:* Breathe in, inhale, draw in
_Example_:
1.  Her courage **inspired** everyone who knew her story. *(Verb: motivate/encourage)*
2.  The rugged coastline **inspired** a sense of awe in the visitors. *(Verb: evoke feeling)*
3.  We **inspire** oxygen with every breath. *(Verb: inhale - less common usage)*

=====

### PERSPIRE
@@
**Verb** | हिंदी: पसीना आना / पसीजना : Give out sweat through the pores of the skin as the result of heat, physical exertion, or stress.
- ***Synonyms***: Sweat, swelter, glow (euphemism), exude moisture
_Example_: It's natural to **perspire** heavily when exercising in the heat. *(Verb: sweat)*

=====

### RESPIRE
@@
**Verb** | हिंदी: साँस लेना / श्वसन करना : (Of a living organism) take in oxygen and give out carbon dioxide through breathing or analogous processes; breathe.
- ***Synonyms***: Breathe, inhale and exhale, oxygenate, undergo respiration
_Example_: Fish **respire** using gills to extract oxygen from water. *(Verb: breathe/undergo respiration)*

=====

### SPIRIT
@@
**Noun** | हिंदी: आत्मा / रूह; मन / अंतरात्मा; मनोभाव / भावना / उत्साह / मिज़ाज; मदिरा / शराब; प्रेत / भूत : The nonphysical part of a person, the seat of emotions and character (soul); The prevailing quality or attitude; Strong distilled alcoholic liquor; A supernatural being.
**Verb** | हिंदी: चुपके से ले जाना / उड़ा ले जाना : Convey rapidly and secretly.
- ***Synonyms***:
    - **Noun:**
        - *Soul/Essence:* Soul, psyche, core, essence, inner self
        - *Mood/Attitude:* Mood, attitude, morale, enthusiasm, character, ethos, tenor, vibe
        - *Alcohol:* Liquor, alcohol, hard liquor (often plural: spirits)
        - *Supernatural Being:* Ghost, phantom, apparition, spectre, entity
    - **Verb:**
        - *Convey Secretly:* Whisk away/off, carry off, snatch away, transport secretly
_Example_:
1.  Yoga aims to unite body, mind, and **spirit**. *(Noun: soul/essence)*
2.  Despite the challenges, the team maintained a positive **spirit**. *(Noun: mood/attitude)*
3.  The bar stocked a wide variety of **spirits** from around the world. *(Noun: alcohol)*
4.  Legend says the **spirit** of a knight haunts the castle grounds. *(Noun: supernatural being)*
5.  The security team managed to **spirit** the VIP away before the crowd grew too large. *(Verb: convey secretly)*

=====

### TRANSPIRE
@@
**Verb** | हिंदी: घटित होना; पता लगना / प्रकट होना : Occur; happen; Prove to be the case; become known; 
- ***Synonyms***:
    - **Verb:**
        - *Occur/Happen:* Happen, occur, take place, come about, arise, chance
        - *Become Known:* Emerge, come to light, become known, turn out, be revealed
_Example_:
1.  No one could predict what would **transpire** during the unpredictable meeting. *(Verb: occur/happen)*
2.  It later **transpired** that the witness had lied under oath. *(Verb: become known)*

=====
## **53 TERM** = period, end

### DETERMINE
@@
**Verb** | हिंदी: पता लगाना / निर्धारित करना; तय करना / निश्चित करना; ठान लेना / संकल्प करना : Ascertain or establish exactly, typically as a result of research or calculation; Cause (something) to occur in a particular way or be the decisive factor in; Firmly decide.
- ***Synonyms***:
    - **Verb:**
        - *Ascertain/Establish:* Ascertain, find out, establish, discover, verify, check
        - *Cause/Influence:* Control, decide, influence, shape, dictate, govern
        - *Decide Firmly:* Decide, resolve, choose, conclude, settle, make up one's mind
_Example_:
1.  Scientists are still trying to **determine** the exact cause of the phenomenon. *(Verb: ascertain/establish)*
2.  Supply and demand often **determine** the price of goods. *(Verb: cause/influence)*
3.  She **determined** to finish the race despite her injury. *(Verb: decide firmly)*

=====

### INTERMINABLE
@@
**Adjective** | हिंदी: अंतहीन / अनंत : Endless or apparently endless (often used hyperbolically).
- ***Synonyms***: Endless, never-ending, incessant, ceaseless, unending, perpetual
_Example_: The wait in the queue felt **interminable**. *(Adjective: seemingly endless)*

=====

### INTERMITTENT
@@
**Adjective** | हिंदी: रुक-रुक कर होनेवाला / आंतरायिक : Occurring at irregular intervals; not continuous or steady.
- ***Synonyms***: Sporadic, irregular, fitful, occasional, discontinuous, periodic
_Example_: We experienced **intermittent** rain showers throughout the afternoon. *(Adjective: occurring irregularly)*

=====

### TERMINAL
@@
**Noun** | हिंदी: अंतिम स्टेशन / अड्डा / टर्मिनल; सिरा / संयोजक बिंदु; टर्मिनल (कंप्यूटर) : The end of a transport route, or a station/building there; A point of connection for an electric circuit; A device for inputting/displaying computer data.
**Adjective** | हिंदी: अंतिम / अंत का; असाध्य (रोग) / अंतिम (अवस्था) : Relating to, forming, or situated at the end or extremity; (Of a disease) predicted to lead to death; incurable.
- ***Synonyms***:
    - **Noun:**
        - *Transport End:* Station, depot, terminus, endpoint, end-of-the-line
        - *Connection Point:* Connector, point, junction, pole, contact
        - *Computer Device:* Workstation, VDU, console, input/output device
    - **Adjective:**
        - *End/Extremity:* Final, last, concluding, ultimate, endmost, closing
        - *Incurable Disease:* Incurable, fatal, deadly, mortal, lethal, final stage
_Example_:
1.  We need to be at the airport **terminal** two hours before departure. *(Noun: transport building)*
2.  Connect the wire to the positive **terminal** of the battery. *(Noun: connection point)*
3.  Please enter your password at the **terminal**. *(Noun: computer device)*
4.  The train reached the **terminal** station. *(Adjective: end/final)*
5.  Sadly, the patient was diagnosed with a **terminal** illness. *(Adjective: incurable disease)*

=====
## **54 TREM/ TREP** = shake

### INTREPID
@@
**Adjective** | हिंदी: निडर / साहसी : Fearless; adventurous (often used for rhetorical or humorous effect).
- ***Synonyms***: Fearless, brave, courageous, valiant, bold, adventurous
_Example_: The **intrepid** explorer ventured deep into the uncharted jungle. *(Adjective: fearless/adventurous)*

=====

### TREMBLE
@@
**Verb** | हिंदी: काँपना : Shake involuntarily, typically as a result of anxiety, excitement, or frailty.
**Noun** | हिंदी: कंपन / कंपकंपी : A shaking movement.
- ***Synonyms***:
    - **Verb:**
        - *Shake involuntarily:* Shake, quiver, shiver, shudder, vibrate, quaver
    - **Noun:**
        - *Shaking movement:* Shake, quiver, shiver, shudder, tremor, vibration
_Example_:
1.  His hands began to **tremble** as he nervously opened the letter. *(Verb: shake involuntarily)*
2.  A slight **tremble** ran through the floorboards as the truck passed by. *(Noun: shaking movement)*

=====

### TREMOR
@@
**Noun** | हिंदी: कंपन / कंपकंपी; हल्का भूकंप : An involuntary quivering movement; A slight earthquake.
- ***Synonyms***:
    - **Noun:**
        - *Quivering:* Shake, trembling, quiver, shiver, vibration, shudder
        - *Slight Earthquake:* Earth tremor, quake, temblor, microseism
_Example_:
1.  A **tremor** in his voice betrayed his anxiety. *(Noun: involuntary quivering)*
2.  The region experienced a minor **tremor** last night, but no damage was reported. *(Noun: slight earthquake)*

=====

### TREPID
@@
**Adjective** | हिंदी: भयभीत / डरपोक *(Rare)* : Fearful, anxious, or trembling.
- ***Synonyms***: Fearful, apprehensive, frightened, anxious, timid, nervous
_Example_: The **trepid** child hid behind his mother's legs. *(Adjective: fearful/trembling)*

=====
## **55 VAL/ VAIL** = value, strength

### AMBIVALENT
@@
**Adjective** | हिंदी: द्विधाग्रस्त : Having mixed or contradictory feelings about someone or something.
- ***Synonyms***: Uncertain, undecided, conflicted, torn, indecisive
_Example_: She felt **ambivalent** about accepting the job offer, weighing the better salary against the longer commute. *(Adjective: experiencing conflicting feelings)*

=====

### AVAIL
@@
**Verb** | हिंदी: लाभ उठाना; उपयोग करना : To use or take advantage of (an opportunity or available resource); To be of use or help.
**Noun** | हिंदी: लाभ; फायदा : Help, benefit, or advantage; Use or effectiveness.
- ***Synonyms***:
    - **Verb:**
        - *Use or take advantage of:* Utilize, use, employ, exploit
        - *Be of use:* Help, benefit, serve, assist
    - **Noun:**
        - *Benefit or advantage:* Benefit, advantage, use, utility, value
_Example_:
1. They decided to **avail** themselves of the free legal service. *(Verb: to make use of)*
2. His efforts were of little **avail** in changing the company's policy. *(Noun: benefit or advantage)*

=====

### CONVALESCENCE
@@
**Noun** | हिंदी: स्वास्थ्य-लाभ : The gradual recovery of health and strength after illness or injury.
- ***Synonyms***: Recovery, recuperation, rehabilitation, healing, mending
_Example_: After his surgery, the doctor recommended a month of **convalescence** at home before returning to work. *(Noun: period of recovery)*

=====

### COUNTERVAIL
@@
**Verb** | हिंदी: प्रतिसंतुलन करना / बराबरी करना / निष्प्रभाव करना : To act against (something) with equal force; counteract; offset.
- ***Synonyms***: Counteract, counterbalance, offset, compensate for, neutralize, negate
_Example_: The company hopes the increased efficiency will **countervail** the initial investment costs. *(Verb: counteract/offset)*

=====

### PREVAIL
@@
**Verb** | हिंदी: प्रचलित होना; विजयी होना : To be widespread or current; To prove more powerful than opposing forces; be victorious.
- ***Synonyms***:
    - **Verb:**
        - *To be widespread:* Predominate, exist, persist, be common
        - *To be victorious:* Triumph, win, overcome, succeed
_Example_:
1. Silence **prevailed** throughout the hall as the conductor raised his baton. *(Verb: to be widespread or dominant)*
2. Despite the challenges, truth and justice will ultimately **prevail**. *(Verb: to triumph or be victorious)*

=====

### PREVALENT
@@
**Adjective** | हिंदी: प्रचलित / व्यापक / वर्तमान : Widespread in a particular area or at a particular time; predominant.
- ***Synonyms***: Widespread, common, prevailing, frequent, general, rampant, ubiquitous
_Example_: This type of flu is most **prevalent** during the winter months. *(Adjective: widespread/common)*

=====

### VALIANT
@@
**Adjective** | हिंदी: वीर / बहादुर / साहसी : Possessing or showing courage or determination.
- ***Synonyms***: Brave, courageous, valorous, heroic, fearless, gallant, bold
_Example_: Despite being outnumbered, the **valiant** soldiers fought bravely. *(Adjective: courageous/determined)*

=====

### VALOR
@@
**Noun** | हिंदी: वीरता / शौर्य / पराक्रम : Great courage in the face of danger, especially in battle.
- ***Synonyms***: Courage, bravery, heroism, boldness, fearlessness, gallantry
_Example_: He was awarded the highest military honor for his **valor** on the battlefield. *(Noun: great courage)*

=====
## **56 VER** = true

### AVER
@@
**Verb** | हिंदी: दावे से कहना / बलपूर्वक कहना : To state or assert to be the case; declare positively. *(Formal)*
- ***Synonyms***: Assert, declare, state, affirm, claim, profess
_Example_ : She **averred** that she had never seen the man before. *(Verb: stating something firmly)*

=====


### Veracious  🪐
@@
**Adjective** | हिंदी: सत्यवादी : Speaking or representing the truth; truthful.
- ***Synonyms***: Truthful, honest, accurate, factual, candid, forthright
_Example_ :
1. Known for being a **veracious** reporter, his articles were always trusted by the public. *(Adjective: habitually truthful)*
2. The jury questioned the **veracity** of the witness's testimony. *(Noun: accuracy or truthfulness)*

=====
### VERDICT
@@
**Noun** | हिंदी: निर्णय / फैसला : A decision on an issue of fact in a civil or criminal case or an inquest; an opinion or judgment.
- ***Synonyms***: Judgment, decision, finding, ruling, conclusion, opinion
_Example_ : The jury reached a guilty **verdict** after six hours of deliberation. *(Noun: formal decision in court)*


=====

### VERIFY
@@
**Verb** | हिंदी: सत्यापित करना / पुष्टि करना : To make sure or demonstrate that (something) is true, accurate, or justified.
- ***Synonyms***: Confirm, substantiate, corroborate, validate, authenticate, check
_Example_ : You must **verify** your account before you can log in. *(Verb: confirming accuracy)*

=====

### VERISIMILAR
@@
**Adjective** | हिंदी: सत्य जैसा लगने वाला / सत्यभासी : Having the appearance of being true or real; probable or likely.
- ***Synonyms***: Realistic, plausible, believable, lifelike, credible, authentic-seeming
_Example_ : The historical novel was praised for its **verisimilar** characters and dialogue. *(Adjective: appearing true or real)*

=====
## **57 VERB** = word

### VERBAL
@@
**Adjective** | हिंदी: मौखिक; शाब्दिक : Spoken rather than written; relating to words.
- ***Synonyms***: Oral, spoken, vocal, Linguistic, lexical
_Example_:
1. The agreement was only **verbal**, so it was not legally binding. *(Adjective: spoken rather than written)*
2. His **verbal** skills improved after taking the communication course. *(Adjective: relating to words)*

=====

### VERBATIM
@@
**Adverb/Adjective** | हिंदी: शब्दशः : In exactly the same words as were used originally.
- ***Synonyms***: Word for word, exactly, precisely, literally, accurately
_Example_: The speech was transcribed **verbatim** to preserve its original meaning. *(Adverb: in exactly the same words)*

=====

### VERBIAGE
@@
**Noun** | हिंदी: शब्दाडंबर : Excessive or unnecessary use of words, often making something unclear.
- ***Synonyms***: Wordiness, verbosity, prolixity, redundancy, rhetoric
_Example_: The contract was filled with legal **verbiage**, making it difficult to understand. *(Noun: excessive use of words)*

=====
## **58 VERT/ VERS** = turn

### AVERSE
@@
**Adjective** | हिंदी: विरुद्ध / अनिच्छुक : Having a strong dislike of or opposition to something.
- ***Synonyms***: Opposed, reluctant, unwilling, disinclined, loath, resistant
_Example_ : He seems to be **averse** to hard work. *(Adjective: having a strong dislike or opposition)*

=====

### AVERT
@@
**Verb** | हिंदी: फेर लेना; टालना / रोकना : Turn away (one's eyes or thoughts); Prevent or ward off (an undesirable occurrence).
- ***Synonyms***:
    - **Verb:**
        - *Turn away:* Look away, turn aside.
        - *Prevent/Ward off:* Prevent, avoid, preclude, stave off, forestall.
_Example_:
1.  She **averted** her eyes during the scary parts of the movie. *(Verb: turning away eyes/thoughts)*
2.  Quick action by the pilot **averted** a potential disaster. *(Verb: preventing an undesirable occurrence)*

=====

### CONVERT
@@
**Verb** | हिंदी: बदलना / रूपांतरित करना; धर्म परिवर्तन कराना / मत बदलना : Change the form, character, or function of something; Cause to change in opinion, belief, or faith.
**Noun** | हिंदी: धर्म-परिवर्तित व्यक्ति / नव-विश्वासी : A person who has been persuaded to change their religious faith or other beliefs.
- ***Synonyms***:
    - **Verb:**
        - *Change form/function:* Transform, change, adapt, modify, alter, metamorphose.
        - *Change belief:* Persuade, convince, win over, proselytize.
    - **Noun:**
        - *Person changed:* Proselyte, neophyte, disciple, new believer.
_Example_:
1.  The old warehouse was **converted** into luxury apartments. *(Verb: changing form/function)*
2.  Missionaries attempted to **convert** the indigenous population. *(Verb: causing change in belief)*
3.  He is a recent **convert** to vegetarianism. *(Noun: person who changed beliefs)*

=====

### DIVERGE
@@
**Verb** | हिंदी: अलग होना / भिन्न होना; विचलित होना; मतभेद होना : (Of a road, route, or line) separate from another route and go in a different direction; Depart from a set course or standard; Differ in opinion.
- ***Synonyms***:
    - **Verb:**
        - *Separate/Go apart:* Branch off, fork, split, divide, separate.
        - *Deviate:* Stray, digress, veer, depart.
        - *Differ:* Disagree, vary, contrast.
_Example_:
1.  The path **diverges** into two trails just ahead. *(Verb: separating or branching off)*
2.  His account of the event **diverged** significantly from the official report. *(Verb: deviating or differing)*
3.  Our opinions on the matter **diverge** quite strongly. *(Verb: differing in opinion)*

=====

### DIVERT
@@
**Verb** | हिंदी: मोड़ना / मार्ग बदलना; ध्यान बँटाना; मनोरंजन करना : Cause (someone or something) to change course or turn from one direction to another; Distract (someone or their attention) from something; Entertain or amuse.
- ***Synonyms***:
    - **Verb:**
        - *Change course:* Reroute, redirect, deflect, switch.
        - *Distract:* Sidetrack, draw away, lead away.
        - *Entertain:* Amuse, entertain, delight, regale.
_Example_:
1.  Traffic was **diverted** around the accident scene. *(Verb: changing course)*
2.  The loud noise **diverted** my attention from the book. *(Verb: distracting attention)*
3.  A magician was hired to **divert** the guests during the reception. *(Verb: entertaining or amusing)*

=====

### INCONTROVERTIBLE
@@
**Adjective** | हिंदी: अकाट्य / निर्विवाद : Not able to be denied or disputed.
- ***Synonyms***: Indisputable, undeniable, irrefutable, unquestionable, unarguable, beyond doubt
_Example_ : The DNA evidence provided **incontrovertible** proof of his guilt. *(Adjective: unable to be disputed)*

=====

### PERVERT
@@
**Verb** | हिंदी: दुरुपयोग करना; भ्रष्ट करना : To misuse or distort something from its original purpose or meaning; to corrupt morally.
**Noun** | हिंदी: विकृत व्यक्ति : A person whose behavior, especially sexual, is considered abnormal or unacceptable.
- ***Synonyms***:
    - **Verb:**
        - *Misuse or distort:* Misapply, twist, warp, distort
        - *Corrupt morally:* Debase, corrupt, deprave
    - **Noun:**
        - *Person with abnormal behavior:* Deviant, degenerate, sicko
_Example_:
1. The lawyer accused the media of trying to **pervert** the course of justice. *(Verb: to misuse or distort)*
2. The community was shocked to learn that he was a **pervert** hiding behind a respectable facade. *(Noun: person with abnormal behavior)*

=====

### REVERT
@@
**Verb** | हिंदी: लौटना; पुनर्जनन करना : To return to a previous state, condition, or behavior; to go back to an earlier topic or owner.
- ***Synonyms***: Regress, relapse, backslide, Return, refer, go back
_Example_:
1. After trying the new software, the company decided to **revert** to the older version. *(Verb: return to previous state)*
2. Ownership of the land will **revert** to the state if no heirs are found. *(Verb: go back to owner)*

=====

### SUBVERT
@@
**Verb** | हिंदी: उलट देना; भ्रष्ट करना : To undermine or overthrow, especially an established system or institution
- ***Synonyms***: Undermine, destabilize, overthrow, topple
_Example_: The rebels sought to **subvert** the government through covert operations. *(Verb: to undermine or overthrow)*

=====

### VERSATILE
@@
**Adjective** | हिंदी: बहुमुखी : Able to adapt or be used for many different purposes or functions; having varied skills or abilities.
- ***Synonyms***: Adaptable, flexible, multifaceted, all-purpose, resourceful
_Example_: The **versatile** actor excelled in both comedy and drama roles. *(Adjective: having varied skills or abilities)*

=====
## **59 VICT/ VINC** = conquer

### CONVICT
@@
**Verb** | हिंदी: दोषी ठहराना : To find or declare someone guilty of a criminal offense.
**Noun** | हिंदी: अपराधी / कैदी : A person found guilty of a crime and serving a sentence.
- ***Synonyms***:
    - **Verb:**
        - *Find guilty:* Condemn, sentence, find guilty
    - **Noun:**
        - *Person found guilty:* Prisoner, felon, inmate, offender
_Example_:
1. The jury took only two hours to **convict** the defendant of fraud. *(Verb: to find guilty)*
2. The **convict** was transferred to a maximum-security prison. *(Noun: person found guilty)*

=====

### CONVINCE
@@
**Verb** | हिंदी: विश्वास दिलाना : To persuade someone to believe or do something through reasoning or argument.
- ***Synonyms***: Persuade, assure, satisfy, sway, win over
_Example_: She managed to **convince** the team to adopt her innovative strategy. *(Verb: to persuade through reasoning)*

=====

### EVICT
@@
**Verb** | हिंदी: बेदखल करना : To remove someone from a property or land by legal process.
- ***Synonyms***: Expel, eject, oust, remove, dispossess
_Example_: The landlord decided to **evict** the tenant for not paying rent. *(Verb: to remove by legal process)*

=====

### EVIDENT
@@
**Adjective** | हिंदी: स्पष्ट : Clearly seen or understood; obvious.
- ***Synonyms***: Apparent, obvious, clear, manifest, noticeable
_Example_: Her disappointment was **evident** in her facial expression. *(Adjective: clearly seen or understood)*

=====

### VANQUISH
@@
**Verb** | हिंदी: पराजित करना : To defeat thoroughly in a competition, conflict, or battle.
- ***Synonyms***: Conquer, defeat, overcome, subdue, crush
_Example_: The hero managed to **vanquish** the dragon and save the village. *(Verb: to defeat thoroughly)*

=====

### VICTOR
@@
**Noun** | हिंदी: विजेता : A person who defeats an opponent in a competition or battle.
- ***Synonyms***: Winner, champion, conqueror, vanquisher, hero
_Example_: The **victor** of the chess tournament received a grand trophy. *(Noun: person who defeats an opponent)*

=====
## **60 VIV/ VIT** = life

### CONVIVIAL
@@
**Adjective** | हिंदी: मिलनसार / उत्सवप्रिय : Friendly, lively, and enjoyable; sociable.
- ***Synonyms***: Genial, affable, sociable, jovial, cheerful, friendly
_Example_: The host created a warm and **convivial** atmosphere for the dinner party. *(Adjective)*

=====

### VITAL
@@
**Adjective** | हिंदी: अत्यावश्यक / महत्वपूर्ण; जीवंत / ऊर्जावान : Absolutely necessary or important; essential; Full of energy; lively.
- ***Synonyms***:
    - **Adjective:**
        - *Essential:* Crucial, indispensable, key, necessary, imperative, critical
        - *Lively:* Energetic, animated, spirited, dynamic, vibrant, sprightly
_Example_:
1.  Access to clean water is **vital** for the survival of the community. *(Adjective: essential)*
2.  Despite his advanced age, he remained a **vital** contributor to the team's discussions. *(Adjective: lively, energetic)*

=====

### VIVACIOUS
@@
**Adjective** | हिंदी: ज़िंदादिल / प्रफुल्ल : Attractively lively and animated (often used for women).
- ***Synonyms***: Lively, animated, spirited, bubbly, effervescent, sparkling
_Example_: Her **vivacious** personality lit up the room and charmed everyone she met. *(Adjective)*

=====

### VIVID
@@
**Adjective** | हिंदी: सुस्पष्ट / सजीव; चमकीला / गहरा : Producing powerful feelings or strong, clear images in the mind; (Of colour) intensely deep or bright.
- ***Synonyms***:
    - **Adjective:**
        - *Clear Image/Feeling:* Graphic, realistic, detailed, evocative, clear, strong
        - *Bright Colour:* Brilliant, intense, bright, radiant, rich, deep
_Example_:
1.  She gave a **vivid** description of her holiday adventures. *(Adjective: clear image/feeling)*
2.  The painter used **vivid** reds and oranges to depict the sunset. *(Adjective: bright colour)*

=====
## **61 VOC/ VOK** = call, word

### ADVOCATE
@@
**Noun** | हिंदी: समर्थक / वकील : A person who publicly supports or recommends a particular cause or policy; A person who pleads on someone else's behalf.
**Verb** | हिंदी: वकालत करना / समर्थन करना : To publicly recommend or support.
- ***Synonyms***:
    - **Noun:**
        - *Supporter:* Champion, promoter, proponent, backer, campaigner
        - *Legal Pleader:* Lawyer, counsel, barrister, solicitor
    - **Verb:**
        - *Support/Recommend:* Champion, support, back, promote, uphold, recommend
_Example_:
1. She is a strong **advocate** for environmental protection. *(Noun: supporter)*
2. He worked as a defense **advocate** for many years. *(Noun: legal pleader)*
3. They **advocate** for stricter gun control laws. *(Verb: support/recommend)*

=====

### CONVOKE
@@
**Verb** | हिंदी: बुलाना / संयोजन करना : To call together or summon (an assembly, meeting, or group).
- ***Synonyms***: Summon, convene, assemble, gather, call, muster
_Example_: The president decided to **convoke** an emergency meeting of the cabinet. *(Verb: call together or summon)*

=====

### EQUIVOCAL
@@
**Adjective** | हिंदी: अनेकार्थक / संदिग्ध : Open to more than one interpretation; ambiguous; Uncertain or questionable in nature.
- ***Synonyms***: Ambiguous, indefinite, vague, unclear, ambivalent, uncertain, dubious, questionable
_Example_: His response was **equivocal**, leaving us unsure of his true intentions. *(Adjective: ambiguous or uncertain)*

=====

### INVOKE
@@
**Verb** | हिंदी: आह्वान करना / लागू करना / उदाहरण देना : To cite or appeal to (someone or something) as an authority or for justification; To call forth or bring about (a feeling, memory, or image); To implement or put into effect (a law, penalty, or procedure).
- ***Synonyms***:
    - **Verb:**
        - *Cite/Appeal To:* Cite, refer to, adduce, instance
        - *Call Forth (Feeling/Memory):* Evoke, induce, elicit, arouse, cause
        - *Implement/Enact:* Apply, implement, execute, enact, resort to
_Example_:
1. The defendant **invoked** his right to remain silent. *(Verb: cite/appeal to)*
2. The smell of rain **invoked** memories of her childhood. *(Verb: call forth feeling/memory)*
3. The government may **invoke** emergency powers if the situation worsens. *(Verb: implement/enact)*

=====

### IRREVOCABLE
@@
**Adjective** | हिंदी: अपरिवर्तनीय / अटल : Not able to be changed, reversed, or recovered; final.
- ***Synonyms***: Irreversible, unalterable, unchangeable, final, binding, permanent
_Example_: Signing the contract made the decision **irrevocable**. *(Adjective: unable to be changed or reversed)*

=====

### PROVOKE
@@
**Verb** | हिंदी: उकसाना / भड़काना; उत्पन्न करना / कारण बनना; जगाना : To deliberately make someone annoyed or angry; To stimulate or give rise to (a reaction or emotion, typically a strong or unwelcome one) in someone; To call forth (a memory or feeling).
- ***Synonyms***:
    - **Verb:**
        - *Incite anger:* Irritate, annoy, anger, incite, exasperate, infuriate
        - *Cause reaction:* Elicit, cause, induce, generate, trigger, evoke
        - *Evoke feeling:* Arouse, stir up, call forth
_Example_:
1. His persistent teasing was designed to **provoke** his sister. *(Verb: incite anger)*
2. The article **provoked** widespread debate about the education system. *(Verb: cause reaction)*
3. The familiar melody **provoked** a wave of nostalgia. *(Verb: evoke feeling)*

=====

### REVOKE
@@
**Verb** | हिंदी: रद्द करना / वापस लेना; खंडन करना : To officially cancel (a decree, decision, or promise); To take back or withdraw.
- ***Synonyms***: Cancel, repeal, rescind, annul, nullify, invalidate, retract, withdraw, countermand, reverse.
- ***Antonyms***: Institute, enact, introduce, validate, confirm, ratify, approve, authorize.
_Example_:
1. The authorities threatened to **revoke** their license if they didn't comply with the regulations. *(Verb: officially cancel)*
2. He decided to **revoke** his earlier promise due to the changed circumstances. *(Verb: take back)*

_Word Form Examples_
1. **REVOCATION**: 🌟
   - The **revocation** of the treaty led to renewed tensions between the countries. *(Noun: the act of cancelling)*
   - ***Synonyms***: cancellation, repeal, rescission, annulment, withdrawal, invalidation
2. **REVOCABLE**:
   - The power of attorney granted was **revocable** upon written notice. *(Adjective: capable of being cancelled)*
   - ***Synonyms***: cancellable, reversible, rescindable
3. **IRREVOCABLE**: 🌟
   - Once submitted, the application becomes **irrevocable**. *(Adjective: not able to be cancelled or changed)*
   - ***Synonyms***: irreversible, unalterable, final, permanent, binding
4. **REVOKED**:
   - His driving privileges were **revoked** after multiple violations. *(Adjective/Past Participle: having been officially cancelled)*
   - ***Synonyms***: cancelled, annulled, rescinded, invalidated, withdrawn

=====

### VOCAL
@@
**Adjective** | हिंदी: स्वर-संबंधी / वाचिक; मुखर : Relating to or produced by the voice; Expressing opinions or feelings freely or loudly.
**Noun** | हिंदी: गायन भाग / बोल; गायन : The part of a piece of music that is sung (often plural 'vocals' in pop music).
- ***Synonyms***:
    - **Adjective:**
        - *Relating to voice:* Oral, spoken, voiced, uttered, phonetic
        - *Expressing opinions freely:* Outspoken, forthright, expressive, articulate, communicative, blunt, strident
    - **Noun:**
        - *Sung part/Singing:* Singing, lyrics, song line, melody line (often plural: vocals)
- ***Antonyms***:
    - **Adjective:**
        - *Relating to voice:* Written, instrumental, nonverbal
        - *Expressing opinions freely:* Silent, quiet, reticent, reserved, taciturn, subdued, suppressed
    - **Noun:**
        - *Sung part/Singing:* Instrumental
_Example_:
1. The disease affected his **vocal** cords, making speech difficult. *(Adjective: relating to voice)*
2. He was a **vocal** critic of the government's new policy. *(Adjective: expressing opinions freely)*
3. The song features a catchy melody and powerful **vocals**. *(Noun: singing, typically plural)*
4. The lead **vocal** enters after the instrumental introduction. *(Noun: sung part)*

_Word Form Examples_
1. **VOCALLY**: 🌟
   - She expressed her support **vocally** at the meeting. *(Adverb: using the voice; in an outspoken manner)*
   - ***Synonyms***: orally, verbally, outspokenly, audibly, articulately, aloud
2. **VOCALIST**: 🌟
   - The band auditioned several talented **vocalists** before making a choice. *(Noun: a singer, especially in popular music)*
   - ***Synonyms***: singer, songster, cantor, chanteuse, crooner, performer
3. **VOCALIZE**:
   - Birds **vocalize** to communicate warnings or attract mates. *(Verb: to make sounds with the voice; to sing)*
   - ***Synonyms***: utter, sound, sing, articulate, voice, enunciate, express
4. **VOCALIZATION**:
   - Complex **vocalization** is a key aspect of human language. *(Noun: the act or process of producing sounds with the voice; a sound produced)*
   - ***Synonyms***: utterance, articulation, sound, enunciation, expression, singing
5. **VOCALS**: 🌟
   - She provided backing **vocals** for the lead singer. *(Noun Plural: the singing part of a piece of popular music)*
   - ***Synonyms***: singing, lead singing, harmonies, backing vocals

=====

### VOCIFEROUS
@@
**Adjective** | हिंदी: कोलाहलपूर्ण / मुखर / प्रबल : Expressing or characterized by vehement opinions; loud and forceful.
- ***Synonyms***: Vehement, outspoken, clamorous, noisy, insistent, loud, strident
_Example_: The **vociferous** crowd demanded the resignation of the mayor. *(Adjective: loud and forceful in expressing opinions)*

=====