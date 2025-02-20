# Enhanced Grammar and Sentence Analysis Prompt

Act as Grammar GPT:
I will provide a sentence. Please perform the following tasks:

1. Check for grammatical correctness:
   - If errors are found, I'll point them out and suggest corrections.
   - If the sentence is correct, I'll proceed with the analysis.

2. Analyze each word in the sentence:
   a) Identify its part of speech (noun, verb, adjective, adverb, pronoun, preposition, conjunction, interjection, determiner).
   b) Explain its role or function in the sentence (subject, predicate, direct object, indirect object, modifier, etc.).
   
3. Return Response in Tabular: You should present the analysis in a table format for easy reference.

Example request: Sonali prepared herself very well for the exam. 

Example response:

| Word     | Part of Speech | Type                         | Role in Sentence                               |
| -------- | -------------- | ---------------------------- | ---------------------------------------------- |
| Sonali   | Noun           | Proper Noun                  | Subject                                        |
| prepared | Verb           | Transitive Verb (Past Tense) | Action Verb                                    |
| herself  | Pronoun        | Reflexive Pronoun            | Direct Object                                  |
| very     | Adverb         | Adverb of Degree             | Modifies the adverb "well"                     |
| well     | Adverb         | Adverb of Manner             | Modifies the adverb "prepared"                 |
| for      | Preposition    | Preposition                  | Shows the purpose or target of the preparation |
| the      | Article        | Definite Article             | Modifies "exam"                                |
| exam     | Noun           | Common Noun                  | Object of the Preposition "for"                |
|          |                |                              |                                                |
|          |                |                              |                                                |

```c
I will provide a bunch of words. Please uppercase each word and generate a single sentence that contain only words separated by ; semi-colon
```

```c
I will provide a list of words. For each word, perform the following steps: Identify its base or root form (e.g., 'running' → 'run'). Generate all relevant word forms derived from the base word, including but not limited to: Past tense (e.g., 'ran'). Noun, verb, and adjective forms (e.g., 'runner', 'running', 'run'). Combine all derived word forms into a single sentence, ensuring each word is separated by a semicolon (;). Capitalize every word in the final sentence. Ensure the output is a single, cohesive sentence with no additional punctuation or spaces between words and semicolons. Example: Input: 'running' Output: RUN;RAN;RUNNER;RUNNING; AND COMBINE ALL OUTPUT IN SINGLE SENTENCE
```
# Comprehensive Vocabulary Builder GPT


```c

I will give you word(s) , Follow the format below for each word and ensure clarity, accuracy, and completeness:

### WORD
@@ 
[All applicable forms of Part of Speech] | हिंदी: [translation]  : [Clear, concise meaning with brief context in English]
- ***Synonyms***: [2-6 most relevant direct synonyms]
- ***Antonyms***: [2-5 most relevant direct antonyms]

_Examples_
1. [Contextual sentence showing primary usage] *(Part of Speech)*
2. [Contextual sentence showing secondary usage if applicable] *(Part of Speech)*
	[If the word has additional relevant usages or nuances, provide further contextual sentences here, each preceded by a number.] *(Part of Speech)*
	
_Word Form Examples_
[List all relevant word forms derived from the base word, past tense, comparative/superlative forms, noun/verb/adjective forms, etc. ]
For each derived word:
[Derived word] : 
[Contextual sentence using the derived word]*(Part of Speech)*
[Synonyms: [2-6 most relevant direct synonyms for the derived form]]

=====

HERE IS AN EXAMPLE RESULT THAT YOU NEED TO REPRODUCE:

### ACUTE

@@  
**Adjective** | हिंदी: तीव्र, नुकीला : 

1. Sharp or severe in effect, intense.
2. Having a sharp or pointed end.
3. Keenly perceptive or intelligent.
4. Referring to an angle less than 90 degrees in geometry.
5. A condition or disease with rapid onset and severe symptoms.

- ***Synonyms***: sharp, severe, intense, keen, critical
- ***Antonyms***: dull, mild, chronic, blunt, sluggish

_Examples_

1. The patient complained of **acute** pain in the abdomen. _(Adjective: severe/intense)_
2. She has an **acute** sense of hearing, able to detect even the faintest sounds. _(Adjective: keen/perceptive)_
3. The **acute** angle in the triangle measured 45 degrees. _(Adjective: geometric)_

_Word Form Examples_

1. **Acutely**:
	- The disease manifested in an **acutely** painful form, requiring strong medication. _(Adverb: intensely)_
	- ***Synonyms***: intensely, sharply, severely, keenly, miserably, dismally

2. **Acuity**:
	- The **acuity** of her vision allowed her to notice subtle details in the painting._((Noun: keenness of perception )
	- ***Synonyms***: sharpness, keenness, perceptiveness, sensitivity
				  
=====

NOTE : NEVER FORGET "=====" AT END .
```

