
```c
I will provide a bunch of words. Please uppercase each word and generate a single sentence that contain only words separated by ; semi-colon
```

```c
I will provide a list of words. For each word, perform the following steps: Identify its base or root form (e.g., 'running' → 'run'). Generate all relevant word forms derived from the base word, including but not limited to: Past tense (e.g., 'ran'). Noun, verb, and adjective forms (e.g., 'runner', 'running', 'run'). Combine all derived word forms into a single sentence, ensuring each word is separated by a semicolon (;). Capitalize every word in the final sentence. Ensure the output is a single, cohesive sentence with no additional punctuation or spaces between words and semicolons. Example: Input: 'running' Output: RUN;RAN;RUNNER;RUNNING; AND COMBINE ALL OUTPUT IN SINGLE SENTENCE
```

# DICT GPT

## WORD

### TYPE -1

```c

I will give you word(s) , Follow the format below for each word and ensure clarity, accuracy, and correct grammar:

### WORD
@@ 
[All applicable forms of Part of Speech] | हिंदी: [translation]  : [Clear, concise meaning with brief context in English]
- ***Synonyms***: [2-6 most relevant direct synonyms]
- ***Antonyms***: [2-5 most relevant direct antonyms]

_Examples_
1. [Contextual sentence showing primary usage] *(Part of Speech: specific meaning hint)*
2. [Contextual sentence showing secondary usage if applicable] *(Part of Speech: specific meaning hint)*
	[If the word has additional relevant usages or nuances, provide further contextual sentences here, each preceded by a number.] *(Part of Speech: specific meaning hint)*
	
_Word Form Examples_
[List all relevant word forms derived from the base word, past tense, comparative/superlative forms, noun/verb/adjective forms, etc. ]
For each derived word:
[Derived word] : 
[Contextual sentence using the derived word]*(Part of Speech: specific meaning hint)*
[Synonyms: [2-6 most relevant direct synonyms for the derived form]]

=====

HERE IS AN EXAMPLE RESULT THAT YOU NEED TO REPRODUCE:

### LIGHT  
@@  
**Noun, Verb, Adjective** | हिंदी: प्रकाश, रोशनी :  
1. The natural agent that stimulates sight and makes things visible. *(Noun)*  
2. To illuminate or make something brighter. *(Verb)*  
3. Of little weight; easy to lift or move. *(Adjective)*  

- ***Synonyms***: radiance, glow, illumination *(Noun: brightness)*; brighten, illuminate, spotlight *(Verb)*; lightweight, airy, feathery *(Adjective)*  
- ***Antonyms***: darkness, shadow, obscurity *(Noun: brightness)*; darken, obscure, dim *(Verb)*; heavy, cumbersome, ponderous *(Adjective)*  

_Examples_  
1. The room was filled with **light** streaming through the open window. *(Noun: brightness)*  
2. She used a lantern to **light** the path ahead. *(Verb: illuminate)*  
3. The suitcase was surprisingly **light**, making it easy to carry. *(Adjective: not heavy)*  

_Word Form Examples_  
1. **LIGHTED**:  
   - The hallway was poorly **lighted**, making it hard to see. *(Adjective: illuminated)*  
   - ***Synonyms***: illuminated, lit, brightened, radiant, glowing  
2. **LIGHTING**: 🌟  
   - The stage **lighting** created a dramatic effect during the performance. *(Noun: arrangement of lights)*  
   - ***Synonyms***: illumination, radiance, brilliance, glow, luminescence  
3. **LIGHTWEIGHT**:  
   - The athlete was classified as a **lightweight** in boxing. *(Adjective/Noun: not heavy or a specific category)*  
   - ***Synonyms***: featherweight, slight, delicate, portable  

=====

NOTE : NEVER FORGET "=====" AT END .
And add 🌟 important word forms and *(Rare)* when the word is rare or obscure
RETURN IN CODE BLOCK
IF YOU UNDERSTAND ALL ABOVE INSTRUCTIONS JUST SAY "Yes".
```

### TYPE-2

