#root1
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

## **01 AC, ACR** = Sharp Sour, Bitter

### ACERBIC
@@
**Adjective** | हिंदी: कटु, तीखा : Sharp and forthright in tone; characterized by harsh or biting criticism or remarks.
- ***Synonyms***: Caustic, biting, sharp, sardonic, cutting, mordant
_Example_: The reviewer was known for his **acerbic** wit that spared no one in the literary world. *(Adjective: harshly critical)*

=====

### ACRID
@@
**Adjective** | हिंदी: कड़वा, तीखा : Having a sharp, bitter, and unpleasant taste or smell; can also describe harsh or bitter language.
- ***Synonyms***: Pungent, bitter, sharp, caustic, harsh, astringent
_Example_: **Acrid** smoke from the burning building stung their eyes and made breathing difficult. *(Adjective: sharply unpleasant to senses)*

=====

### ACRIMONY
@@
**Noun** | हिंदी: कटुता, तीक्ष्णता : Bitterness and ill feeling, especially in speech, arguments, or relationships.
- ***Synonyms***: Bitterness, hostility, animosity, rancor, resentment, spite
_Example_: The divorce proceedings were filled with **acrimony** as both parties refused to compromise on anything. *(Noun: bitter hostility)*

=====

### ACUMEN
@@
**Noun** | हिंदी: प्रतिभा, तीक्ष्णता : The ability to make good judgments and quick decisions, especially in a particular domain.
- ***Synonyms***: Shrewdness, astuteness, perception, discernment, insight, sharpness
_Example_: Her business **acumen** helped the struggling company turn profitable within just one year. *(Noun: sharp judgment ability)*

=====

### ACUTE
@@
**Adjective** | हिंदी: तीक्ष्ण, तीव्र, गंभीर 
1. Severe or intense, especially referring to pain, illness, or a problem.
2. Having or showing a perceptive understanding or insight.
- ***Synonyms***: 
   - For "severe": Intense, severe, extreme, critical, grave
   - For "perceptive": Sharp, keen, astute, perceptive, discerning
   - For "angle": Sharp, pointed
_Example_:
1. She was rushed to the hospital with **acute** appendicitis requiring immediate surgery. *(Adjective: severe)*
2. His **acute** observations about human nature made his novels particularly compelling. *(Adjective: perceptive)*

=====

### EXACERBATE
@@
**Verb** | हिंदी: बढ़ाना, और भी बुरा करना : To make a problem, bad situation, or negative feeling worse.
- ***Synonyms***: Aggravate, worsen, intensify, compound, heighten, inflame
_Example_: The government's poor response to the crisis only served to **exacerbate** public anxiety and distrust. *(Verb: make worse)*

=====
## **02 AM, AMI** = Love

### AMELIORATE
@@
**Verb** | हिंदी: सुधारना, बेहतर बनाना : To make something bad or unsatisfactory better.
- ***Synonyms***: Improve, better, enhance, upgrade, boost, refine
_Example_: The new policies were designed to **ameliorate** the living conditions in disadvantaged communities. *(Verb: make better)*

=====

### AMENABLE
@@
**Adjective** | हिंदी: सहमत होने वाला, आज्ञाकारी : Willing to accept or be influenced by suggestions or guidance; responsive to advice.
- ***Synonyms***: Cooperative, compliant, receptive, responsive, agreeable, tractable
_Example_: The new team member was **amenable** to feedback and quickly adapted her approach based on suggestions. *(Adjective: responsive to advice)*

=====

### AMIABLE
@@
**Adjective** | हिंदी: मिलनसार, सौहार्दपूर्ण : Having a pleasant and friendly disposition; good-natured and likeable.
- ***Synonyms***: Friendly, pleasant, genial, affable, cordial, agreeable
_Example_: Despite her fame, she maintained an **amiable** personality and was well-liked by everyone she met. *(Adjective: friendly and pleasant)*
<!--SR:!2025-07-20,20,251-->

=====

### AMITY
@@
**Noun** | हिंदी: मैत्री, मित्रता : Friendly and peaceful relations, especially between nations or groups.
- ***Synonyms***: Friendship, harmony, goodwill, cordiality, peace, accord
_Example_: After decades of conflict, the two neighboring countries finally signed a treaty of **amity** that promised lasting peace. *(Noun: peaceful relations)*

=====

### AMOROUS
@@
**Adjective** | हिंदी: प्रेमपूर्ण, कामुक : Showing, feeling, or relating to sexual desire or romantic love.
- ***Synonyms***: Romantic, passionate, loving, affectionate, lustful, ardent
_Example_: The couple exchanged **amorous** glances across the room throughout the evening party. *(Adjective: showing romantic interest)*

=====

### ENAMOR
@@
**Verb** | हिंदी: मोहित करना, आकर्षित करना : To fill someone with love, affection, or admiration; to captivate or charm.
- ***Synonyms***: Captivate, charm, enchant, fascinate, enthrall, beguile
_Example_: Her intelligence and wit quickly **enamored** him, and he found himself thinking about her constantly. *(Verb: to charm or captivate)*

=====
## **03 ANTE, ANT** = Before

### ANTECEDENT
@@
**Noun/Adjective** | हिंदी: पूर्ववर्ती 
1. A thing or event that existed before or logically precedes another.
2. (Grammar) A word, phrase, or clause that is referred to by a pronoun.
- ***Synonyms***: Predecessor, precursor, forerunner, precedent, precondition
_Example_:
1. The French Revolution was an important **antecedent** to many modern democratic movements. *(Noun: preceding event)*
2. In the sentence "When Maria finished her work, she went home," "Maria" is the **antecedent** of "she." *(Noun: grammatical reference)*

=====

### ANTEDILUVIAN
@@
**Adjective** | हिंदी: प्राचीन, जलप्लावन-पूर्व का : Extremely old, outdated, or antiquated; literally meaning "before the biblical flood."
- ***Synonyms***: Ancient, prehistoric, archaic, outdated, primitive, obsolete
_Example_: His **antediluvian** views on technology made him refuse to use even a basic smartphone. *(Adjective: extremely outdated)* *(Somewhat Rare)*

=====

### ANTICIPATE
@@
**Verb** | हिंदी: प्रत्याशा करना, पूर्वानुमान करना 
1. To expect or predict that something will happen.
2. To take action in preparation for something before it happens.
- ***Synonyms***: Expect, foresee, predict, await, prepare for, envisage
_Example_:
1. Market analysts **anticipate** a rise in interest rates following the central bank's announcement. *(Verb: predict)*
2. We didn't **anticipate** such a large turnout for the event, so we ran out of refreshments. *(Verb: expect)*

=====

### ANTIQUE
@@
**Noun/Adjective** | हिंदी: प्राचीन वस्तु, पुरातन 
1. An object having special value because of its age, especially a piece of furniture or work of art.*(Noun)*
2. Old and valuable; belonging to ancient times.*(Adjective)*
- ***Synonyms***: Vintage, collectible, heirloom, ancient, time-honored, classic
_Example_:
1. The mahogany desk is a valuable **antique** that has been in our family for generations. *(Noun: old valuable object)*
2. They specialize in restoring **antique** furniture from the Victorian era. *(Adjective: old and valuable)*

=====

### ANTIQUITY
@@
**Noun** | हिंदी: प्राचीनता, पुरातनता :The ancient past, especially the period before the Middle Ages.
- ***Synonyms***: Ancient times, classical period, ancientness, ancient history, olden days
_Example_: The archaeological site revealed artifacts of great **antiquity**, some dating back more than 3,000 years. *(Noun: ancient origin or extreme age)*

=====
## **04 ANTI** = Against, Opposite

### ANTAGONISM
@@
**Noun** | हिंदी: विरोध, शत्रुता : Active opposition or hostility between individuals, groups, or forces.
- ***Synonyms***: Hostility, opposition, enmity, animosity, conflict, friction
_Example_: The **antagonism** between the two political parties prevented any meaningful legislation from being passed. *(Noun: active opposition)*

=====

### ANTIDOTE
@@
**Noun** | हिंदी: प्रतिविष, मारक : A substance that counteracts a poison; metaphorically, something that prevents or counteracts an unwanted situation.
- ***Synonyms***: Remedy, cure, countermeasure, corrective, treatment, solution
_Example_: Activated charcoal is used as an **antidote** for many types of poisoning in emergency medicine. *(Noun: remedy for poison)*
_Example_: Regular exercise is often considered an **antidote** to the negative effects of a sedentary lifestyle. *(Noun: metaphorical remedy)*

=====

### ANTIPATHY
@@
**Noun** | हिंदी: घृणा, अरुचि : A deep-seated feeling of dislike, aversion, or repugnance.
- ***Synonyms***: Aversion, dislike, hostility, repulsion, hatred, animosity
_Example_: He has a strong **antipathy** toward seafood and refuses to eat at restaurants that specialize in it. *(Noun: strong dislike)*

=====
## **05 BEN / BON** = Good Benefit

### BENEDICT
@@
**Noun** | हिंदी: नवविवाहित पुरुष : A newly married man, especially one who was previously considered a confirmed bachelor.
- ***Synonyms***: Newlywed, groom, newly married man, husband *(Rare)*
_Example_: After years of declaring he would never marry, James became a **benedict** last spring in a small ceremony by the lake. *(Noun: newly married man)* *(Somewhat Rare)*
<!--SR:!2025-07-13,13,230-->

=====

### BENEFACTOR
@@
**Noun** | हिंदी: परोपकारी, दानदाता : A person who gives money or other help to a person or cause.
- ***Synonyms***: Donor, patron, supporter, contributor, philanthropist, sponsor
_Example_: The anonymous **benefactor** donated millions to build the new children's hospital wing. *(Noun: generous donor)*

=====