```
_Note_

"Acute" differs from "chronic" as it refers to conditions or situations that are **severe but short-term**, while "chronic" implies **long-term persistence**. It can describe **physical pain, mental awareness, crises, or sensory sharpness**.

```

```c

I will give you word(s) , Follow the format below for each word and ensure clarity, accuracy, and completeness:

### WORD
@@ 
[All applicable forms of Part of Speech] | हिंदी: [translation]  : [Clear, concise meaning with brief context in English]

##### 1. **[Primary Part of Speech]**: Detailed definition for this usage.

as in _[specific sense/context]_ (brief explanation of this sense):
	- ***Synonyms***: [2-6 most relevant synonyms]
	- ***Antonyms***: [2-5 most relevant synonyms]

_Examples_
	1.[Example sentence using the word]. _(Part of Speech: specific sense)_
	2.[Additional example sentences...]

[Repeat numbered sections for each major part of speech the word can take]

_Word Form Examples (if applicable)_
[List all relevant word forms derived from the base word, past tense, comparative/superlative forms, noun/verb/adjective forms, etc. ]
For each derived word:
[Derived word] : 
[Contextual sentence using the derived word]*(Part of Speech)*
[Synonyms: [2-6 most relevant synonyms for the derived form]]

=====

HERE IS AN EXAMPLE RESULT THAT YOU NEED TO REPRODUCE:

### STAGGER

@@  
**Verb / Noun** | हिंदी: लड़खड़ाना, हिलाना, झटका : To move unsteadily, as if about to fall; to astonish or shock greatly.

 1. **Verb**: To move unsteadily or with difficulty, often due to weakness or imbalance.

as in _totter_ (to sway or move back and forth unsteadily):

- ***Synonyms***: totter, sway, stumble, reel, lurch
- ***Antonyms***: steady, stabilize, balance

as in _astonish_ (to cause someone to be extremely surprised):

- ***Synonyms***: astonish, shock, amaze, astound, dumbfound, flabbergast
- ***Antonyms***: reassure, clarify, explain

_Examples:_

1. He **staggered** across the room after waking up. _(Verb: totter)_
2. The breathtaking view **staggered** her imagination. _(Verb: astonish)_


 2. **Noun**: An unsteady movement or walk.

as in _lurch_ (a sudden, unsteady motion):

- ***Synonyms***: lurch, stumble, reel, totter
- ***Antonyms***: stability, steadiness, balance

_Examples:_

1. The old man walked with a noticeable **stagger** after his injury. _(Noun: lurch)_
2. His step turned into a **stagger** after the exhausting hike. _(Noun: stumble)_


_Word Form Examples:_

1. **Staggering**:
    
    - The **staggering** beauty of the mountain left us speechless. _(Adjective: overwhelming)_
    - ***Synonyms***: astounding, shocking, overwhelming
2. **Staggered**:
    
    - She was **staggered** by the sudden news. _(Verb: past tense, shocked)_
    - ***Synonyms***: shocked, astonished, amazed
3. **Staggeringly**:
    
    - The view was **staggeringly** beautiful. _(Adverb: extremely)_
    - ***Synonyms***: incredibly, astonishingly, remarkably

=====

NOTE : NEVER FORGET "=====" AT END .

```


---

# Phrase & Idioms

```c
I will give you a phrasal verb, idiom, phrase, OR OWS.  Follow the format below for each word and ensure clarity, accuracy, and completeness:

### Phrase/Idiom/Phrasal Verb/ OWS
@@
[Clear, concise meaning with brief context in English]
- ***Synonyms***: [Synonyms/Similar expressions]
_Example_ : [Contextual sentence showing primary usage] 

=====

HERE IS AN EXAMPLE RESULT THAT YOU NEED TO REPRODUCE:

### Run of the Mill  
@@  
A phrase used to describe something that is ordinary, average, or not special in any way.  
- ***Synonyms***: Commonplace, standard, unexceptional  
_Example_: The restaurant serves **run-of-the-mill** food, nothing particularly memorable.  

=====

NOTE : NEVER FORGET "=====" AT END .
```
