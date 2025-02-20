```dataviewjs
// DataviewJS To-Do List Script with Emojis (Shortened)

// Get the current day of the week
const today = new Date().toLocaleString("en-US", { weekday: "long" });

// Task presets: common tasks and specific tasks for each day
const tasks = {
    common: [
        { task: "🧮 Calculation practice", time: "1 hr", days: ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"] },
        { task: "📖 Vocab & Reading", time: "1.5 hrs", days: ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday"] },
        { task: "📝 Daily Mock", time: "1.5 hrs", days: ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"] }
    ],
    specific: {
        Monday: [
            { task: "📐 Math Basic", time: "1.5 hrs" },
            { task: "🧠 Reasoning", time: "1.5 hrs" }
        ],
        Tuesday: [
            { task: "🧠 Reasoning", time: "1.5 hrs" },
            { task: "📘 English", time: "1.5 hrs" }
        ],
        Wednesday: [
            { task: "📐 Math Basic", time: "1.5 hrs" },
            { task: "📘 English", time: "1.5 hrs" }
        ],
        Thursday: [
            { task: "📐 Math Basic", time: "1.5 hrs" },
            { task: "🧠 Reasoning", time: "1.5 hrs" }
        ],
        Friday: [
            { task: "🧠 Reasoning", time: "1.5 hrs" },
            { task: "📘 English", time: "1.5 hrs" }
        ],
        Saturday: [
            { task: "📐 Math Basic", time: "1.5 hrs" },
            { task: "📘 English", time: "1.5 hrs" }
        ],
        Sunday: [
            { task: "🔄 Revision", time: "3 hrs" }
        ]
    }
};

// Combine common and specific tasks for today
const getTasksForDay = (day) => [
    ...tasks.common.filter(task => task.days.includes(day)),
    ...(tasks.specific[day] || [])
];

// Render tasks for today
const renderTasks = (day) => {
    const dayTasks = getTasksForDay(day);
    dv.header(6, `Tasks for ${day}`);
    if (dayTasks.length) {
        dayTasks.forEach(task => dv.paragraph(`${task.task} (*${task.time}*)`));
    } else {
        dv.paragraph("Enjoy your day off!");
    }
};

// Render today's tasks
renderTasks(today);

```


# English 

## Vocab 

 **Daily Vocabulary Practice**: First, watch the entire video within 45 minutes and take note of all the words in a notepad. Then, in the next 45 minutes, add those unique words to your notes.



##  Grammar 


## **SBI Clerk Prelims Topic wise Weightage - English Language**

|                               |                                         |                                         |                                         |                                         |                                         |
| ----------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| **Topics**                    | **SBI Clerk Topic Wise Weightage 2023** | **SBI Clerk Topic Wise Weightage 2022** | **SBI Clerk topic wise Weightage 2021** | **SBI Clerk topic wise Weightage 2020** | **SBI Clerk topic wise Weightage 2019** |
| Reading Comprehension         | 8-10                                    | 7-10                                    | 7-8                                     | 9-10                                    | 8-10                                    |
| Error Detection               | 3-7                                     | 4-5                                     | 4-6                                     | 5                                       | 5-7                                     |
| Misspelt                      | 3-5                                     | 0-5                                     | 0-6                                     | 2-5                                     | 0-5                                     |
| Para Jumbles                  | 4-5                                     | 0-5                                     | 0-5                                     | -                                       | -                                       |
| Fillers                       | 3-5                                     | 0-5                                     | 0-4                                     | 3-5                                     | 0-5                                     |
| Sentence Improvement          | -                                       | 3-5                                     | 0-4                                     | 0-5                                     | 0-5                                     |
| Word Swap/ Word Rearrangement | 1-5                                     | 4-5                                     | 0-5                                     | -                                       | -                                       |
| Phrase Replacement            | 4-5                                     | 0-5                                     | 2-6                                     | -                                       | -                                       |
| Cloze Test                    | 5-6                                     | 0-7                                     | 5-8                                     | 5-6                                     | 0-5                                     |
| Sentence Rearrangement        | 3-5                                     | 0-5                                     | -                                       | 0-5                                     | 0-5                                     |
| Word Usage                    | 2-5                                     | 0-5                                     | 0-2                                     | 0-5                                     | -                                       |
| Column Based                  | 1-2                                     | -                                       | -                                       | -                                       | -                                       |