### BENEFIT
@@
**Noun, Verb** | हिंदी: लाभ, फायदा/लाभ पहुंचाना 
1. An advantage or profit gained from something.*(Noun)*/*(Verb)*
2. A payment made by the state or an insurance company to someone entitled to receive it.*(Noun)*
- ***Synonyms***: Advantage, gain, profit, help, aid, assistance
_Example_: 
1. The main **benefit** of regular exercise is improved cardiovascular health. *(Noun: advantage)*
2. The new policy will **benefit** both the company and its employees in the long run. *(Verb: be advantageous to)*

=====

### BENEVOLENCE
@@
**Noun** | हिंदी: परोपकारिता, दयालुता : The quality of being well-meaning and kind; the disposition to do good.
- ***Synonyms***: Kindness, generosity, goodwill, compassion, charity, altruism
_Example_: Her **benevolence** toward the community was demonstrated through years of volunteer work and charitable donations. *(Noun: kindness and generosity)*
<!--SR:!2025-05-10,7,251-->

=====

### BENIGN
@@
**Adjective** | हिंदी: सौम्य, अहानिकारक : 
1. Gentle and kind; not harmful or threatening.
2. (Medical) Not malignant; not likely to spread or cause death.
- ***Synonyms***: Harmless, gentle, mild, kindly, favorable, non-threatening
_Example_: 
1. The doctors were relieved to discover that the tumor was **benign** and could be safely removed. *(Adjective: not cancerous)*
2. She had a **benign** smile that immediately put nervous patients at ease. *(Adjective: gentle and kind)*

=====

### BONA FIDE
@@
**Adjective** | हिंदी: वास्तविक, असली : Genuine; real; sincere; made in good faith without deception or fraud.
- ***Synonyms***: Authentic, genuine, legitimate, real, actual, sincere
_Example_: The lawyer confirmed that the contract was a **bona fide** agreement that met all legal requirements. *(Adjective: genuine or legitimate)*

=====
## **06 CIDE** = To kill

### FRATRICIDE
@@
**Noun** | हिंदी: भ्रातृहत्या : The act of killing one's own brother or sister; can also refer to the killing of people who belong to the same community or country.
- ***Synonyms***: Brother-killing, siblicide, fraternal killing *(Rare)*
_Example_: In Shakespeare's "Hamlet," Claudius commits **fratricide** when he murders his brother, King Hamlet, to take the throne. *(Noun: killing of one's brother)*

=====

### GENOCIDE
@@
**Noun** | हिंदी: नरसंहार, जातिसंहार : The deliberate killing of a large group of people, especially those of a particular ethnic group or nation.
- ***Synonyms***: Mass murder, ethnic cleansing, mass extermination, holocaust
_Example_: The United Nations was established partly in response to the **genocide** that occurred during World War II, with the aim of preventing such atrocities in the future. *(Noun: mass killing of an ethnic group)*

=====

### HOMICIDE
@@
**Noun** | हिंदी: हत्या, नरहत्या : The killing of one person by another; also refers to the legal term for murder or manslaughter.
- ***Synonyms***: Murder, killing, slaying, manslaughter
_Example_: The detective was assigned to investigate the **homicide** that occurred in the downtown apartment complex last night. *(Noun: killing of a person)*

=====

### MATRICIDE
@@
**Noun** | हिंदी: मातृहत्या : The killing of one's mother.
- ***Synonyms***: Mother-killing, maternal murder *(Rare)*
_Example_: In Greek mythology, Orestes commits **matricide** by killing his mother Clytemnestra to avenge his father's death. *(Noun: killing of one's mother)*

=====

### PARRICIDE
@@
**Noun** | हिंदी: पितृहत्या, मातापिता की हत्या : The killing of a close relative, especially one's father, mother, or other close relative.
- ***Synonyms***: Parent-killing, family murder, kin-slaying *(Rare)*
_Example_: The ancient Roman law punished **parricide** with exceptional severity, often sentencing the perpetrator to be sewn into a sack with animals and thrown into water. *(Noun: killing of a parent or close relative)*

=====

### PATRICIDE
@@
**Noun** | हिंदी: पितृहत्या : The act of killing one's own father.
- ***Synonyms***: Father-killing, paternal murder *(Rare)*
_Example_: In Sophocles' tragedy "Oedipus Rex," the title character unknowingly commits **patricide** when he kills King Laius, who turns out to be his biological father. *(Noun: killing of one's father)*

=====

### REGICIDE
@@
**Noun** | हिंदी: राजहत्या : The killing of a king or sovereign.
- ***Synonyms***: King-killing, monarch assassination, royal murder *(Somewhat Rare)*
_Example_: The execution of King Charles I of England in 1649 was an act of **regicide** that temporarily ended the monarchy and established the Commonwealth. *(Noun: killing of a monarch)*

=====

### SORORICIDE
@@
**Noun** | हिंदी: बहन-हत्या : The act of killing one's own sister.
- ***Synonyms***: Sister-killing, sisterly murder *(Rare)*
_Example_: The ancient myth tells a tragic tale of **sororicide** driven by jealousy over a shared love interest. *(Noun: killing of one's sister)* *(Rare)*

=====

### SUICIDE
@@
**Noun** | हिंदी: आत्महत्या : The act of intentionally causing one's own death.
- ***Synonyms***: Self-destruction, taking one's life, self-murder
_Example_: The organization provides a helpline for people considering **suicide** and works to raise awareness about mental health issues. *(Noun: act of killing oneself)*

=====

### UXORICIDE
@@
**Noun** | हिंदी: पत्नी-हत्या : The murder of one's wife.
- ***Synonyms***: Wife-killing, spousal murder
_Example_: The detective suspected **uxoricide** when the husband's alibi for the night of his wife's death couldn't be verified. *(Noun: killing of one's wife)* *(Rare)*

=====
## **07 CIRE / CIRCUM** = around

### CIRCUITOUS 
@@  
**Adjective** | हिंदी: घुमावदार, टेढ़ा-मेढ़ा : Not direct or straightforward; taking a roundabout route or approach.
- ***Synonyms***: Roundabout, indirect, winding, meandering, tortuous, convoluted  
_Example_: The GPS led us on a **circuitous** route through mountain roads, adding an extra hour to our journey. *(Adjective: indirect or roundabout)*

=====

### CIRCUMNAVIGATE 
@@  
**Verb** | हिंदी: परिक्रमा करना, चारों ओर घूमना : To travel completely around something, especially to sail around the world.
- ***Synonyms***: Circle, sail around, go around, orbit, traverse, encircle  
_Example_: Ferdinand Magellan's expedition was the first to **circumnavigate** the globe, though Magellan himself died before completing the journey. *(Verb: to travel all the way around)*

=====

### CIRCUMSCRIBE 
@@
**Verb** | हिंदी: सीमित करना, घेरना  
1. To draw a line around something; to encircle.  
2. To restrict or limit something within bounds or specific parameters.  
- ***Synonyms***: Restrict, limit, confine, bound, constrain, delineate  
_Example_:  
1. The mathematician carefully **circumscribed** a circle around the triangle to demonstrate a geometric principle. *(Verb: to draw around)*  
2. His diplomatic role was **circumscribed** by strict governmental policies that limited what he could discuss in negotiations. *(Verb: to restrict or limit)*  

=====

### CIRCUMSPECT 
@@  
**Adjective** | हिंदी: सावधान, विवेकी, सतर्क : Careful to consider all circumstances and possible consequences; prudently watchful and discreet.
- ***Synonyms***: Cautious, wary, careful, guarded, prudent, vigilant  
_Example_: The experienced lawyer was **circumspect** in her responses to the media, careful not to reveal any confidential information about the high-profile case. *(Adjective: cautious and discreet)*

=====

### CIRCUMSTANCE 
@@
**Noun** | हिंदी: परिस्थिति  
1. A condition or fact that determines or affects a situation.  
2. One's state of wealth or material welfare (often used in plural form).  
- ***Synonyms***: Situation, condition, context, factor, state, position  
_Example_:  
1. Under the **circumstances** of the pandemic, the company implemented remote work policies for all employees. *(Noun: conditions or factors affecting a situation)*  
2. Despite their humble **circumstances**, the family always managed to be generous with what little they had. *(Noun: financial or material situation)*  

=====

### CIRCUMVENT
@@
**Verb** | हिंदी: बचना, दरकिनार करना : To find a way around an obstacle, especially rules, laws or regulations, often in a clever and possibly deceptive way.
- ***Synonyms***: Bypass, avoid, evade, sidestep, get around, outwit
_Example_: The company attempted to **circumvent** environmental regulations by moving their factory operations to a country with more lenient laws. *(Verb: to get around or bypass)*
<!--SR:!2025-05-14,9,251-->

=====
## **08 CLIN / CLIV** = slope, lean

### ACCLIVITY
@@
**Noun** | हिंदी: चढ़ाव : A steep upward slope or incline.
- ***Synonyms***: Upslope, ascent, rise, upgrade, hill
_Example_: The hikers struggled to climb the steep **acclivity** that led to the mountain peak. *(Noun: upward slope)*

=====

### DECLINE  
@@  
**Noun** | हिंदी: पतन, गिरावट : A gradual and continuous decrease or deterioration in quality, quantity, or importance.  
**Verb** | हिंदी: अस्वीकार करना, घटना : To refuse something offered or to decrease in strength, quality, or value.  
- ***Synonyms***:  
   - For "decrease": Reduction, downturn, fall, shrinkage, depreciation *(Formal)*  
   - For "refuse": Reject, turn down, spurn *(Formal)*, dismiss  
_Example_:  
1. The **decline** in sales over the past year has alarmed the management team. *(Noun: decrease)*  
2. He politely **declined** the invitation to the party due to prior commitments. *(Verb: refuse)*  

=====

### DECLIVITY
@@
**Noun** | हिंदी: उतार, ढलान : A downward slope or descent.
- ***Synonyms***: Descent, downslope, downgrade, drop-off, incline
_Example_: The car gained speed as it moved down the **declivity** of the mountain road. *(Noun: downward slope)* *(Rare)*
<!--SR:!2025-07-16,16,250-->

=====

### INCLINE  
@@  
**Noun** | हिंदी: ढाल, झुकाव : A slope or slanting surface; a gradual tilt or angle.  
**Verb** | हिंदी: झुकना, प्रवृत्त होना : To lean or cause to lean in a particular direction; to have a tendency or preference toward something.  
- ***Synonyms***:  
   - For "slope": Slope, gradient, incline, ramp *(Specific)*, tilt  
   - For "tendency": Lean, predispose, favor, tend  
_Example_:  
1. The hikers walked carefully up the steep **incline** of the mountain trail. *(Noun: slope)*  
2. She seemed to **incline** toward accepting the proposal after much deliberation. *(Verb: have a tendency)*  

=====

### PROCLIVITY
@@
**Noun** | हिंदी: प्रवृत्ति, झुकाव : A natural inclination or tendency toward something, especially something considered bad.
- ***Synonyms***: Tendency, inclination, predisposition, penchant, propensity, predilection
_Example_: Despite his **proclivity** for procrastination, he managed to complete the project on time. *(Noun: natural tendency)*

=====

### RECLINE
@@
**Verb** | हिंदी: लेटना, पीछे की ओर झुकना : To lean or lie back in a relaxed position.
- ***Synonyms***: Lie back, lean back, rest, lounge, stretch out
_Example_: After the long hike, she **reclined** on the sofa to rest her tired muscles. *(Verb: lean back)*

=====
## **09 CLU/CLO = close, shut

### CLOISTER  
@@  
**Noun** | हिंदी: मठ, आश्रम : A secluded place, especially a monastery or convent, where people live in seclusion for religious purposes.  
**Verb** | हिंदी: अलग करना, एकांत में रहना : To isolate or seclude someone, often for religious devotion or protection.  
- ***Synonyms***:  
   - For "secluded place": Monastery, convent, abbey, hermitage *(Rare)*, sanctuary  
   - For "isolate": Seclude, isolate, withdraw, segregate, shelter  
_Example_:  
1. The old **cloister** stood quietly on the hill, its walls echoing centuries of prayer and devotion. *(Noun: secluded place)*  
2. She decided to **cloister** herself from the outside world to focus on her spiritual growth. *(Verb: isolate)*  

=====

### CLUSTER  
@@  
**Noun** | हिंदी: गुच्छा / समूह / झुंड  : A group of similar things or people positioned or occurring closely together.  
**Verb** | हिंदी: इकट्ठा होना/ समूह बनाना : To gather or form a group of things or people in a close arrangement.  
- ***Synonyms***:  
   - For "group": Group, bunch, cluster, collection, gathering  
   - For "gather": Collect, assemble, congregate, bunch up, huddle  
_Example_:  
1. A **cluster** of stars formed a beautiful constellation visible in the night sky. *(Noun: group)*  
2. The children began to **cluster** around the teacher as she started telling a story. *(Verb: gather)*  

=====

### EXCLUDE
@@
**Verb** | हिंदी: बाहर रखना, निकाल देना : To deny someone access to or keep something out.
- ***Synonyms***: Omit, bar, ban, reject, eliminate, shut out
_Example_: The private club voted to **exclude** women from membership until 1990, a policy that was later changed due to public pressure. *(Verb: deny access)*

=====

### OCCLUDE
@@
**Verb** | हिंदी: अवरुद्ध करना, रोकना : To block or close up a passage or opening.
- ***Synonyms***: Block, obstruct, close, clog, seal, shut off
_Example_: Cholesterol deposits can **occlude** arteries and restrict blood flow to the heart. *(Verb: block)* *(Medical)*

=====

### RECLUSIVE
@@
**Adjective** | हिंदी: एकांतप्रिय, अलग-थलग रहने वाला : Avoiding the company of others; living in solitude or isolation.
- ***Synonyms***: Solitary, hermitic, withdrawn, secluded, antisocial, retiring
_Example_: The **reclusive** author hadn't granted an interview in decades, preferring to communicate with the world only through his novels. *(Adjective: avoiding social contact)*

=====

### SECLUDE
@@
**Verb** | हिंदी: अलग करना, एकांत में रखना : To keep someone or something away from social contact or public view.
- ***Synonyms***: Isolate, sequester, separate, detach, segregate, withdraw
_Example_: After the scandal, the celebrity chose to **seclude** himself in his mountain cabin until the media attention subsided. *(Verb: isolate)*

=====
## **10 CORP** = BODY

### CORPORAL  
@@  
**Noun** | हिंदी: कंपनी का सैनिक : A rank of soldier in the army, typically below sergeant and above private.  
- ***Synonyms***:  Soldier, enlisted man, non-commissioned officer
_Example_: The **corporal** led the squad with discipline and ensured orders were followed promptly. *(Noun: military rank)*  

=====

### CORPS 
@@  
**Noun** | हिंदी: कोर : A large military unit, typically consisting of two or more divisions; or a group of people engaged in a particular activity.
- ***Synonyms***: Division, unit, battalion, force, organization, body  
_Example_: The Marine **Corps** was deployed to assist with disaster relief efforts following the devastating hurricane. *(Noun: organized military body)*

=====

### CORPSE 
@@  
**Noun** | हिंदी: शव, लाश : The dead body of a human being.
- ***Synonyms***: Body, cadaver, remains, deceased, dead body  
_Example_: The forensic pathologist carefully examined the **corpse** to determine the time and cause of death. *(Noun: dead body)*

=====

### CORPULENT 
@@  
**Adjective** | हिंदी: स्थूल, मोटा : Having a large, heavy, or fat body; obese.
- ***Synonyms***: Obese, overweight, fat, portly, rotund, stout  
_Example_: The once athletic boxer had become increasingly **corpulent** in his retirement years. *(Adjective: excessively fat)*

=====
## **11 CRAC/CRAT** = rule power

### ARISTOCRAT
@@
**Noun** | हिंदी: अभिजात, कुलीन : A person who belongs to the highest social class or nobility, often having inherited titles and privileges.
- ***Synonyms***: Noble, lord, patrician, blue blood, elite, highborn
_Example_: The **aristocrat** maintained his family's ancestral estate and continued the traditions that had been passed down for generations. *(Noun: member of nobility)*

=====

### AUTOCRAT
@@
**Noun** | हिंदी: निरंकुश शासक, स्वेच्छाचारी : A ruler who has absolute power and authority, typically exercising it in an oppressive manner.
- ***Synonyms***: Dictator, despot, tyrant, absolute ruler, totalitarian
_Example_: The **autocrat** silenced all opposition and ruled the country with an iron fist for over three decades. *(Noun: absolute ruler)*

=====

### DEMOCRAT
@@
**Noun** | हिंदी: लोकतंत्रवादी, प्रजातंत्रवादी : A person who believes in and supports democracy.
- ***Synonyms***: Supporter of democracy, egalitarian, republican
_Example_: As a committed **democrat**, she fought tirelessly for free elections and equal rights for all citizens. *(Noun: supporter of democracy)*
<!--SR:!2025-05-12,9,251-->

=====

### PLUTOCRAT
@@
**Noun** | हिंदी: धनतंत्री, धनपति : A person who derives power and influence from their wealth.
- ***Synonyms***: Tycoon, magnate, mogul, oligarch, wealthy elite
_Example_: The **plutocrat** donated millions to political campaigns, ensuring his business interests were protected by favorable legislation. *(Noun: wealthy influential person)*

=====

### THEOCRACY
@@
**Noun** | हिंदी: धर्मतंत्र, धर्मराज्य : A system of government in which priests rule in the name of God or a deity.
- ***Synonyms***: Religious state, divine rule, ecclesiastical government, hierocracy
_Example_: In the **theocracy**, all laws and social norms were derived from religious texts and enforced by clerical authorities. *(Noun: religious government)*

=====
## **12 CRED** = belief, trust

### CREDENCE
@@
**Noun** | हिंदी: विश्वास, प्रामाणिकता : Belief in or acceptance of something as true; trust or confidence.
- ***Synonyms***: Belief, faith, trust, acceptance, confidence
_Example_: Scientists are reluctant to give **credence** to claims that lack substantial evidence or peer review. *(Noun: belief or acceptance)*

=====

### CREDENTIALS
@@
**Noun (plural)** | हिंदी: प्रमाणपत्र, योग्यता : Documents or qualifications that prove someone's identity, abilities, or authorization.
- ***Synonyms***: Qualifications, documents, proof, certification, ID
_Example_: The hiring manager was impressed by her **credentials**, which included a master's degree and five years of relevant experience. *(Noun: qualifications)*

=====

### CREDIT
@@
**Noun** | हिंदी: श्रेय / मान्यता; उधार / साख; जमा; क्रेडिट : Public approval or praise, often for an achievement; The ability to obtain goods or services before payment, based on trust; An entry recording a sum received in an account; A unit of study counting towards a degree.
**Verb** | हिंदी: श्रेय देना; विश्वास करना / मानना; जमा करना : Publicly acknowledge someone's contribution; Believe something surprising or unlikely; Add an amount of money to an account.
- ***Synonyms***:
    - **Noun:**
        - *Approval/Praise:* Praise, commendation, acclaim, kudos, recognition, acknowledgement, glory, honour
        - *Trust for Payment:* Loan, advance, trust, financial standing
        - *Accounting Entry:* Asset, payment received
        - *Academic Unit:* Unit, point, module
    - **Verb:**
        - *Acknowledge Contribution:* Acknowledge, recognize, accredit, attribute, ascribe
        - *Believe:* Believe, trust, accept, swallow, buy *(informal)*
        - *Add Money to Account:* Deposit, post, add to, put into
- ***Antonyms***:
    - **Noun:**
        - *Approval/Praise:* Blame, discredit, dishonour, censure, condemnation
        - *Trust for Payment:* Debit, debt, distrust, cash
        - *Accounting Entry:* Debit, withdrawal, charge, liability
    - **Verb:**
        - *Acknowledge Contribution:* Discredit, blame, deny, censure
        - *Believe:* Disbelieve, doubt, distrust, question, reject
        - *Add Money to Account:* Debit, withdraw, deduct, charge
_Example_:
1.  She deserves full **credit** for the team's success. *(Noun: approval/praise)*
2.  We bought the furniture on **credit**. *(Noun: trust for payment)*
3.  The refund appeared as a **credit** on my statement. *(Noun: accounting entry)*
4.  You need 120 **credits** to earn the degree. *(Noun: academic unit)*
5.  The report **credits** Dr. Lee with the initial discovery. *(Verb: acknowledge contribution)*
6.  I can scarcely **credit** that he would do such a thing. *(Verb: believe)*
7.  The bank will **credit** your account with the interest earned. *(Verb: add money to account)*

=====

### CREDULOUS
@@
**Adjective** | हिंदी: आसानी से विश्वास करने वाला, भोला : Tending to believe things too easily, especially things that are somewhat dubious or unlikely.
- ***Synonyms***: Gullible, naive, trusting, unsuspecting, innocent
_Example_: The scammer targeted **credulous** elderly people who readily believed his promises of enormous investment returns. *(Adjective: overly trusting)*
<!--SR:!2025-07-05,5,210-->

=====

### CREED
@@
**Noun** | हिंदी: धर्म-सिद्धांत, विश्वास : A formal statement of religious belief; a set of beliefs or principles.
- ***Synonyms***: Beliefs, doctrine, ideology, principles, faith, dogma
_Example_: Regardless of race, color, or **creed**, all citizens are entitled to equal protection under the law. *(Noun: set of beliefs)*

=====
## **13 DOC/DOCT** = teach

### DOCILE
@@
**Adjective** | हिंदी: आज्ञाकारी, विनम्र : Ready to accept control or instruction; submissive and easily managed.
- ***Synonyms***: Obedient, compliant, submissive, tractable, amenable, tame
_Example_: The normally energetic puppy became surprisingly **docile** after the long walk in the park. *(Adjective: submissive or manageable)*

=====

### DOCTRINE
@@
**Noun** | हिंदी: सिद्धांत, मतवाद : A belief or set of beliefs held and taught by a religious, political, or other group.
- ***Synonyms***: Principle, belief, dogma, tenet, precept, creed
_Example_: The Monroe **doctrine**, which opposed European colonization in the Americas, shaped U.S. foreign policy for generations. *(Noun: established principle)*

=====

### DOCUMENT
@@
**Noun, Verb** | हिंदी: दस्तावेज़, प्रलेखित करना
1. A piece of written, printed, or electronic matter that provides information or evidence.*(Noun)*
2. To record or prove with documents or evidence.*(Verb)*
- ***Synonyms***:
   - For "written matter": Record, file, paper, certificate, form
   - For "record": Record, chronicle, register, log, archive
_Example_:
1. The lawyer requested all **documents** related to the property transaction. *(Noun: written record)*
2. The photographer spent years **documenting** the effects of climate change on coastal communities. *(Verb: recording)*

=====

### INDOCTRINATE
@@
**Verb** | हिंदी: विचारधारा से प्रभावित करना, मतानुयायी बनाना : To teach a person or group to accept a set of beliefs uncritically.
- ***Synonyms***: Brainwash, condition, instill, inculcate, propagandize
_Example_: The authoritarian regime attempted to **indoctrinate** the youth through controlled education and propaganda. *(Verb: impose beliefs)*

=====
## **14 DUC/DUCT** = lead

### AQUEDUCT
@@
**Noun** | हिंदी: जलसेतु, पानी की नहर : A bridge-like structure built to carry water over gaps, such as valleys or rivers.
- ***Synonyms***: Water bridge, water channel, conduit, waterway
_Example_: The ancient Roman **aqueduct** still stands today, a testament to the engineering prowess of that civilization. *(Noun: water-carrying structure)*
<!--SR:!2025-07-10,10,230-->

=====

### CONDUCT
@@
**Noun, Verb** | हिंदी: आचरण, संचालन करना
1. The manner in which a person behaves.*(Noun)*
2. To direct or lead something such as an orchestra, meeting, or investigation.*(Verb)*
- ***Synonyms***:
   - For "behavior": Behavior, demeanor, deportment, manner
   - For "direct": Lead, manage, direct, oversee, guide
_Example_:
1. His professional **conduct** during the crisis earned him the respect of his colleagues. *(Noun: behavior)*
2. The professor will **conduct** research on climate change over the summer. *(Verb: direct/lead)*
<!--SR:!2025-05-08,5,230-->

=====

### DEDUCT
@@
**Verb** | हिंदी: काटना, घटाना : To subtract or take away an amount from a total.
- ***Synonyms***: Subtract, remove, take away, withhold, discount
_Example_: The company will **deduct** the cost of health insurance from your monthly salary. *(Verb: subtract)*

=====

### DUCTILE
@@
**Adjective** | हिंदी: तन्य, लचीला : 
1. (Of metal or other materials) Able to be drawn out into a thin wire without breaking.
2. (Figurative) Easily influenced or shaped; pliable.
- ***Synonyms***: Malleable, flexible, pliable, elastic, workable
_Example_: 
1. Gold is highly **ductile**, allowing it to be drawn into extremely thin wires for use in electronics. *(Adjective: able to be stretched)*
2. His **ductile** nature made him an easy target for peer pressure. _(Adjective: figurative flexibility)_

=====

### INDUCE
@@
**Verb** | हिंदी: प्रेरित करना, उत्पन्न करना : 
1. To persuade or influence someone to do something.
2. To bring about or cause a condition.
- ***Synonyms***: Cause, bring about, prompt, trigger, stimulate, lead to
_Example_: 
1. No amount of money could **induce** him to betray his principles. *(Verb: persuade)*
2. Certain medications can **induce** drowsiness as a side effect. *(Verb: cause)*

=====

### INDUCT
@@
**Verb** | हिंदी: शामिल करना, प्रवेश कराना : To formally introduce or admit someone to an organization, office, or position.
- ***Synonyms***: Install, initiate, introduce, admit, enroll
_Example_: The university will **induct** the new professors at a ceremony next month. *(Verb: formally admit)*

=====

### REDUCE
@@
**Verb** | हिंदी: कम करना, घटाना : To make smaller or less in amount, degree, or size.
- ***Synonyms***: Decrease, diminish, lessen, lower, minimize, shrink
_Example_: The new policy helped **reduce** carbon emissions by 30% over five years. *(Verb: make smaller)*

=====

### SEDUCE
@@
**Verb** | हिंदी: बहकाना, लुभाना : To attract or tempt someone into doing something, especially something wrong or unwise.
- ***Synonyms***: Entice, tempt, lure, allure, beguile, charm
_Example_: The marketing campaign was designed to **seduce** consumers into buying the luxury product despite its high price. *(Verb: tempt or attract)*

=====

### VIADUCT
@@
**Noun** | हिंदी: सड़क-सेतु, पुल : A long bridge-like structure, typically a series of arches, carrying a road or railway across a valley or other low ground.
- ***Synonyms***: Bridge, overpass, flyover, elevated roadway
_Example_: The railway **viaduct** spans the entire valley, allowing trains to cross without navigating the steep terrain below. *(Noun: bridge-like structure)*
<!--SR:!2025-04-17,9,250-->

=====
## **15 FRAG/FRACT** = break, shatter

### FRACAS
@@
**Noun** | हिंदी: झगड़ा, कोलाहल : A noisy, disruptive disturbance or quarrel; a loud argument or physical altercation.
- ***Synonyms***: Brawl, disturbance, uproar, commotion, scuffle, melee
_Example_: A minor disagreement at the bar escalated into a full-blown **fracas** that required police intervention. *(Noun: noisy fight)*

=====

### FRACTIOUS
@@
**Adjective** | हिंदी: चिड़चिड़ा, अनियंत्रित : Irritable, unruly, or difficult to control; tending to cause trouble.
- ***Synonyms***: Irritable, cranky, peevish, quarrelsome, unruly, rebellious
_Example_: The long flight delay made the passengers increasingly **fractious**, with some demanding to speak to airline representatives. *(Adjective: irritable and difficult)*

=====

### FRACTURE
@@
**Noun, Verb** | हिंदी: टूट, दरार, टूटना
1. A break or crack in a hard object or material.*(Noun)*
2. To cause to break or to become broken.*(Verb)*
- ***Synonyms***: Break, crack, rupture, split, shatter, snap
_Example_:
1. The fall resulted in a hairline **fracture** of his wrist that required six weeks to heal. *(Noun: break)*
2. The extreme pressure caused the pipe to **fracture** at its weakest point. *(Verb: break)*

=====

### FRAGILE
@@
**Adjective** | हिंदी: नाज़ुक, भंगुर : Easily broken, damaged, or destroyed; delicate and vulnerable.
- ***Synonyms***: Breakable, delicate, brittle, frail, weak, vulnerable
_Example_: The ancient manuscript was so **fragile** that researchers had to wear gloves when handling it. *(Adjective: easily damaged)*

=====

### FRAGMENT
@@
**Noun, Verb** | हिंदी: टुकड़ा, विखंडित होना
1. A small piece or part broken off from something.*(Noun)*
2. To break or cause to break into fragments.*(Verb)*
- ***Synonyms***: Piece, bit, portion, section, shard, remnant
_Example_:
1. Archaeologists found **fragments** of ancient pottery scattered throughout the excavation site. *(Noun: broken piece)*
2. The mirror **fragmented** into dozens of pieces when it fell to the floor. *(Verb: break into pieces)*

=====
## **16 GEN** = birth, class , kin

### CONGENITAL
@@
**Adjective** | हिंदी: जन्मजात : Present from birth, typically referring to a disease or physical abnormality that develops during fetal development.
- ***Synonyms***: Inborn, innate, inherited, hereditary, inherent
_Example_: The infant was diagnosed with a **congenital** heart defect that would require surgery within the first year of life. *(Adjective: present from birth)*

=====

### ENGENDER
@@
**Verb** | हिंदी: उत्पन्न करना, पैदा करना : To cause or give rise to a feeling, situation, or condition.
- ***Synonyms***: Cause, produce, generate, create, provoke, bring about
_Example_: The principal's inclusive leadership style helped **engender** a sense of community and belonging among students and faculty alike. *(Verb: bring about)*

=====

### GENEALOGY
@@
**Noun** | हिंदी: वंशावली, कुलवृत्तांत : The study of family history and lineage; the tracing of lines of descent.
- ***Synonyms***: Ancestry, lineage, family history, heritage, descent, pedigree
_Example_: After discovering an old family Bible with handwritten records, she became fascinated with **genealogy** and traced her ancestors back six generations. *(Noun: family lineage study)*

=====

### GENESIS
@@
**Noun** | हिंदी: उत्पत्ति, आरंभ : The origin or beginning of something.
- ***Synonyms***: Origin, beginning, source, root, inception, creation
_Example_: The **genesis** of the internet can be traced back to ARPANET, a computer network developed in the late 1960s. *(Noun: origin)*

=====

### GENETICS
@@
**Noun** | हिंदी: आनुवंशिकी, जीन विज्ञान : The study of heredity and the variation of inherited characteristics.
- ***Synonyms***: Heredity, inheritance, genomics, hereditability
_Example_: Modern **genetics** has revolutionized our understanding of diseases and opened new possibilities for personalized medicine. *(Noun: study of inherited traits)*

=====

### GENRE
@@
**Noun** | हिंदी: शैली, विधा : A category of artistic composition characterized by similarities in form, style, or subject matter.
- ***Synonyms***: Category, style, class, type, classification, form
_Example_: The film blends elements of horror and comedy, creating a hybrid **genre** that appeals to diverse audiences. *(Noun: category of art)*

=====

### GENTILITY
@@
**Noun** | हिंदी: सभ्यता, शिष्टता : Social refinement and good breeding; polite or refined behavior typical of the upper class.
- ***Synonyms***: Refinement, cultivation, elegance, politeness, sophistication, class
_Example_: Despite their modest circumstances, the family maintained an air of **gentility** in their manners and home. *(Noun: refined behavior)*
<!--SR:!2025-07-13,13,230-->

=====

### GENUINE
@@
**Adjective** | हिंदी: असली, वास्तविक : Truly what something is said to be; authentic and not counterfeit.
- ***Synonyms***: Authentic, real, true, legitimate, sincere, bona fide
_Example_: Her **genuine** concern for others made her a beloved figure in the community. *(Adjective: sincere or authentic)*

=====

### HETEROGENEOUS
@@
**Adjective** | हिंदी: विजातीय, विषम : Diverse in character or content; composed of dissimilar elements or parts.
- ***Synonyms***: Diverse, varied, mixed, assorted, disparate, dissimilar
_Example_: The city's **heterogeneous** population represents cultures from around the world. *(Adjective: diverse in composition)*

=====

### HOMOGENEOUS
@@
**Adjective** | हिंदी: समजातीय, सम : Of the same kind; consisting of similar elements or parts.
- ***Synonyms***: Uniform, same, consistent, identical, unvaried, similar
_Example_: Unlike diverse urban areas, the rural community remained largely **homogeneous** in its cultural makeup. *(Adjective: uniform in composition)*

=====

### INGENIOUS
@@
**Adjective** | हिंदी: चतुर, प्रतिभाशाली : Showing great cleverness and originality; resourceful and inventive.
- ***Synonyms***: Clever, creative, inventive, innovative, resourceful, brilliant
_Example_: Her **ingenious** solution to the complex problem impressed even the most experienced engineers. *(Adjective: cleverly inventive)*

=====

### PROGENY
@@
**Noun** | हिंदी: संतान, वंश : A person's children or descendants; offspring.
- ***Synonyms***: Offspring, descendants, children, heirs, successors, scions
_Example_: The aging monarch was concerned about his legacy and how his **progeny** would rule the kingdom after his death. *(Noun: offspring or descendants)*

=====
## **17 GRAD/ GRESS** = degree, step,

### CONGRESS
@@
**Noun** | हिंदी: कांग्रेस; संसद : A national legislative assembly; A formal meeting or gathering of representatives.
- ***Synonyms***:
    - **Noun:**
        - *Legislative body:* Parliament, legislature, assembly, senate
        - *Formal meeting:* Convention, conference, assembly, gathering
_Example_:
1. The bill must be approved by both houses of **Congress** before it can become law. *(Noun: legislative body)*
2. Scientists from around the world attended the international **congress** on climate change. *(Noun: formal meeting)*

=====

### DEGRADE
@@
**Verb** | हिंदी: अपमानित करना; गिराना; क्षय करना : To lower in status, character, or quality; To break down or deteriorate chemically or physically.
- ***Synonyms***:
    - **Verb:**
        - *Lower in status:* Demean, humiliate, disparage, belittle, dishonor
        - *Deteriorate:* Deteriorate, decay, break down, decompose, erode
_Example_:
1. It is unprofessional to **degrade** colleagues in front of others. *(Verb: humiliate or lower in status)*
2. These plastics will **degrade** naturally in the environment over several decades. *(Verb: break down physically)*
<!--SR:!2025-05-09,4,230-->

=====

### DIGRESS
@@
**Verb** | हिंदी: विषयांतर करना : To depart from the main subject in speech or writing; to wander off-topic.
- ***Synonyms***: Deviate, stray, wander, depart, drift, diverge
_Example_: I don't mean to **digress**, but your comment reminds me of an interesting historical parallel. *(Verb: depart from main topic)*

=====

### EGRESS
@@
**Noun** | हिंदी: निकास : A way out or exit; the act of leaving a place.
**Verb** | हिंदी: बाहर निकलना : To go out or leave a place; to exit.
- ***Synonyms***:
    - **Noun:**
        - *Way out:* Exit, outlet, way out, passage
    - **Verb:**
        - *Act of leaving:* Exit, leave, depart, emerge
_Example_:
1. The building code requires at least two points of **egress** from every floor. *(Noun: exit)*
2. Spectators began to **egress** from the stadium after the final whistle. *(Verb: leave or exit)*

=====

### GRADATION
@@
**Noun** | हिंदी: क्रमिक परिवर्तन; श्रेणीकरण : A series of successive stages or degrees; a gradual transition from one shade, tone, or condition to another.
- ***Synonyms***: Progression, sequence, spectrum, scale, transition, hierarchy
_Example_: The sunset displayed a beautiful **gradation** of colors from deep orange to pale pink. *(Noun: gradual transition between stages)*

=====

### GRADIENT
@@
**Noun** | हिंदी: ढलान; प्रवणता : The degree of slope or incline; the rate of change of a variable with respect to another variable.
**Adjective** | हिंदी: क्रमिक परिवर्तित : Changing by slight degrees; having a gradual slope.
- ***Synonyms***:
    - **Noun:**
        - *Slope:* Incline, grade, pitch, slope, declivity
        - *Rate of change:* Differential, rate of increase/decrease
    - **Adjective:**
        - *Gradually changing:* Graded, graduated, incremental, progressive
_Example_:
1. Cyclists struggled with the steep **gradient** of the mountain road. *(Noun: degree of slope)*
2. In mathematics, the **gradient** vector points in the direction of the steepest ascent. *(Noun: rate of change)*

=====

### GRADUAL
@@
**Adjective** | हिंदी: क्रमिक; धीरे-धीरे होने वाला : Taking place or occurring by degrees; moving, changing, or developing slowly.
- ***Synonyms***: Slow, incremental, progressive, steady, step-by-step, measured
_Example_: There has been a **gradual** improvement in her condition since she started the new treatment. *(Adjective: occurring slowly over time)*
<!--SR:!2025-07-09,9,230-->

=====

### GRADUATE
@@
**Verb** | हिंदी: स्नातक होना; विभाजित करना : To successfully complete an academic degree; to change gradually or by degrees.
**Noun** | हिंदी: स्नातक : A person who has successfully completed a course of study or training, especially a degree at a university.
- ***Synonyms***:
    - **Verb:**
        - *Complete education:* Qualify, certify, pass, complete
        - *Change gradually:* Progress, advance, evolve, transition
    - **Noun:**
        - *Degree holder:* Alumnus, alumna, diplomate
_Example_:
1. She will **graduate** from medical school next spring. *(Verb: complete an academic program)*
2. As a recent **graduate**, he's eager to apply his knowledge in the workplace. *(Noun: person who completed a degree)*

=====

### INGRESS
@@
**Noun** | हिंदी: प्रवेश : An entrance or the act of entering; a way to enter a place.
**Verb** | हिंदी: प्रवेश करना : To enter or go into a place. *(Rare)*
- ***Synonyms***:
    - **Noun:**
        - *Entrance:* Entry, access, admission, way in
    - **Verb:**
        - *Enter:* Access, enter, penetrate
_Example_:
1. The **ingress** of water through the damaged roof caused significant damage to the ceiling. *(Noun: entry or entrance)*
2. Security guards monitored both **ingress** and egress points around the facility. *(Noun: entrance point)*

=====

### PROGRESS
@@
**Noun** | हिंदी: प्रगति; विकास : Forward movement toward a destination; development toward an improved or more advanced condition.
**Verb** | हिंदी: प्रगति करना; आगे बढ़ना : To move forward or onward; to develop to a higher, better, or more advanced stage.
- ***Synonyms***:
    - **Noun:**
        - *Development:* Advancement, improvement, growth, development, headway
        - *Forward movement:* Progression, advance, headway, march
    - **Verb:**
        - *Move forward:* Advance, proceed, develop, improve, evolve
_Example_:
1. The team has made significant **progress** on the project over the past month. *(Noun: advancement or improvement)*
2. The negotiations **progress** slowly but steadily toward a resolution. *(Verb: move forward or develop)*

=====

### REGRESS
@@
**Verb** | हिंदी: पीछे हटना; पतन होना : To return to a previous, typically worse state; To move backward.
**Noun** | हिंदी: पीछे हटाव : The act of returning to a previous, often less developed state.
- ***Synonyms***:
    - **Verb:**
        - *Return to earlier state:* Revert, backslide, relapse, deteriorate, retrogress
        - *Move backward:* Retreat, recede, withdraw
    - **Noun:**
        - *Backward movement:* Regression, reversal, backsliding, retrogression
_Example_:
1. Without consistent practice, students tend to **regress** in their language skills during long breaks. *(Verb: return to earlier state)*
2. The **regress** to more primitive technology was necessary after the power grid failed. *(Noun: backward movement)*

=====

### TRANSGRESS
@@
**Verb** | हिंदी: उल्लंघन करना; अपराध करना : To violate a law, command, or moral code; to go beyond limits or boundaries.
- ***Synonyms***: Violate, infringe, breach, contravene, offend, trespass
_Example_: Those who **transgress** the rules will face disciplinary action. *(Verb: violate or break a rule)*

=====
## **18 GREG** = herd, mob, crowd, flock

### AGGREGATE
@@
**Noun** | हिंदी: कुल योग / सकल / समष्टि : A whole formed by combining several separate elements; a total sum.
**Verb** | हिंदी: जमा करना / इकट्ठा करना; जोड़ना : To form or group into a class or cluster; To amount to a particular total.
**Adjective** | हिंदी: कुल / सकल : Formed or calculated by the combination of many separate units or items; total.
- ***Synonyms***:
    - **Noun:**
        - *Total Sum:* Total, sum, whole, entirety, gross, amount.
        - *Collection/Mass:* Collection, mass, cluster, assemblage, combination.
    - **Verb:**
        - *Combine/Gather:* Combine, collect, gather, amass, accumulate, bring together, assemble.
        - *Total:* Amount to, total, sum up to.
    - **Adjective:**
        - *Total/Combined:* Total, combined, collective, cumulative, gross.
_Example_:
1. The final report presents the **aggregate** of the survey responses. *(Noun: total sum)*
2. Concrete is an **aggregate** of cement, sand, and gravel. *(Noun: collection/mass)*
3. The system **aggregates** data from multiple websites. *(Verb: combine/gather)*
4. The small payments **aggregate** to a substantial sum over time. *(Verb: total)*
5. The **aggregate** score determines the winner. *(Adjective: total/combined)*

=====

### CONGREGATE
@@
**Verb** | हिंदी: एकत्र होना, जमा होना : To gather or come together in a group, assembly, or crowd.
- ***Synonyms***: Gather, assemble, collect, convene, flock together
_Example_: Students tend to **congregate** in the cafeteria during lunch breaks to socialize. *(Verb)*

=====

### EGREGIOUS
@@
**Adjective** | हिंदी: अत्यंत बुरा, भयंकर : Outstandingly bad; shocking or flagrant.
- ***Synonyms***: Outrageous, appalling, shocking, flagrant, atrocious
_Example_: The politician's **egregious** misconduct led to immediate calls for his resignation. *(Adjective)*

=====

### GREGARIOUS
@@
**Adjective** | हिंदी: मिलनसार, सामाजिक : Fond of company; sociable, enjoying being in groups or crowds.
- ***Synonyms***: Sociable, outgoing, social, extroverted, friendly
_Example_: Her **gregarious** nature made her the life of every party she attended. *(Adjective)*

=====

### SEGREGATE
@@
**Verb** | हिंदी: अलग करना, पृथक करना : To separate or isolate one group from others, especially on the basis of race, class, or gender.
- ***Synonyms***: Separate, isolate, divide, partition, seclude
_Example_: Laws were passed to stop practices that **segregate** students by race in the public school system. *(Verb)*

=====
## **19 JEC, JET** = to throw, lie

### ABJECT
@@
**Adjective** | हिंदी: दयनीय, निकृष्ट : Extremely wretched, degraded, or contemptible; utterly hopeless.
- ***Synonyms***: Miserable, wretched, degraded, despicable, pitiful, contemptible
_Example_: The refugees were living in **abject** poverty, without access to clean water or adequate shelter. *(Adjective)*

=====

### CONJECTURE
@@
**Noun** | हिंदी: अनुमान / अटकल : An opinion or conclusion formed on the basis of incomplete information; a guess.
**Verb** | हिंदी: अनुमान लगाना / अटकल लगाना : To form an opinion or supposition about something on the basis of incomplete information; to guess.
- ***Synonyms***:
    - **Noun:**
        - *Guess/Supposition:* Guess, speculation, supposition, theory, hypothesis, assumption, surmise, notion, postulation.
    - **Verb:**
        - *Guess/Surmise:* Guess, speculate, suppose, theorize, hypothesize, assume, surmise, infer, postulate.
_Example_:
1.  His theory about the market crash was pure **conjecture**, lacking any solid evidence. *(Noun: guess/supposition)*
2.  We can only **conjecture** about the reasons for her sudden departure. *(Verb: guess/surmise)*

=====

### DEJECT
@@
**Verb** | हिंदी: निराश करना, हतोत्साहित करना : To make sad or dispirited; to cause someone to lose hope or enthusiasm.
- ***Synonyms***: Dishearten, discourage, dispirit, depress, sadden *(Rare)*
_Example_: The continuous rejections **dejected** him to the point where he nearly abandoned his dream. *(Verb)*

=====

### EJECT
@@
**Verb** | हिंदी: बाहर निकालना, निष्कासित करना : To force or throw someone or something out.
- ***Synonyms***: Expel, throw out, remove, oust, discharge
_Example_: The pilot had to **eject** from the aircraft when it developed a critical mechanical failure. *(Verb)*

=====

### INJECT
@@
**Verb** | हिंदी: इंजेक्शन लगाना / सुई लगाना; डालना / शामिल करना : To introduce a liquid (especially a drug or vaccine) into the body with a syringe; To introduce (a new or different element) into something.
- ***Synonyms***:
    - **Verb:**
        - *Administer Medically:* Vaccinate, inoculate, administer, shoot up (informal), jab (informal).
        - *Introduce/Instill:* Introduce, instill, infuse, insert, bring in, add, imbue, introduce.
_Example_:
1.  The nurse prepared to **inject** the patient with the prescribed medication. *(Verb: administer medically)*
2.  The team leader tried to **inject** some enthusiasm into the flagging project. *(Verb: introduce/instill)*
3.  Hackers attempted to **inject** malicious code into the website's database. *(Verb: introduce/instill)*

=====

### JETTISON
@@
**Verb** | हिंदी: फेंक देना / गिरा देना; त्याग देना / छोड़ देना : To throw or drop (something) from an aircraft or ship; To abandon or discard (someone or something) that is no longer wanted.
- ***Synonyms***:
    - **Verb:**
        - *Throw Overboard/Eject:* Discard, dump, drop, unload, eject, discharge.
        - *Abandon/Discard:* Discard, abandon, scrap, ditch, dump, get rid of, dispose of, shed.
_Example_:
1. To save the sinking ship, the captain ordered the crew to **jettison** non-essential cargo. *(Verb: throw overboard/eject)*
2. The company decided to **jettison** its outdated software system. *(Verb: abandon/discard)*

=====

### OBJECT
@@
**Noun** | हिंदी: वस्तु / चीज़; लक्ष्य / उद्देश्य; कर्म (व्याकरण); उद्देश्य / लक्ष्य / प्रयोजन : A material thing that can be seen and touched; A person or thing to which a specified action or feeling is directed; (Grammar) A noun or noun phrase governed by a preposition or transitive verb; The goal or purpose.
**Verb** | हिंदी: आपत्ति करना / विरोध करना : To say something to express one's disapproval of or disagreement with something.
- ***Synonyms***:
    - **Noun:**
        - *Thing:* Item, article, entity, body, artifact, commodity.
        - *Target/Focus:* Target, focus, recipient, butt, subject.
        - *Goal/Purpose:* Aim, goal, purpose, objective, intention, end, point.
        - *Grammar Term:* Complement (in some contexts).
    - **Verb:**
        - *Protest/Disagree:* Protest, oppose, disagree, demur, remonstrate, take exception, complain, dispute, challenge.
_Example_:
1. The detectives examined the strange **object** found at the crime scene. *(Noun: thing)*
2. He became the **object** of widespread criticism after his remarks. *(Noun: target/focus)*
3. The primary **object** of the research is to find a cure. *(Noun: goal/purpose)*
4. In "I see the cat", "the cat" is the direct **object**. *(Noun: grammar term)*
5. Many citizens strongly **object** to the new tax increase. *(Verb: protest/disagree)*

=====

### PROJECTILE
@@
**Noun** | हिंदी: प्रक्षेप्य : An object propelled through the air, especially one thrown as a weapon.
- ***Synonyms***: Missile, bullet, shell, rocket, shot
_Example_: The scientists studied the **projectile's** arc to better understand ballistic physics. *(Noun)*

=====

### REJECT
@@
**Verb** | हिंदी: अस्वीकार करना / ठुकराना / ख़ारिज करना; नामंज़ूर करना; तिरस्कार करना : To dismiss as inadequate, unacceptable, or faulty; Refuse to agree to (a request); Show aversion or lack of affection for (someone).
**Noun** | हिंदी: अस्वीकृत व्यक्ति / अस्वीकृत वस्तु : A person or thing dismissed as inadequate or unacceptable.
- ***Synonyms***:
    - **Verb:**
        - *Dismiss/Refuse:* Refuse, decline, turn down, deny, dismiss, repudiate, spurn, discard, veto, rebuff.
        - *Refuse Agreement:* Decline, deny, turn down, refuse.
        - *Show Aversion:* Spurn, rebuff, shun, snub, repel, cast aside, jilt.
    - **Noun:**
        - *Discarded Item/Person:* Discard, cast-off, failure, second, castaway, pariah.
_Example_:
1. The publisher decided to **reject** the author's latest manuscript. *(Verb: dismiss/refuse)*
2. The committee **rejected** the proposal for budget cuts. *(Verb: refuse agreement)*
3. He felt deeply hurt when she seemed to **reject** his friendship. *(Verb: show aversion)*
4. Items with minor flaws are sold as factory **rejects**. *(Noun: discarded item/person)*

=====

### TRAJECTORY
@@
**Noun** | हिंदी: प्रक्षेप-पथ : The path followed by a projectile flying or an object moving under the action of given forces.
- ***Synonyms***: Path, course, route, flight path, arc
_Example_: The physicist calculated the **trajectory** of the rocket to ensure it would reach orbit safely. *(Noun)*

=====
## **20 JUD** = judge

### ADJUDICATE
@@
**Verb** | हिंदी: न्याय करना/निर्णय देना : To make an official decision in a legal matter or dispute; To act as a judge to settle a dispute.
- ***Synonyms***: Arbitrate, judge, rule on, determine, decide, settle
_Example_: The tribunal will **adjudicate** the competing claims to the disputed property. *(Verb: make an official judgment)*

=====

### JUDGE
@@
**Noun** | हिंदी: न्यायाधीश; निर्णायक : A public official with authority to hear cases in a court of law; A person who decides the result of a competition.
**Verb** | हिंदी: निर्णय करना; आकलन करना : To form an opinion or evaluation; To act as a judge in a court or competition.
- ***Synonyms***:
    - **Noun:**
        - *Legal official:* Justice, magistrate, adjudicator, jurist
        - *Competition evaluator:* Referee, umpire, adjudicator, evaluator
    - **Verb:**
        - *Form opinion:* Evaluate, assess, appraise, determine
        - *Preside legally:* Adjudicate, preside over, hear, try
_Example_:
1. The **judge** sentenced the defendant to five years in prison. *(Noun: court official)*
2. It's unfair to **judge** someone based on first impressions. *(Verb: form an opinion)*

=====

### JUDICIAL
@@
**Adjective** | हिंदी: न्यायिक : Relating to courts of law or to the administration of justice; Having the authority to judge or make legal decisions.
- ***Synonyms***: Legal, juridical, judiciary, court, forensic, juristic
_Example_: The **judicial** review found the legislation to be unconstitutional. *(Adjective: relating to courts or judgment)*

=====

### JUDICIOUS
@@
**Adjective** | हिंदी: विवेकपूर्ण/समझदार : Having, showing, or characterized by good judgment or sound thinking; wise and careful.
- ***Synonyms***: Prudent, sensible, wise, thoughtful, discerning, sagacious
_Example_: The company made **judicious** investments that helped them weather the economic downturn. *(Adjective: showing good judgment)*

=====

### PREJUDICE
@@
**Noun** | हिंदी: पूर्वाग्रह/पक्षपात : A preconceived opinion not based on reason or experience; bias against a particular group.
**Verb** | हिंदी: पूर्वाग्रहित करना : To give rise to prejudice in; to cause to have an unfair bias.
- ***Synonyms***:
    - **Noun:**
        - *Unreasoned bias:* Bias, preconception, partiality, discrimination, intolerance
    - **Verb:**
        - *Cause bias:* Bias, influence unfairly, predispose, color
_Example_:
1. Racial **prejudice** has no place in a modern, diverse society. *(Noun: unfair bias)*
2. The negative media coverage could **prejudice** potential jurors against the defendant. *(Verb: cause to be biased)*

=====

### SUBJUGATE
@@
**Verb** | हिंदी: अधीन करना/दबाना : To bring under control or dominion; to conquer and rule over forcibly.
- ***Synonyms***: Conquer, subdue, dominate, enslave, overpower, suppress
_Example_: The empire sought to **subjugate** neighboring territories through military force. *(Verb: bring under control by force)*
<!--SR:!2025-07-11,11,230-->

=====
## **21 LOCU/ LOQU/ LOGUE/ ** = speak thought speech

### CIRCUMLOCUTION
@@
**Noun** | हिंदी: घुमा-फिराकर बात करना : The use of many words where fewer would do, especially in a deliberate attempt to be vague or evasive.
- ***Synonyms***: Verbosity, roundabout language, periphrasis, indirect expression, wordiness, prolixity
_Example_: Instead of directly refusing, he used **circumlocution** to avoid giving a clear answer to the simple question. *(Noun: roundabout way of speaking)*

=====

### COLLOQUIAL
@@
**Adjective** | हिंदी: बोलचाल का/लोकप्रचलित : Characteristic of or appropriate to ordinary conversation rather than formal speech or writing; informal.
- ***Synonyms***: Informal, conversational, casual, everyday, vernacular, idiomatic
_Example_: The author uses **colloquial** language in her novels to make the dialogue feel more authentic. *(Adjective: informal, conversational)*

=====

### DIALOGUE
@@
**Noun** | हिंदी: संवाद/वार्तालाप : A conversation between two or more people; the lines spoken by characters in drama or fiction; a discussion aimed at resolution.
- ***Synonyms***: Conversation, discussion, talk, exchange, discourse, communication
_Example_: The movie was praised for its realistic **dialogue** that captured how people actually speak. *(Noun: conversation between characters)*

=====

### ELOCUTION
@@
**Noun** | हिंदी: वक्तृत्व कला/उच्चारण कौशल : The skill of clear and expressive speech, especially of distinct pronunciation and articulation.
- ***Synonyms***: Oratory, public speaking, speech-making, rhetoric, articulation, delivery
_Example_: As part of her training, she took **elocution** lessons to improve her pronunciation and public speaking skills. *(Noun: skill of clear speech and pronunciation)*

=====

### ELOQUENT
@@
**Adjective** | हिंदी: वाक्पटु/सुवक्ता : Fluent or persuasive in speaking or writing; clearly expressing or indicating something.
- ***Synonyms***: Articulate, fluent, expressive, persuasive, well-spoken, silver-tongued
_Example_: Her **eloquent** speech about climate change moved the audience to action. *(Adjective: fluent and persuasive in expression)*

=====

### EPILOGUE
@@
**Noun** | हिंदी: उपसंहार/समापन कथन : A section or speech at the end of a book or play that serves as a comment on or conclusion to what has happened.
- ***Synonyms***: Afterword, conclusion, postscript, closing statement, coda, finale
_Example_: The author added an **epilogue** explaining what happened to the characters ten years after the main story. *(Noun: concluding section)*

=====

### GRANDILOQUENT
@@
**Adjective** | हिंदी: अतिवादी/बड़े-बड़े शब्दों से युक्त : Using language or expressed in a way that is intended to impress people but sounds ridiculous and uses unnecessarily long words.
- ***Synonyms***: Pompous, bombastic, verbose, flowery, high-flown, pretentious
_Example_: His **grandiloquent** speeches were full of elaborate metaphors but contained little substance. *(Adjective: using overly elaborate language)*

=====

### LOQUACIOUS
@@
**Adjective** | हिंदी: वाचाल/बातूनी : Tending to talk a great deal; very talkative.
- ***Synonyms***: Talkative, garrulous, verbose, chatty, conversational, long-winded
_Example_: The **loquacious** guide provided far more historical details than the tourists could absorb. *(Adjective: excessively talkative)*

=====

### MONOLOGUE
@@
**Noun** | हिंदी: एकालाप/एकोक्ति : A long speech by one person during a conversation; a dramatic soliloquy.
- ***Synonyms***: Soliloquy, speech, discourse, oration, address, lecture
_Example_: The actor delivered a powerful **monologue** that revealed his character's inner thoughts. *(Noun: extended speech by one person)*

=====

### PROLOGUE
@@
**Noun** | हिंदी: प्रस्तावना/प्रारंभिक कथन : A separate introductory section of a literary or musical work; an event or action that leads to another event or situation.
- ***Synonyms***: Introduction, preface, foreword, preamble, prelude, opening
_Example_: The **prologue** of the novel set the historical context for the story that followed. *(Noun: introductory section)*
<!--SR:!2025-07-17,17,250-->

=====
## **22 LUC/ LUM/ LUS/** = light, shine

### ELUCIDATE
@@
**Verb** | हिंदी: स्पष्ट करना/व्याख्या करना : To make clear or explain something that was previously difficult to understand.
- ***Synonyms***: Clarify, explain, illuminate, explicate, interpret, expound
_Example_: The professor took time to **elucidate** the complex theory so that all students could comprehend it. *(Verb: make clear)*

=====

### ILLUMINATE
@@
**Verb** | हिंदी: प्रकाशित करना; स्पष्ट करना : To provide or brighten with light; To make clear or explain something.
- ***Synonyms***:
    - **Verb:**
        - *Provide light:* Light up, brighten, shine on, enlighten
        - *Make clear:* Clarify, elucidate, explain, reveal
_Example_:
1. The candles **illuminated** the dining room during the power outage. *(Verb: provide light)*
2. Her research **illuminated** several previously misunderstood aspects of medieval history. *(Verb: make clear or explain)*

=====

### ILLUSTRATE
@@
**Verb** | हिंदी: चित्रित करना; उदाहरण देना : To provide with visual features or pictures; To make clear by using examples.
- ***Synonyms***:
    - **Verb:**
        - *Provide pictures:* Depict, diagram, picture, visualize
        - *Provide examples:* Demonstrate, exemplify, show, clarify
_Example_:
1. The children's book was beautifully **illustrated** with watercolor paintings. *(Verb: provided with pictures)*
2. She used case studies to **illustrate** the practical applications of the theory. *(Verb: make clear by example)*

=====

### LUSTER
@@
**Noun** | हिंदी: चमक/आभा; शोभा : A gentle sheen or soft glow reflected from a surface; Excellence or distinction.
- ***Synonyms***:
    - **Noun:**
        - *Shine:* Sheen, gleam, glow, brilliance, radiance, polish
        - *Excellence:* Glory, distinction, prestige, renown
_Example_:
1. The pearls had a beautiful **luster** that caught the light. *(Noun: gentle sheen)*
2. His reputation lost its **luster** after the scandal. *(Noun: excellence or distinction)*

=====

### PELLUCID
@@
**Adjective** | हिंदी: पारदर्शी; स्पष्ट : Allowing maximum passage of light; transparently clear; Easy to understand; lucid.
- ***Synonyms***: Transparent, clear, lucid, limpid, comprehensible, crystalline
_Example_: Her **pellucid** explanation of the complex concept made it accessible to the entire audience. *(Adjective: extremely clear)* *(Rare)*

=====

### TRANSLUCENT
@@
**Adjective** | हिंदी: पारभासी/अर्धपारदर्शी : Allowing light to pass through but diffusing it so that objects on the other side are not clearly visible.
- ***Synonyms***: Semi-transparent, partly transparent, diaphanous, gauzy, cloudy
_Example_: The bathroom window had **translucent** glass that let in light while preserving privacy. *(Adjective: allowing light but not clear visibility)*

=====
## **23 LUD** = to play, trick

### ALLUDE
@@
**Verb** | हिंदी: संकेत करना/इशारा करना : To refer to something indirectly or by suggestion rather than explicit mention.
- ***Synonyms***: Refer, hint, suggest, mention, imply, insinuate
_Example_: In her speech, she **alluded** to past failures without specifically naming anyone responsible. *(Verb: refer indirectly)*

=====

### COLLUDE
@@
**Verb** | हिंदी: मिलीभगत करना/षड्यंत्र करना : To cooperate secretly or illegally in order to deceive or gain an advantage.
- ***Synonyms***: Conspire, plot, scheme, connive, connive, cooperate secretly
_Example_: The investigation revealed that several companies had **colluded** to fix prices in the industry. *(Verb: cooperate secretly for improper purposes)*

=====

### DELUDE
@@
**Verb** | हिंदी: धोखा देना/भ्रमित करना : To mislead the mind or judgment of; to deceive.
- ***Synonyms***: Mislead, deceive, fool, trick, dupe, hoodwink
_Example_: He continued to **delude** himself into thinking she would return despite all evidence to the contrary. *(Verb: mislead or deceive)*

=====

### ELUDE
@@
**Verb** | हिंदी: बचना/चकमा देना : To evade or escape from, typically in a skillful or cunning way; to fail to be understood or grasped.
- ***Synonyms***: Evade, escape, avoid, dodge, slip away from, baffle
_Example_: The meaning of the ancient text continued to **elude** scholars despite years of study. *(Verb: escape understanding)*

=====

### ILLUDE
@@
**Verb** | हिंदी: छलना/भ्रम उत्पन्न करना : To deceive or create an illusion; to trick.
- ***Synonyms***: Deceive, trick, delude, mislead, fool, beguile
_Example_: The magician used mirrors to **illude** the audience into believing objects had disappeared. *(Verb: create an illusion)* *(Rare)*

=====

### LUDICROUS
@@
**Adjective** | हिंदी: हास्यास्पद/बेतुका : So foolish, unreasonable, or out of place as to be amusing; ridiculous.
- ***Synonyms***: Absurd, ridiculous, preposterous, laughable, comical, farcical
_Example_: The excuse he gave for missing the meeting was so **ludicrous** that nobody could keep a straight face. *(Adjective: absurdly foolish)*

=====

### PRELUDE
@@
**Noun** | हिंदी: प्रस्तावना/भूमिका : An introductory piece of music; An action or event serving as an introduction to something more important.
- ***Synonyms***: Introduction, preliminary, forerunner, overture, precursor, prologue
_Example_: The economic crisis was merely a **prelude** to the political upheaval that followed. *(Noun: introductory event)*

=====
## **24 MAGN/ MAGNA/ MAJ/ MAS/ MAX** = great, big

### MAGNANIMOUS
@@
**Adjective** | हिंदी: उदार/दयालु : Very generous or forgiving, especially toward a rival or less powerful person.
- ***Synonyms***: Generous, benevolent, charitable, big-hearted, noble, altruistic
_Example_: The CEO was **magnanimous** in victory, praising the hard work of her competitors rather than gloating. *(Adjective: generously forgiving)*
<!--SR:!2025-07-17,17,250-->

=====

### MAGNATE
@@
**Noun** | हिंदी: उद्योगपति/धनकुबेर : A wealthy and influential person, especially in business or industry.
- ***Synonyms***: Tycoon, mogul, baron, industrialist, entrepreneur, business leader
_Example_: The oil **magnate** donated millions to establish a new wing at the city hospital. *(Noun: wealthy industrialist)*

=====

### MAGNIFICENT
@@
**Adjective** | हिंदी: शानदार/भव्य : Extremely beautiful, elaborate, or impressive; grand or splendid in appearance or quality.
- ***Synonyms***: Splendid, majestic, grand, superb, impressive, spectacular
_Example_: The **magnificent** palace with its gold-plated domes and marble halls left visitors in awe. *(Adjective: impressively beautiful)*

=====

### MAGNIFY
@@
**Verb** | हिंदी: बढ़ाना/आवर्धित करना : To make something appear larger than it is, especially through a lens; To increase the importance or effect of something.
- ***Synonyms***: Enlarge, amplify, increase, exaggerate, intensify, heighten
_Example_: The microscope can **magnify** cells up to a thousand times their actual size. *(Verb: make appear larger)*

=====

### MAGNILOQUENT
@@
**Adjective** | हिंदी: बड़बोला/अतिशयोक्तिपूर्ण : Using high-flown or extravagantly colorful language, especially in a pompous way.
- ***Synonyms***: Bombastic, grandiose, pompous, high-flown, pretentious, verbose
_Example_: The politician's **magniloquent** speeches impressed some but struck others as insincere and overblown. *(Adjective: using overly elaborate language)* *(Rare)*
<!--SR:!2025-07-19,19,251-->

=====

### MAGNITUDE
@@
**Noun** | हिंदी: परिमाण/आकार; महत्व; तीव्रता : Size or extent of something; Importance or significance; A measure of brightness (stars) or intensity (earthquakes).
- ***Synonyms***:
    - **Noun:**
        - *Size:* Extent, dimension, proportions, scale, scope
        - *Importance:* Significance, consequence, moment, weight
        - *Measurement:* Intensity, strength, force, power
_Example_:
1. Scientists were surprised by the **magnitude** of the earthquake that registered 8.2 on the Richter scale. *(Noun: size or intensity)*
2. He failed to grasp the **magnitude** of the decision and its potential consequences. *(Noun: importance or significance)*
<!--SR:!2025-05-11,8,251-->

=====

### MAGNUM OPUS
@@
**Noun** | हिंदी: सर्वश्रेष्ठ कृति : The greatest work of an artist, writer, or composer.
- ***Synonyms***: Masterpiece, masterwork, chef-d'oeuvre, tour de force, crowning achievement
_Example_: Many critics consider "War and Peace" to be Tolstoy's **magnum opus**. *(Noun: greatest creative work)*

=====

### MAJESTY
@@
**Noun** | हिंदी: प्रताप/राजसी शान; महामहिम : Impressive beauty, scale, or dignity; A title used to address or refer to a sovereign.
- ***Synonyms***:
    - **Noun:**
        - *Grandeur:* Splendor, magnificence, grandeur, dignity, stateliness
        - *Royal title:* Sovereignty, highness, excellency
_Example_:
1. The **majesty** of the mountains against the sunset left us speechless. *(Noun: impressive grandeur)*
2. The ambassador was granted an audience with Her **Majesty** the Queen. *(Noun: royal title)*

=====

### MASTER
@@
**Noun** | हिंदी: स्वामी/मालिक; गुरु/आचार्य; विशेषज्ञ : A person who has control or authority; An expert or skilled practitioner; A teacher or leader.
**Verb** | हिंदी: नियंत्रित करना; महारत हासिल करना : To gain control over; To become highly skilled at.
**Adjective** | हिंदी: मुख्य/प्रधान : Being a main or principal item; Original or controlling.
- ***Synonyms***:
    - **Noun:**
        - *Authority figure:* Owner, lord, ruler, boss, controller
        - *Expert:* Virtuoso, genius, adept, professional, authority
        - *Teacher:* Mentor, instructor, guru, sensei
    - **Verb:**
        - *Control:* Conquer, overcome, subdue, tame
        - *Learn thoroughly:* Perfect, excel at, become proficient in
    - **Adjective:**
        - *Main:* Principal, chief, primary, dominant, controlling
_Example_:
1. She is a **master** of classical violin and performs worldwide. *(Noun: expert)*
2. It took years for him to **master** the art of meditation. *(Verb: become highly skilled at)*
3. Keep the **master** key in a secure location as it opens all doors. *(Adjective: principal or controlling)*

=====
## **25 MAL** = bad

### ANOMALY
@@
**Noun** | हिंदी: विसंगति/असामान्यता : Something that deviates from what is standard, normal, or expected.
- ***Synonyms***: Irregularity, deviation, oddity, peculiarity, abnormality, aberration
_Example_: Scientists discovered an **anomaly** in the data that couldn't be explained by existing theories. *(Noun: deviation from normal pattern)*

=====

### MALADROIT
@@
**Adjective** | हिंदी: अनाड़ी/बेढंगा : Showing or characterized by clumsiness or lack of skill.
- ***Synonyms***: Clumsy, awkward, inept, bungling, unskillful, ungainly
_Example_: His **maladroit** attempt at fixing the computer made the problem worse. *(Adjective: clumsy or unskilled)*

=====

### MALADY
@@
**Noun** | हिंदी: रोग/व्याधि; समस्या : A disease or ailment; A serious problem or condition.
- ***Synonyms***: Illness, disease, ailment, disorder, affliction, complaint, problem
_Example_: The doctor couldn't identify the strange **malady** that caused the patient's symptoms. *(Noun: disease or ailment)*

=====

### MALEFICENT
@@
**Adjective** | हिंदी: अनिष्टकारी/हानिकारक : Causing or capable of causing harm or evil.
- ***Synonyms***: Harmful, evil, malicious, wicked, baleful, nefarious
_Example_: The villain's **maleficent** schemes threatened the entire kingdom. *(Adjective: evil or harmful)* *(Rare)*

=====

### MALEVOLENT
@@
**Adjective** | हिंदी: द्वेषपूर्ण/शत्रुतापूर्ण : Having or showing a wish to do evil to others.
- ***Synonyms***: Evil, malicious, spiteful, hostile, ill-intentioned, vindictive
_Example_: The character was portrayed as a **malevolent** force seeking to destroy anything good. *(Adjective: wishing harm to others)*

=====

### MALFEASANT
@@
**Adjective, Noun** | हिंदी: कदाचारी/अपराधी : Engaging in misconduct or wrongdoing, especially illegal activity by a public official.
- ***Synonyms***: Corrupt, criminal, wrongdoing, offending, misbehaving, delinquent
_Example_: The investigation uncovered **malfeasant** activities throughout several departments of the local government. *(Adjective: engaging in misconduct)* *(Rare)*
<!--SR:!2025-07-18,18,251-->

=====

### MALICE
@@
**Noun** | हिंदी: द्वेष/वैर : The intention or desire to cause harm or ill will to another.
- ***Synonyms***: Spite, ill will, malevolence, enmity, animosity, vindictiveness
_Example_: The prosecutor needed to prove that the attack was committed with **malice** aforethought to secure a murder conviction. *(Noun: intention to harm)*

=====

### MALIGN
@@
**Verb** | हिंदी: बदनाम करना/निंदा करना : To speak harmful untruths about; to slander or defame.
**Adjective** | हिंदी: हानिकारक/दुष्ट : Evil in nature or effect; injurious.
- ***Synonyms***:
    - **Verb:**
        - *Defame:* Slander, libel, disparage, vilify, denigrate, smear
    - **Adjective:**
        - *Harmful:* Evil, pernicious, injurious, baleful, noxious
_Example_:
1. Political opponents often try to **malign** each other's character during election campaigns. *(Verb: speak ill of)*
2. The tumor was found to be **malign** and required immediate surgery. *(Adjective: harmful or evil)*

=====

### MALNUTRITION
@@
**Noun** | हिंदी: कुपोषण : A condition caused by an inadequate or unbalanced diet or by a medical condition that prevents proper absorption of nutrients.
- ***Synonyms***: Undernourishment, malnourishment, poor nutrition, nutritional deficiency
_Example_: Aid workers provided supplements to combat **malnutrition** among refugee children. *(Noun: poor nutritional condition)*

=====

### MALODOROUS
@@
**Adjective** | हिंदी: दुर्गंधयुक्त/बदबूदार : Having an unpleasant or offensive smell.
- ***Synonyms***: Smelly, foul-smelling, stinking, fetid, rank, noisome
_Example_: The **malodorous** garbage in the alley attracted flies and needed to be removed immediately. *(Adjective: having an offensive smell)*

=====
## **26 MATR/ MATRI/ MATER** = mother

### MATERNAL
@@
**Adjective** | हिंदी: मातृ/मातृक : Relating to or characteristic of a mother; relating to or derived from the mother's side of the family.
- ***Synonyms***: Motherly, mother-like, nurturing, caring, protective, mom-like
_Example_: Her **maternal** instincts kicked in immediately when she saw the child in danger. *(Adjective: relating to mother or motherly)*

=====

### MATRIARCH
@@
**Noun** | हिंदी: कुलमाता/वंशप्रमुख महिला : A woman who is the head of a family or tribe; a powerful older woman who controls a family or organization.
- ***Synonyms***: Female head, mother figure, family leader, ruling mother, dominant female
_Example_: As the family **matriarch**, grandmother made all the important decisions at family gatherings. *(Noun: female head of family)*

=====

### MATRIMONY
@@
**Noun** | हिंदी: विवाह/शादी : The state of being married; marriage, especially viewed as a formal institution.
- ***Synonyms***: Marriage, wedlock, married state, marital union, conjugal bond, nuptials
_Example_: After dating for five years, they finally entered into holy **matrimony** last spring. *(Noun: state of marriage)*

=====

### MATRON
@@
**Noun** | हिंदी: गृहिणी/प्रबंधिका : A married woman, especially one who is mature and dignified; a woman in charge of domestic arrangements in a hospital, prison, or school.
- ***Synonyms***: Married woman, dame, lady, dowager, house mother, supervisor
_Example_: The hospital **matron** ensured all patients received proper care and that the ward was maintained efficiently. *(Noun: woman in charge)*

=====
## **27 MNE/ MEMOR/ MEMEN/ REMINISC** = remember

### AMNESIA
@@
**Noun** | हिंदी: स्मृतिलोप : A partial or total loss of memory, typically due to brain injury, illness, or psychological trauma.
- ***Synonyms***: Memory loss, forgetfulness, blackout, blank, oblivion
_Example_: After the accident, he suffered from **amnesia** and couldn't remember his own name. *(Noun: memory loss)*

=====

### COMMEMORATE
@@
**Verb** | हिंदी: स्मरण करना/याद करना : To recall and show respect for someone or something in a ceremony or through a monument.
- ***Synonyms***: Memorialize, celebrate, honor, observe, remember, recognize
_Example_: The city will **commemorate** the 50th anniversary of the historic event with a special parade. *(Verb: honor the memory of)*
<!--SR:!2025-05-13,8,251-->

=====

### IMMEMORIAL
@@
**Adjective** | हिंदी: अनादिकाल से : Originating in the distant past; extending beyond the reach of memory, record, or tradition.
- ***Synonyms***: Ancient, age-old, time-honored, traditional, primeval, primordial
_Example_: This ritual has been practiced since time **immemorial**. *(Adjective: ancient beyond memory)*

=====

### MEMENTO
@@
**Noun** | हिंदी: यादगार वस्तु/स्मृति-चिन्ह : An object kept as a reminder or souvenir of a person, place, or event.
- ***Synonyms***: Souvenir, keepsake, reminder, token, remembrance, trophy
_Example_: She kept the seashell as a **memento** of their beach vacation. *(Noun: keepsake)*

=====

### MEMORIAL
@@
**Noun** | हिंदी: स्मारक/यादगार : A structure, statue, or event established to remind people of a person or event.
**Adjective** | हिंदी: स्मारक संबंधी : Relating to or preserving the memory of a person or event.
- ***Synonyms***:
    - **Noun:**
        - *Monument:* Monument, tribute, shrine, statue, commemoration
    - **Adjective:**
        - *Commemorative:* Commemorative, remembrance, in memory of
_Example_:
1. The town erected a **memorial** to honor the soldiers who died in the war. *(Noun: monument)*
2. They attended the **memorial** service to pay their respects. *(Adjective: commemorative)*

=====

### MEMORY
@@
**Noun** | हिंदी: स्मृति/याद; स्मरण शक्ति : A recollection of past events or people; the faculty by which the mind stores and recalls information.
- ***Synonyms***:
    - **Noun:**
        - *Recollection:* Remembrance, reminiscence, recollection, impression
        - *Mental faculty:* Recall, retention, mindfulness, remembrance
_Example_:
1. She has fond **memories** of her childhood summers by the lake. *(Noun: recollections)*
2. His **memory** is still excellent despite his advanced age. *(Noun: ability to remember)*

=====

### MNEMONICS
@@
**Noun** | हिंदी: स्मृति सहायक : A system or technique designed to aid the memory.
- ***Synonyms***: Memory aid, memory device, memory technique, memory system
_Example_: Students use **mnemonics** like "Every Good Boy Does Fine" to remember the notes on a musical staff. *(Noun: memory aid technique)*

=====

### REMEMBER
@@
**Verb** | हिंदी: याद करना/स्मरण करना : To recall to mind; to retain in memory; to bear in mind.
- ***Synonyms***: Recollect, recall, reminisce, think back, memorize, retain
_Example_: 
1. I still **remember** the day we first met. *(Verb: recall to mind)*
2. Please **remember** to lock the door when you leave. *(Verb: keep in mind)*

=====

### REMINISCE
@@
**Verb** | हिंदी: पुरानी यादें ताज़ा करना : To indulge in enjoyable recollection of past events.
- ***Synonyms***: Recollect, recall, remember, look back, reflect, muse
_Example_: The elderly couple sat on the porch to **reminisce** about their younger days. *(Verb: recall fond memories)*

=====
## **28 MONO** = one single

### MONARCHY
@@
**Noun** | हिंदी: राजतंत्र/राजशाही : A form of government with a monarch (king, queen, emperor) at the head of state.
- ***Synonyms***: Kingdom, realm, crown, sovereign state, empire, royalty
_Example_: The **monarchy** in the United Kingdom is primarily ceremonial rather than political. *(Noun: royal government)*

=====

### MONOCHROME
@@
**Adjective** | हिंदी: एकरंगी/एकवर्णी : Containing or using only one color or shades of one color.
**Noun** | हिंदी: एकरंगी चित्र : A photograph or picture developed or executed in a single color.
- ***Synonyms***:
    - **Adjective:**
        - *Single-colored:* Single-colored, one-toned, grayscale, black-and-white
    - **Noun:**
        - *Image:* Black-and-white photo, grayscale image
_Example_:
1. The art exhibition featured **monochrome** paintings in various shades of blue. *(Adjective: single-colored)*
2. The photographer specialized in dramatic **monochromes** that captured urban landscapes. *(Noun: black-and-white images)*

=====

### MONOGAMY
@@
**Noun** | हिंदी: एकविवाह/एकपत्नीत्व : The practice or state of being married to only one person at a time or having only one mate.
- ***Synonyms***: Faithfulness, fidelity, exclusivity, one-to-one relationship
_Example_: Many species of birds practice **monogamy** and mate for life. *(Noun: exclusive pairing)*

=====

### MONOLITH
@@
**Noun** | हिंदी: एकाश्म/विशालकाय पत्थर; एकरूप संस्था : A large single upright block of stone; a large, impersonal, and uniform structure or organization.
- ***Synonyms***:
    - **Noun:**
        - *Stone structure:* Megalith, standing stone, obelisk, column
        - *Uniform entity:* Colossus, behemoth, giant, unified whole
_Example_:
1. Stonehenge consists of several **monoliths** arranged in a circular pattern. *(Noun: large stone block)*
2. The corporation was once viewed as an unchangeable **monolith** in the industry. *(Noun: large, uniform entity)*

=====

### MONOTONOUS
@@
**Adjective** | हिंदी: एकरस/नीरस : Dull, tedious, and repetitious; lacking in variety and interest.
- ***Synonyms***: Tedious, repetitive, boring, unvarying, dull, flat
_Example_: The speaker's **monotonous** voice made it difficult for the audience to stay engaged. *(Adjective: lacking variation)*

=====
## **29 MOR/ MORI/ MORT** = death

### IMMORTAL
@@
**Adjective** | हिंदी: अमर/अजर : Living or lasting forever; not subject to death.
**Noun** | हिंदी: अमर प्राणी : A being that lives forever and cannot die.
- ***Synonyms***:
    - **Adjective:**
        - *Undying:* Eternal, everlasting, deathless, perpetual, undying
    - **Noun:**
        - *Divine being:* Deity, god, divine being
_Example_:
1. Greek mythology is filled with stories of **immortal** gods and goddesses. *(Adjective: undying)*
2. His poems will make him an **immortal** in literary history. *(Noun: person whose fame lives forever)*

=====

### MORBID
@@
**Adjective** | हिंदी: रुग्ण/विकृत : Characterized by an abnormal and unhealthy interest in disturbing subjects, especially death and disease.
- ***Synonyms***: Macabre, gruesome, ghoulish, grisly, grotesque, unhealthy
_Example_: She had a **morbid** fascination with crime scenes and murder investigations. *(Adjective: unhealthily preoccupied with death)*

=====

### MORIBUND
@@
**Adjective** | हिंदी: मृतप्राय/मरणासन्न : At the point of death; in terminal decline; lacking vitality or vigor.
- ***Synonyms***: Dying, declining, waning, stagnating, obsolescent, terminal
_Example_: The once-thriving industry is now **moribund**, with factories closing and workers being laid off. *(Adjective: in terminal decline)*

=====

### MORTAL
@@
**Adjective** | हिंदी: नश्वर/मरणशील; प्राणघातक : Subject to death; not immortal; causing or capable of causing death.
**Noun** | हिंदी: मनुष्य/मानव : A human being, as opposed to a divine being.
- ***Synonyms***:
    - **Adjective:**
        - *Subject to death:* Perishable, finite, transient, ephemeral
    - **Noun:**
        - *Human:* Human being, person, human
_Example_:
1. All humans are **mortal** and must someday face death. *(Adjective: subject to death)*
2. The gods often disguised themselves as **mortals** in ancient myths. *(Noun: human beings)*

=====

### MORTIFY
@@
**Verb** | हिंदी: लज्जित करना; कष्ट देना : To cause someone to feel very embarrassed or ashamed; to subdue bodily desires through self-discipline.
- ***Synonyms***:
    - **Verb:**
        - *Embarrass:* Humiliate, shame, humble, abash
        - *Subdue:* Suppress, control, discipline, deny
_Example_:
1. She was **mortified** when she tripped and fell in front of the entire audience. *(Verb: extremely embarrassed)*
2. The ascetic monk sought to **mortify** his flesh through fasting and prayer. *(Verb: subdue bodily desires)* *(Rare)*

=====

### MORTUARY
@@
**Noun** | हिंदी: शवगृह : A room or building in which dead bodies are kept before burial or cremation.
- ***Synonyms***: Funeral home, funeral parlor, morgue
_Example_:
1. The body was taken to the **mortuary** to be prepared for the funeral. *(Noun: place where dead bodies are kept)*

=====

### POST-MORTEM
@@
**Noun** | हिंदी: शव-परीक्षा; कार्य-समीक्षा : An examination of a dead body to determine the cause of death
- ***Synonyms***: Autopsy, necropsy, examination
_Example_:
1. The **post-mortem** revealed that the victim died from poisoning. *(Noun: autopsy)*

=====
## **30 MORPH** = from, shape

### ANTHROPOMORPHIC
@@
**Adjective** | हिंदी: मानवरूपी : Attributing human characteristics, behaviors, or emotions to non-human entities such as animals, gods, or objects.
- ***Synonyms***: Humanized, humanlike, personified, human-shaped, man-like
_Example_: Disney movies often feature **anthropomorphic** animals that talk, wear clothes, and display human emotions. *(Adjective: having human qualities)*

=====

### METAMORPHOSIS
@@
**Noun** | हिंदी: कायांतरण/रूपांतरण : A complete change of physical form, structure, or substance; a profound transformation.
- ***Synonyms***: Transformation, transmutation, evolution, mutation, conversion, change
_Example_: The **metamorphosis** of a caterpillar into a butterfly is one of nature's most dramatic transformations. *(Noun: complete transformation)*

=====

### MORPH
@@
**Verb** | हिंदी: रूपांतरित होना : To change form or character completely, often gradually or seamlessly.
- ***Synonyms***: Transform, change, metamorphose, transmute, convert
_Example_: The image software allowed the designer to **morph** one face into another. *(Verb: transform gradually)*

=====

### POLYMORPHOUS
@@
**Adjective** | हिंदी: बहुरूपी : Having, taking, or occurring in various forms, characters, or styles.
- ***Synonyms***: Multiform, multifaceted, protean, diverse, variable, changeable
_Example_: The **polymorphous** nature of the virus makes it difficult to create an effective vaccine against it. *(Adjective: existing in many forms)*

=====

### ZOOMORPHIC
@@
**Adjective** | हिंदी: पशुरूपी : Having or representing animal forms; attributing animal qualities to humans, deities, or objects.
- ***Synonyms***: Animal-shaped, beast-like, theriomorphic, animal-formed
_Example_: Ancient Egyptian deities were often depicted in **zoomorphic** form, such as the falcon-headed god Horus. *(Adjective: having animal qualities)*

=====