```python
I will provide you with a word, phrase, or idiom. Generate a response strictly following the format and instructions below. Ensure accuracy, clarity, and adherence to the structural details.

### [Word/Phrase/Idiom]
@@
**[Part of Speech 1, e.g., Noun]** | हिंदी: [Hindi Term 1a / Hindi Term 1b]; [Hindi Term 2] : [Concise English Meaning for Term 1a/1b]; [Concise English Meaning for Term 2].
**[Part of Speech 2, e.g., Verb]** | हिंदी: [Hindi Term 3]; [Hindi Term 4] : [Concise English Meaning for Term 3]; [Concise English Meaning for Term 4].
*(Use separate lines for each major Part of Speech. Use `/` between Hindi terms that are synonymous for the *same* specific meaning. Use `;` to separate distinct Hindi terms corresponding to distinct English meanings listed in the same order after the colon.)*

- ***Synonyms***:
    - **[Part of Speech 1]:**
        - *[Meaning Hint 1]:* Synonym1, Synonym2, Synonym3
        - *[Meaning Hint 2]:* Synonym4, Synonym5
    - **[Part of Speech 2]:**
        - *[Meaning Hint 3]:* SynonymA, SynonymB
    *(Group synonyms by Part of Speech, then by specific meaning using an italicized meaning hint. List only English synonyms, separated by commas. Do not include Hindi here.)*

- ***Antonyms***:
    - **[Part of Speech 1]:**
        - *[Meaning Hint 1]:* Antonym1, Antonym2
        - *[Meaning Hint 2]:* Antonym3, Antonym4
    - **[Part of Speech 2]:**
        - *[Meaning Hint 3]:* AntonymA, AntonymB
    *(Follow the exact same structure as Synonyms. List only English antonyms. If no relevant antonyms exist for a specific meaning or for the entire word/phrase, omit that line or the entire Antonyms section.)*

_Example_:
1.  [Example sentence with the **word/phrase** in bold]. *(Part of Speech: specific meaning hint)*
2.  [Second example sentence for a different meaning/POS]. *(Part of Speech: specific meaning hint)*
*(Provide at least one example sentence for each distinct meaning/POS* defined above. Ensure the word/phrase is bolded. The clarification in parentheses should state the Part of Speech and a brief English hint corresponding to the meaning being illustrated.)*

_Word Form Examples_
[List all relevant word forms derived from the base word, past tense, comparative/superlative forms, noun/verb/adjective forms, etc. ]
For each derived word:
[Derived word] : 
[Contextual sentence using the derived word]*(Part of Speech)*
[Synonyms: [2-6 most relevant direct synonyms for the derived form]]

HERE IS AN EXAMPLE RESULT THAT YOU NEED TO REPRODUCE:

### MANDATE
@@
**Noun** | हिंदी: आदेश/जनादेश; अधिदेश : An official order or commission to do something; The authority granted by a constituency to act as its representative.
**Verb** | हिंदी: आदेश देना; अनिवार्य करना : To authorize or command officially; To require something by law or formal decision.
- ***Synonyms***:
    - **Noun:**
        - *Official order:* Command, directive, instruction, authorization, commission
        - *Political authority:* Authority, sanction, approval, endorsement
    - **Verb:**
        - *Order officially:* Decree, direct, command, require, prescribe
_Example_:
1. The government issued a **mandate** requiring masks in all public spaces. *(Noun: official order)*
2. After winning the election, she claimed a **mandate** to implement her proposed reforms. *(Noun: authority from voters)*
3. Federal law **mandates** that employers provide a safe workplace. *(Verb: requires by law)*

_Word Form Examples_  
1. **MANDATORY**: 🌟  
   - Wearing helmets is **mandatory** for all motorcycle riders in this country. *(Adjective: required by rule or law)*  
   - ***Synonyms***: compulsory, obligatory, required, essential, binding  
2. **MANDATED**:  
   - The policy was **mandated** by the board of directors to ensure compliance. *(Adjective: officially ordered)*  
   - ***Synonyms***: decreed, enforced, prescribed, imposed, authorized  

=====

NOTE : NEVER FORGET "=====" AT END .
And add 🌟 important word forms and *(Rare)* when the word is rare or obscure
RETURN IN CODE BLOCK
IF YOU UNDERSTAND ALL ABOVE INSTRUCTIONS JUST SAY "Yes".
```

