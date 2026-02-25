# My-Asus-ROG-Ally-Z1e
Anything I'll note worthy for my My-Asus-ROG-Ally-Z1e
=
Ryujinx Compatible Games CSV File:
https://play.clickhouse.com/play
````
SELECT
    -- Strips the Title ID and extra spaces to show just the Game Name
    trim(splitByString(' - ', issue_title)[1]) as game_name,
    extracted_game_id as game_id,
    extracted_status as status,
    issue_labels as labels
FROM (
    SELECT
        title as issue_title,
        extract(title, '[\dA-Fa-f]{16}') as extracted_game_id,
        arrayStringConcat(labels, ';') as issue_labels,
        replaceOne(arrayFirst(label -> startsWith(label, 'status-'), labels), 'status-', '') as extracted_status,
        number
    FROM
    (
        SELECT
            number,
            argMax(title, updated_at) as title,
            argMax(labels, updated_at) as labels,
            argMax(state, updated_at) as state
        FROM github_events
        WHERE (event_type = 'IssuesEvent' OR event_type = 'IssueCommentEvent')
            AND repo_name = 'Ryujinx/Ryujinx-Games-List'
        GROUP BY number
    )
    WHERE state = 'open' 
      AND number NOT IN [1, 8, 10, 12, 13, 16, 20, 21, 22, 23, 24, 26, 27, 28, 31, 32, 35, 37, 38, 40, 2419, 2420, 2421, 2422, 2423, 2424, 2425, 2426, 2427, 2428, 2429, 2430, 2431, 2432, 2433, 2434, 2435, 2436, 2437, 2438, 2439, 2440, 2441, 2442, 2443, 2444, 2445, 2944, 3529, 3530, 3722, 3738, 3793, 3827, 3947, 3967, 4024, 4043, 4071, 4088, 4096, 4316, 4338, 4387, 4475, 4488, 4517, 4585, 4588, 4591, 4592, 4595, 4597, 4617, 4630, 4637, 4682, 4717, 4742, 4766, 4768, 4769, 4771, 4772, 4796, 4803, 4805, 4806, 4807, 4808, 4840, 4883, 4891, 4912, 4925, 4926, 4955, 4957, 4978, 4979, 4980, 4987, 5011, 5012, 5019, 5020, 5036, 5049, 5052, 5063]
)
WHERE status IN ('ingame', 'playable')
ORDER BY 
    status ASC, 
    game_name ASC
LIMIT 100000
````
Labels:  
playable: The ideal state. High compatibility, good speed, and minimal to no bugs.  
ingame: The game passes the title screen but may have issues (crashes, bad audio, low FPS) that prevent a normal gameplay experience.
