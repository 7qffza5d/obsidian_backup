# Dashboard

## Schedule

| Project                                  | Session   | Status                                      | 
| ---------------------------------------- | --------- | ------------------------------------------- | 
| [[Project Athena\|Athena]]               | Monday    | <span class="status-active">Active</span>   | 
| [[Project Ogma - Trowch\|Ogma - Trowch]] | Friday | <span class="status-active">Active</span>   | 
| Ogma - Athena                            | Thursday  | <span class="status-active">Active</span>   | 
| [[Project Hephaestus\|Hephaestus]]       | Tuesday    | <span class="status-active">Active</span>   |  
| [[Project Daedalus\|Daedalus]]           | Saturday  | <span class="status-active">Active</span>   | 
| [[Project Cicero\|Cicero]]               | Someday   | <span class="status-dormant">Dormant</span> |  

## Active projects

### [[Project Athena]] : Path to Thailand Olympiad in Informatics

### Project Ogma - Athena : Path to Linguistics Olympiad

### [[Project Ogma - Trowch]] : Government-mandated NLP project

### [[Project Hephaestus]] : Personal blog website

### [[Project Daedalus]] : Personal blog writing

### [[Project Cicero]] : Path to talking coherently



## Journal calendar

```dataview
CALENDAR date
FROM "06 Journal"
WHERE type = "journal"
```

## Recent Journals
```dataview
TABLE date, activities, topics
FROM "06 Journal"
WHERE type = "journal"
SORT date DESC
LIMIT 7
```

## Activity distribution

```dataview
TABLE length(rows) AS "Days recorded"
FROM "06 Journal"
WHERE type = "journal"
FLATTEN activities AS activity
GROUP BY activity
SORT length(rows) DESC
```

## Topics visited

```dataview
TABLE length(rows) AS "Days recorded"
FROM "06 Journal"
WHERE type = "journal"
FLATTEN topics AS topic
GROUP BY topic
SORT length(rows) DESC
```

## Sleep Time

```dataview
TABLE
    date AS "Journal Date",
    sleep_start AS "Fell Asleep",
    sleep_end AS "Woke Up",
    round((sleep_end - sleep_start).hours, 2) AS "Hours Slept"
FROM "06 Journal"
WHERE type = "journal"
    AND sleep_start
    AND sleep_end
SORT date DESC
LIMIT 14
```

```dataview
TABLE WITHOUT ID
    round(average(rows.hours), 2) AS "Average Hours Slept"
FROM "06 Journal"
WHERE type = "journal"
    AND sleep_start
    AND sleep_end
    AND date >= date(today) - dur(6 days)
    AND date <= date(today)
FLATTEN (sleep_end - sleep_start).hours AS hours
GROUP BY true
```