```
### ACCOMPLICE  
@@  
**Noun** | हिंदी: सह-अपराधी: A person who helps another commit a crime or wrongdoing.  
- ***Synonyms***:  
   - **Noun:**  
    - *Partner in Crime:* Collaborator, conspirator, associate, accessory, aide, abettor  
_Example_:  
1. The thief was caught, but his **accomplice** managed to escape. *(Noun: partner in crime)*  

=====

```


## MIX

```JS
I will provide you with a word, phrase, or idiom. Generate a response strictly following the format and instructions below. Ensure accuracy, clarity, and adherence to the structural details.

 IF SINGLE MEANINGS :
### Phrase/Idiom/Phrasal Verb/ OWS
@@
[All applicable forms of Part of Speech] | हिंदी: [translation]  : [Concise English Meaning for the Term]
- ***Synonyms***: [2-6 most relevant direct synonyms or similar expressions]
_Example_ : [Provide one strong, contextual sentence showing primary usage.] *(Part of Speech: specific meaning hint)*

If necessary (e.g., for multiple meanings or forms), include an additional example to enhance clarity.

=====

HERE IS AN EXAMPLE RESULT THAT YOU NEED TO REPRODUCE IF SINGLE MEANINGS :

### PROXIMITY
@@
**Noun** | हिंदी: निकटता : The state of being near in space, time, or relationship.
- ***Synonyms***: Closeness, nearness, vicinity, adjacency, proximity
_Example_: The **proximity** of the coffee shop to the office made it a popular spot for afternoon breaks. *(Noun: state of being close or nearby)*

=====

IF MORE MULTIPLE MEANINGS  :

### Word/Phrase/Idiom
@@
**[Part of Speech 1, e.g., Noun]** | हिंदी: [Hindi Term 1a / Hindi Term 1b]; [Hindi Term 2] : [Concise English Meaning for Term 1a/1b]; [Concise English Meaning for Term 2].
**[Part of Speech 2, e.g., Verb]** | हिंदी: [Hindi Term 3]; [Hindi Term 4] : [Concise English Meaning for Term 3]; [Concise English Meaning for Term 4].
*(Use separate lines for each major Part of Speech. Use / between Hindi terms that are synonymous for the *same* specific meaning. Use ; to separate distinct Hindi terms corresponding to distinct English meanings listed in the same order after the colon.)*
- ***Synonyms***:
    - **[Part of Speech 1]:**
        - *[Meaning Hint 1]:* Synonym1, Synonym2, Synonym3
        - *[Meaning Hint 2]:* Synonym4, Synonym5
    - **[Part of Speech 2]:**
        - *[Meaning Hint 3]:* SynonymA, SynonymB
    *(Group synonyms by Part of Speech, then by specific meaning using an italicized meaning hint. List only English synonyms, separated by commas. Do not include Hindi here.)*
_Example_:
1.  [Example sentence with the **word/phrase** in bold]. *(Part of Speech: specific meaning hint)*
2.  [Second example sentence for a different meaning/POS]. *(Part of Speech: specific meaning hint)*
*(Provide at least one example sentence for each distinct meaning/POS* defined above. Ensure the word/phrase is bolded. The clarification in parentheses should state the Part of Speech and a brief English hint corresponding to the meaning being illustrated.)*

=====

HERE IS AN EXAMPLE RESULT THAT YOU NEED TO REPRODUCE:

### ACCOMPLICE
@@
**Noun** | हिंदी: सह-अपराधी: A person who helps another commit a crime or wrongdoing.
- ***Synonyms***:
    - **Noun:**
        - *Partner in Crime:* Collaborator, conspirator, associate, accessory, aide, abettor
_Example_:
1. The thief was caught, but his **accomplice** managed to escape. *(Noun: partner in crime)*

=====

NOTE : NEVER FORGET "=====" AT END .
And add 🌟 important word forms and *(Rare)* when the word is rare or obscure
RETURN IN SINGLE CODE BLOCK
IF YOU UNDERSTAND ALL ABOVE INSTRUCTIONS JUST SAY "Yes".

```

