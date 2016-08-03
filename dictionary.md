# 字典

### User

| 字段  | 类型  |  可填  |
|---|---|---|---|---|
|sex| Number | 1, 男性 <br> 2, 女性 <br> 0, 无 |

### Tournament

| 字段  | 类型  |  可填  |
|---|---|---|
|state|String|'upcoming', <br> 'ongoing', <br> 'completed'|

### SubTournament

| 字段  | 类型  |  可填  |
|---|---|---|
|state| String | 'preSigningUp', <br> 'signingUp', <br> 'signingUpDue', <br> 'orderReleased', <br>'groupOngoing', <br> 'groupCompleted', <br>'eliminationOngoing', 'subTournamentCompleted' |
|tournamentSys| String | 'groupElimination', <br> 'elimination', <br> 'bigTeamGroupElimination' |

### Match

| 字段  | 类型  |  可填  |
|---|---|---|
|scoringSys| Number | 11, 15, 21 |
|bestOf| Number | 1, 3, 5 |
|discipline| String | 'ms', <br> 'md', <br> 'ws', <br> 'wd', <br> 'xd', <br> 's', <br> 'd' |

### Game

| 字段  | 类型  |  可填  |
|---|---|---|
|unfinished| String | 'withdrawal' |
