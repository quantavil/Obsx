
# 📚 IBPS Clerk Daily Schedule & Todo List


## 🌅 Morning Routine (06:00 - 13:00)  
- [ ] **08:20 – 09:20**   | ➗ *#Math 1*       <span class="timer-p" id="uT0Eoso" data-dur="5" data-ts="1754404005">【⏳00:00:05 】</span> 
	- [ ] ratio -Q31; Ratio Pg -89    
	- [ ] SICI- Q:10 ;SI CI Pg-160   <span class="timer-p" id="uT0EhGp" data-dur="17" data-ts="1754403991">【⏳00:00:17 】</span> 
- [ ] **09:30 – 10:40**   | 📘 *#English 1*     
	- [ ] Web book pg 105  
- [ ] **10:40 – 11:50**    | 🧩 *#Reasoning Puzzle*        
	- [ ] Practice set 6 pg 28; PUZZLE set 3 -0
- [ ] **12:00 – 12:30**    | 📖 *#Vocab*                 
- [ ] **12:40 – 1:10**     | 🍔 *#Calculation*            
	- [ ] square 125
## 🌞 Afternoon Routine (13:00 - 19:20)
- [ ] **15:00 – 16:10** | ✖️ *#Math 2*    
	- [ ] missing num -230 ; simplification Q.90 ; 
	- [ ] Time&Dis Pg. 12; Time&Dis Q:50;
- [ ] **16:20 – 17:30** | 🧠 *#Reasoning 2*     
	- [ ] syllogism revision piyush 5:34 ;
- [ ] **18:00 – 19:00** | 📝 *#English 2*        
	- [ ] Pg.23
- [ ] **19:10 – 20:10** | 🧮 *#Extra*               
	- [ ] profit&loss- Q:8
- [ ] **19:10 – 20:10**



## Revisionboard

### Maths
- [x] Percentage - 19/07   ;   23/07

### Reasoning
 - [x] Coding Decoding - 09/07
 - [x] Inequality - 26/07
 - [x] coded inequality -26/07
 - [x] Blood relation - 25/07
 - [x] Order and Ranking -23/07
 - [x] Puzzle -26/07 
### English
- [x] Basic - 10/07
- [x] Pronoun - 25/07
- [ ] Adjective -