# lang


```
Analyze the user-provided article to enhance comprehension, vocabulary, and critical thinking for 10th graders. Follow this structure:  

---  

### 1. **Article Breakdown**  
   - Divide the article into **numbered sentences**.  
   - Format:  
     ```  
     1. [Sentence 1]  
     2. [Sentence 2]  
     ...  
     ```  

### 2. **Vocabulary, Idioms & Phrases**  
   - Identify **5–8 challenging terms per sentence** (prioritize grade-appropriate difficulty).  
   - For **each term**:  
     - **English Definition**: Simple, student-friendly explanation.  
     - **Hindi Translation**: हिंदी अर्थ (contextually accurate).  
     - **Idioms/Phrases**: Add literal meaning + contextual usage.  
   - Format:  
     ```  
     **Sentence [Number]**: [Original Sentence]  
       - **[Term]**: [Definition]. हिंदी अर्थ: [Translation].  
       - **[Idiom/Phrase]**: [Contextual Meaning]. Literal: [Explanation]. हिंदी अर्थ: [Translation].  
     ```  

### 3. **MCQs (5 Questions)**  
   - **Types**:  
     - 2x **Inference** (tone, purpose, implicit ideas).  
     - 1x **Vocabulary-in-Context**.  
     - 1x **Text Structure** (e.g., cause-effect, comparison).  
     - 1x **Textual Evidence** (identify support for a claim).  
   - **Rules**:  
     - Options **A–D** are distinct and plausible.  
     - Avoid trick questions.  
   - Format:  
     ```  
     **Q1.** [Question stem]  
       A. [Option]  
       B. [Option]  
       C. [Option]  
       D. [Option]  
     ```  

### 4. **Answer Key**  
   - Provide **correct answers** with **brief explanations** referencing article sentences.  
   - Format:  
     ```  
     1. **A** – [Explanation, e.g., "Supports the author’s argument in Sentence 3"].  
     2. **C** – [Explanation]  
     ...  
     ```  

**Notes**:  
- Use **bold** for key terms/questions.  
- Prioritize **Hindi translations** for terms absent in NCERT 10th-grade textbooks.  
- For idioms, **always clarify literal vs. contextual meanings**.  

```


```c
Analyze the provided article by:  
1. Splitting it into individual sentences.  
2. For each sentence:  
   - List difficult vocabulary, idioms, or phrases.  
   - Provide English meanings and Hindi translations for each.  
3. At last Create 5 moderate-to-hard MCQs (multiple-choice questions) testing comprehension, vocabulary, or inference.  
4. Include an answer key at the end.  

Return the analysis in a structured format without additional commentary. 

**Example Workflow:**  
- User provides article.  
- Your response:  
  **Sentence 1:** [Text]  
    - **Difficult Terms:**  
      - [Word/Phrase]: [Hindi Meaning] | [Clear, concise meaning with brief context in English]  
  **MCQs:**  
  1. [Question]  
     a) [Option]  
     b) [Option]  
     c) [Option]  
     d) [Option]

At the end :
**Answer Keys**  
   - Provide **correct answers** with **brief explanations** referencing article sentences .  

```


# CODING

```
Before proceeding, I’d like to prioritize a conversational approach to ensure clarity and accuracy. **Do not write code yet**—instead, let’s discuss the problem first.

1. **Clarifying Questions:** To avoid potential gaps or bugs, could you start by asking me any clarifying questions about the task, requirements, or edge cases I might have overlooked?
    
2. **Proposed Solution & Reasoning:** Once you have enough information, outline your approach to [X] in detail. Explain **why you believe this solution will work**, including potential risks, trade-offs, or alternatives. Wait for my approval before moving forward.
    
3. **Step-by-Step Execution Plan:** After I approve the approach, clearly summarize what you’ll do next. Break it down into concrete steps, confirm your understanding of the task, and ensure alignment with my goals. **Do not proceed without explicit confirmation.**
    

I’ll signal when I’m ready for you to generate code or implement changes.
```

