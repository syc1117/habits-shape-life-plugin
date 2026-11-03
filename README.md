# Habits Shape Life for Claude

Ask Claude about your own Habits Shape Life records. This plugin connects Claude to the Habits Shape Life remote MCP server and adds skills that explain how to read the records correctly and how to analyze them: calorie balance and weight trends, and reviews of a week or month compared with the period before.

## What it connects to

| Component         | Details                                                                                                           |
| ----------------- | ----------------------------------------------------------------------------------------------------------------- |
| Remote MCP server | `https://habit-shape-life.pages.dev/mcp` (Streamable HTTP, OAuth 2.1 sign-in with your Habits Shape Life account) |
| Skills            | Instructions only, no scripts (see below)                                                                         |

The plugin runs no local programs, hooks or scripts. It sends nothing on its own; Claude calls the server's tools only when you ask about your records.

## Set up

1. Install the plugin, then open its **Connectors** tab and connect **Habits Shape Life**.
2. Sign in with the account you use in the Habits Shape Life app (Google, Apple or Kakao).
3. The consent page lists everything that will be shared (meals, workouts, routines, body weight, health-app summaries, desired-self directions, goals and notes). Tick the single agreement box and allow sharing. You can narrow it later under Connected AI.
4. Ask a question, for example "How consistently did I train this month?"

You need a Habits Shape Life account with synchronized records. The connector works in Claude chat on the web, desktop and mobile apps, and in Cowork. Claude Code is not supported yet.

## Skills

| Skill                             | When Claude uses it                                                                                                           |
| --------------------------------- | ----------------------------------------------------------------------------------------------------------------------------- |
| `skills/habit-records/SKILL.md`   | Any question about the records: which tool to call, units, missing data, sharing scope                                        |
| `skills/calorie-balance/SKILL.md` | Losing, gaining or keeping weight: intake, estimated maintenance calories, weight trend and daily targets, every number shown |
| `skills/weekly-review/SKILL.md`   | Reviewing a week, month or other period against the period before across meals, workouts and routines                         |

## Tools

All tools are read-only.

| Tool                   | What it reads                                               |
| ---------------------- | ----------------------------------------------------------- |
| `get_record_summary`   | Overview of the selected period                             |
| `get_nutrition_trends` | Meals, calories, macronutrients and, if shared, body weight |
| `get_workout_trends`   | Strength sets, volume, maximum weight and cardio            |
| `get_routine_trends`   | Completed, missed and open routines                         |
| `list_records`         | Individual records, up to 100 per page                      |
| `get_goals`            | Desired-self directions and goals, if shared                |

There are no tools that create, edit or delete records, make purchases or show advertising.

## Privacy

- Claude receives only the categories you allowed, from your own account. The server checks your current permission on every call.
- Habits Shape Life does not store your Claude conversations. It keeps an access log of which tool was called and whether it succeeded, for security.
- Disconnect or narrow the scope in Habits Shape Life settings under **Connected AI**. Reads stop immediately. Conversations that already include your records are handled under your Claude settings.
- Privacy policy: https://habit-shape-life.pages.dev/en/privacy/

## Troubleshooting

| Symptom                                            | What to do                                                                                                 |
| -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| "Not shared" for weight, health summaries or goals | The scope was narrowed in Connected AI. Disconnect and reconnect from Claude to share every category again |
| Sign-in fails or tools return `unauthenticated`    | Reconnect the connector. If you revoked the connection in Habits Shape Life, a new sign-in is required     |
| Empty results                                      | Check that the app has synchronized and that the period and time zone are correct                          |
| "Quota exceeded"                                   | Ask for a shorter period                                                                                   |

Support: https://habit-shape-life.pages.dev/en/about/
