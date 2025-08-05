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
const file = dv.current().file.path;
app.vault.read(app.vault.getAbstractFileByPath(file)).then(content => {
    // Count ### headers
    const headerMatches = content.match(/^### /gm);
    const headerCount = headerMatches ? headerMatches.length : 0;
    
    // Count exactly 5 equals (=====)
    const fiveEqualsMatches = content.match(/^=====/gm);
    const fiveEqualsCount = fiveEqualsMatches ? fiveEqualsMatches.length : 0;
    
    dv.paragraph(`Headers (###): ${headerCount}`);
    dv.paragraph(`Correct separators (=====): ${fiveEqualsCount}`);
    
    if (headerCount === fiveEqualsCount) {
        dv.paragraph(`✅ **All ${headerCount} words have correct formatting!**`);
    } else {
        dv.paragraph(`❌ **Mismatch detected!** ${headerCount - fiveEqualsCount} words have incorrect formatting.`);
        
        // Find words with wrong separator count and show what they have
        const sections = content.split(/^### /gm).slice(1); // Remove empty first element
        const incorrectWords = [];
        
        sections.forEach(section => {
            const wordName = section.split(/\s/)[0].replace(/[🪐@@]/g, '').trim();
            
            // Check if section has exactly 5 equals at line start
            if (!section.match(/^=====/m)) {
                // Find what separator it actually has
                const equalsMatch = section.match(/^(=+)/m);
                const actualSeparator = equalsMatch ? equalsMatch[1] : 'NONE';
                const equalsCount = equalsMatch ? equalsMatch[1].length : 0;
                
                incorrectWords.push({
                    word: wordName,
                    found: actualSeparator,
                    count: equalsCount
                });
            }
        });
        
        if (incorrectWords.length > 0) {
            dv.paragraph(`**Words needing format correction:**`);
            incorrectWords.forEach(item => {
                if (item.count === 0) {
                    dv.paragraph(`- **${item.word}**: Missing separator (has: NONE, needs: =====)`);
                } else {
                    dv.paragraph(`- **${item.word}**: Wrong separator (has: ${item.found} [${item.count} equals], needs: =====)`);
                }
            });
        }
    }
});
```

```dataviewjs
/**
 * DUPLICATE HEADINGS FINDER - Optimized DataviewJS Script
 * ======================================================
 * 
 * Efficiently scans vault for duplicate headings with file exclusion support.
 * Normalizes headings (removes emojis, trims, lowercases) for accurate comparison.
 * 
 * CONFIGURATION: Edit EXCLUDED_FILES array below to skip specific files
 */

// ==========================================
// CONFIGURATION
// ==========================================
const EXCLUDED_FILES = new Set([
    'PRELIMS',
    'Rule Of Grammar'
]);

// ==========================================
// CORE FUNCTIONS
// ==========================================

/**
 * Normalize heading text for comparison
 */
const normalizeHeading = (text) => text.replace(/[\p{Emoji}]/gu, '').trim().toLowerCase();

// ==========================================
// MAIN EXECUTION
// ==========================================

const headingCounts = new Map();
const headingDetails = [];
let processedFiles = 0;
let excludedFiles = 0;

// Process each page in the vault
for (const page of dv.pages()) {
    const fileName = page.file.name;
    
    // Skip excluded files
    if (EXCLUDED_FILES.has(fileName)) {
        excludedFiles++;
        continue;
    }
    
    // Get headings from cache
    const cache = app.metadataCache.getCache(page.file.path);
    if (!cache?.headings) continue;
    
    processedFiles++;
    
    // Process each heading in the current file
    for (const heading of cache.headings) {
        const normalized = normalizeHeading(heading.heading);
        
        // Count occurrences of normalized heading
        headingCounts.set(normalized, (headingCounts.get(normalized) || 0) + 1);
        
        // Store heading details for later filtering
        headingDetails.push({
            original: heading.heading,
            normalized,
            file: fileName,
            path: page.file.path,
            level: heading.level,
            line: heading.position.start.line + 1
        });
    }
}

// Filter to only duplicate headings and sort them
const duplicateHeadings = headingDetails
    .filter(h => headingCounts.get(h.normalized) > 1)
    .sort((a, b) => {
        const normalizedCompare = a.normalized.localeCompare(b.normalized);
        return normalizedCompare !== 0 ? normalizedCompare : a.path.localeCompare(b.path);
    });

const uniqueDuplicates = [...headingCounts.entries()].filter(([_, count]) => count > 1).length;

// ==========================================
// RESULTS DISPLAY
// ==========================================

dv.header(2, "🔍 Duplicate Headings Analysis");

// Summary statistics
dv.paragraph(`**Files processed:** ${processedFiles} | **Excluded:** ${excludedFiles} | **Total headings:** ${headingDetails.length}`);
dv.paragraph(`**Unique duplicates found:** ${uniqueDuplicates}`);

// Display results table or success message
if (duplicateHeadings.length > 0) {
    dv.table(
        ["Heading", "File", "Level", "Line", "Count"],
        duplicateHeadings.map(h => [
            h.original,
            `[[${h.file.replace('.md', '')}]]`,
            `H${h.level}`,
            h.line,
            headingCounts.get(h.normalized)
        ])
    );
} else {
    dv.paragraph("✅ **No duplicate headings found!**");
}
```


---
PLUNDER

