# Birdie 后端接口

### User

 属性

| name  | type  |  explanation  | required | unique  |
|---|---|---|---|---|
|  id | String  |   |  y | y  |
|  username | String  | 用作登录名  |  y |  y |
|  password | String  | 密码  |  y |  n |
|  realname | String  | 真实姓名  |  y |  n |
|  phoneNumber | String  | 手机号  |  y |  y |
|  phoneNumberVerified | Boolean  | 手机号是否验证过  | y  | n  |
|  sex | Number  | 性别，1，男，2，女  | y  | n  |
|  headimgurl | String  | 用户头像URL  | y  |  n |
|  birthday | Number  | 生日时间戳  | y  | n  |
|  createdAt | Number  | 创建时间戳  | y  | n  |
|  updatedAt | Number  | 更新时间戳  | y  | n  |

接口

| name  | required params  |  optional params  | explanation | return  |
|---|---|---|---|---|
| getAllUsers  | userId (String)  |    | 排除用户自己的所有用户 | type: Array <br> |
| getUserByIds  | userIds (Array)  |    | 批量根据userId获取用户 | type: Array <br> |


### Doubles

属性

| name  | type  |  explanation  | required | unique  |
|---|---|---|---|---|
|  id | String  | 主键  |  y | y  |
|  players | relation  | 关联两个不同的用户  |  y | y  |
|  name | String  | 双打队伍名  |  n | n  |
|  createdAt | Number  | 创建时间戳  | y  | n  |
|  updatedAt | Number  | 更新时间戳  | y  | n  |

接口

| name  | required params  |  optional params  | explanation | return  |
|---|---|---|---|---|
| getMyDoubles  | userId (String)  |    | 获取我的所有队伍 | type: Array |

### Tournament

属性

| name  | type  |  explanation  | required | unique  |
|---|---|---|---|---|
|  id | String  | 主键  |  y | y  |
|  name | String  | 赛事名  |  y | n  |
|  subTournament | relates to subTournament  | 关联子赛事  |  y | y  |
|  location | String  | 地点  |  y | n  |
|  state | String  | 赛事状态  |  y | n  |
|  description | String  | 赛事描述  |  y | n  |
|  chairUmpire | 关联User  | 主裁判  |  y | n  |
|  startAt | Number  | 赛事开始时间戳  |  y | n  |
|  createdAt | Number  | 创建时间戳  | y  | n  |
|  updatedAt | Number  | 更新时间戳  | y  | n  |

接口

| name  | required params  |  optional params  | explanation | return  |
|---|---|---|---|---|
| create  | name, location, startAt, description, subTournaments (Array), chairUmpirePhone (String)  |    | 创建赛事，包括子赛事 | type: Boolean |
| get  |   |    | 获取所有赛事及子赛事 | type: Array |

### Match

| name  | type  |  explanation  | required | unique  |
|---|---|---|---|---|
|  id | String  | 主键  |  y | y  |
|  umpire | relates to User  | 裁判  |  y | n  |
|  players | relates to User  | 单打双方选手  |  y | n  |
|  doubles | relates to Doubles  | 双打双方选手  |  y | n  |
|  bestOf | Number  | 最多打的局数  |  y | n  |
|  scoringSys | Number  | 得分制, 21分，11分，15分  |  y | n  |
|  discipline | String  | 项目，ms男单等  |  y | n  |
|  subTournament | relates to subTournament  | 关联到子赛事  |  y | n  |
|  scores | Array  | 双方比分（大比分）  |  y | n  |
|  duration | Number  | 持续时间(秒)  |  y | n  |
|  winner | relates to User  | 胜者  |  y | n  |


### SubTournament

属性

| name  | type  |  explanation  | required | unique  |
|---|---|---|---|---|
|  id | String  | 主键  |  y | y  |
|  tournament | relates to Tournament  | 外键  |  y | n |
|  name | String  | 子赛事名  |  y | n  |
|  description | String  | 描述  |  y | n  |
|  tournamentSys | String  | 子赛事赛制  |  y | n  |
|  signUpMembers | relates to User or Doubles or Team  | 报名成员  |  y | n  |
|  umpires | relates to User  | 裁判  |  y | n  |
|  members | relates to User or Doubles or Team  | 参赛成员  |  y | n  |
|  state | String  | 状态  |  y | n  |
|  createdAt | Number  | 创建时间戳  | y  | n  |
|  updatedAt | Number  | 更新时间戳  | y  | n  |

接口

| name  | required params  |  optional params  | explanation | return  |
|---|---|---|---|---|
| signUp  | signUpId (userId or doublesId or teamId)|    | 报名比赛 | type: Boolean |
| getMyUmpiredSubTournaments  | userId |    | 获取我作为裁判的赛事及子赛事 | type: Array |
| changeSubTournamentState  | subTournamentId <br> state(String) |    | 更改子赛事状态 | type: Boolean |