# Math

## Calculation ( 60 mins)

12- 29 Table : 10 mins
Square and cube : 10 mins
Fractions : 5 mins
Add,Sub,Mult,Div etc Practice  : 35 mins

## **SBI Clerk Prelims Topic wise Weightage - Quantitative Aptitude**

|                              |                                         |                                         |                                         |                                         |                                         |
| ---------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| **Topics**                   | **SBI Clerk Topic Wise Weightage 2023** | **SBI Clerk Topic Wise Weightage 2022** | **SBI Clerk topic wise Weightage 2021** | **SBI Clerk topic wise Weightage 2020** | **SBI Clerk topic wise Weightage 2019** |
| Data Interpretation          | 5-9                                     | 5                                       | 5                                       | 5-6                                     | 0-5                                     |
| Caselets                     | -                                       | 0-5                                     | 0-5                                     | 0-5                                     | -                                       |
| Missing Number Series        | 5                                       | 0-5                                     | 0-5                                     | 0-5                                     | -                                       |
| Wrong Number Series          | 5-6                                     | 0-5                                     | 0-5                                     | 0-5                                     | 0-5                                     |
| Arithmetic                   | 7-15                                    | 10-12                                   | 8-13                                    | 9-10                                    | 8-10                                    |
| Simplification/Approximation | 9-15                                    | 10-15                                   | 10-13                                   | 10                                      | 10-12                                   |
| Q1, Q2                       | -                                       | -                                       | 2-4                                     | -                                       | -                                       |
| Quadratic Equation           | -                                       | 0-6                                     | 0-2                                     | 0-5                                     | 0-5                                     |
# Reasoning 


## **SBI Clerk Prelims Topic wise Weightage - Reasoning Ability**

|                                   |                                         |                                         |                                         |                                         |                                         |
| --------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- | --------------------------------------- |
| **Topics**                        | **SBI Clerk Topic Wise Weightage 2023** | **SBI Clerk Topic Wise Weightage 2022** | **SBI Clerk topic wise Weightage 2021** | **SBI Clerk topic wise Weightage 2020** | **SBI Clerk topic wise Weightage 2019** |
| Puzzle And Seating Arrangement    | 15-23                                   | 13-21                                   | 12-23                                   | 15-20                                   | 15-23                                   |
| Syllogism                         | 2-5                                     | 2-4                                     | 0-3                                     | 3-4                                     | 4-5                                     |
| Inequality                        | 3-5                                     | 3-5                                     | 2-5                                     | 3-5                                     | -                                       |
| Coding Decoding                   | 4-5                                     | 0-5                                     | 0-5                                     | 0-5                                     | 0-5                                     |
| Alphanumeric Series               | 5                                       | 0-5                                     | 4-5                                     | 3-5                                     | 0-5                                     |
| Direction                         | 1-3                                     | 1-3                                     | 2-3                                     | 3-5                                     | 0-3                                     |
| Blood Relation                    | 2-4                                     | 3-4                                     | 0-2                                     | 0-3                                     | 2-4                                     |
| Order & Ranking                   | 2-3                                     | -                                       | -                                       | 0-3                                     | -                                       |
| Alphabet Series / Number Sequence | 1-5                                     | -                                       | -                                       | -                                       | -                                       |
| Miscellaneous                     | 1-5                                     | 1-4                                     | 1-3                                     | 2-5                                     | 0-5                                     |


---