```dataviewjs
// 🎯 OPTIMIZED SMART DAILY STUDY SCHEDULE GENERATOR
// ================================================

const config = {
    startTime: "8:45",
    endTime: "22:59",
    autoBreakDuration: 10,
    
    fixedBreaks: [
        { name: "😴 Sleep", start: "00:00", end: "08:00" },
        { name: "🍳 Breakfast", start: "09:30", end: "10:00" },
        { name: "🍔 Lunch", start: "14:00", end: "15:00" },
        { name: "😴 Rest", start: "16:30", end: "17:00" },
        { name: "🍽️ Dinner", start: "20:30", end: "21:30" }
    ],
    
    subjects: [
        { name: "➗ Math Practice 1", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "📘 English 1", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "🧩 Reasoning Puzzle", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "📖 Vocab & Reading", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "➕ Math Practice 2", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "🧠 Reasoning Practice", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "🧮 Calculation Practice", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "📝 English 2", duration: 60, days: ["Mon","Tue","Wed","Thu","Fri","Sat","Sun"] },
        { name: "🎯 Mock Test", duration: 120, days: [""] },
        { name: "📚 General Knowledge", duration: 120, days: [""] }
    ]
};

// Utility functions
const timeToMinutes = timeStr => timeStr.split(':').reduce((h, m) => h * 60 + +m);
const minutesToTime = minutes => `${String(Math.floor(minutes / 60)).padStart(2, '0')}:${String(minutes % 60).padStart(2, '0')}`;
const getCurrentDay = () => ['Sun', 'Mon', 'Tue', 'Wed', 'Thu', 'Fri', 'Sat'][new Date().getDay()];

const generateDailySchedule = () => {
    const today = getCurrentDay();
    const todaySubjects = config.subjects.filter(s => s.days.includes(today));
    
    if (!todaySubjects.length) {
        return { success: false, message: `No subjects scheduled for ${today}`, schedule: [] };
    }
    
    // Create available time slots
    const [startMin, endMin] = [config.startTime, config.endTime].map(timeToMinutes);
    const activeBreaks = config.fixedBreaks
        .filter(b => timeToMinutes(b.end) > startMin && timeToMinutes(b.start) < endMin)
        .sort((a, b) => timeToMinutes(a.start) - timeToMinutes(b.start));
    
    const timeSlots = [];
    let currentTime = startMin;
    
    activeBreaks.forEach(breakItem => {
        const [breakStart, breakEnd] = [breakItem.start, breakItem.end].map(t => 
            Math.max(Math.min(timeToMinutes(t), endMin), startMin)
        );
        
        if (currentTime < breakStart) {
            timeSlots.push({ start: currentTime, duration: breakStart - currentTime });
        }
        currentTime = Math.max(currentTime, breakEnd);
    });
    
    if (currentTime < endMin) {
        timeSlots.push({ start: currentTime, duration: endMin - currentTime });
    }
    
    // Schedule subjects with auto breaks
    const scheduled = [];
    const unscheduled = [];
    const sortedSubjects = [...todaySubjects].sort((a, b) => b.duration - a.duration);
    
    sortedSubjects.forEach((subject, index) => {
        const isLast = index === sortedSubjects.length - 1;
        const totalNeeded = subject.duration + (isLast ? 0 : config.autoBreakDuration);
        
        const slotIndex = timeSlots.findIndex(slot => slot.duration >= totalNeeded) !== -1 ? 
            timeSlots.findIndex(slot => slot.duration >= totalNeeded) :
            timeSlots.findIndex(slot => slot.duration >= subject.duration);
        
        if (slotIndex !== -1) {
            const slot = timeSlots[slotIndex];
            
            scheduled.push({
                startTime: minutesToTime(slot.start),
                endTime: minutesToTime(slot.start + subject.duration),
                activity: subject.name,
                type: 'study'
            });
            
            const used = Math.min(totalNeeded, slot.duration);
            slot.start += used;
            slot.duration -= used;
            
            if (slot.duration === 0) timeSlots.splice(slotIndex, 1);
        } else {
            unscheduled.push(subject.name);
        }
    });
    
    // Combine with fixed breaks for display
    const breaks = config.fixedBreaks
        .filter(b => timeToMinutes(b.start) >= startMin)
        .map(b => ({ startTime: b.start, endTime: b.end, activity: b.name, type: 'break' }));
    
    const fullSchedule = [...scheduled, ...breaks]
        .sort((a, b) => timeToMinutes(a.startTime) - timeToMinutes(b.startTime));
    
    const [totalRequired, scheduledTime] = [
        todaySubjects.reduce((sum, s) => sum + s.duration, 0),
        scheduled.reduce((sum, s) => sum + timeToMinutes(s.endTime) - timeToMinutes(s.startTime), 0)
    ];
    
    return {
        success: true,
        message: `📅 Schedule generated for ${today}`,
        schedule: fullSchedule,
        stats: { totalRequired, scheduled: scheduledTime, unscheduled }
    };
};

// Display
const result = generateDailySchedule();
const today = getCurrentDay();
const formatTime = minutes => `${Math.floor(minutes/60)}h ${minutes%60}m`;

dv.header(2, "🎯 Smart Daily Study Schedule");
dv.paragraph(`**Today:** ${today} | **Study Period:** ${config.startTime} - ${config.endTime}`);
dv.paragraph(`**Auto Break:** ${config.autoBreakDuration} minutes after each study session (not shown in table)`);

if (!result.success) {
    dv.paragraph(`❌ **${result.message}**`);
} else {
    const { totalRequired, scheduled, unscheduled } = result.stats;
    
    dv.paragraph(`✅ **${result.message}**`);
    dv.paragraph(`📊 **Study Time:** ${formatTime(scheduled)} scheduled / ${formatTime(totalRequired)} required`);
    
    if (unscheduled.length) {
        dv.paragraph(`⚠️ **Unscheduled (${formatTime(totalRequired - scheduled)}):** ${unscheduled.join(', ')}`);
    }
    
    dv.table(
        ["⏰ Time", "📋 Activity", "📝 Type"],
        result.schedule.map(item => [
            `${item.startTime} – ${item.endTime}`,
            item.activity,
            item.type === 'study' ? '📚 Study' : '🍽️ Break'
        ])
    );
}
```


### 💡 Tips for Success

• ⏰ **Stick to the schedule** - consistency is key
• 🧘 **Take breaks seriously** - they help you focus better
• 📱 **Minimize distractions** during study sessions
• 💧 **Stay hydrated** throughout the day
• 🌙 **Get enough sleep** for better retention

