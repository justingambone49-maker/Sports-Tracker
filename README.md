AI WAS USED FOR DEBUGGING COMMENTS API EXPANDING AND README
Sports Score Tracker — v21
─────────────────────────────────────────────────────────────────────────────

WHAT THIS CODE DOES:

* Real-time sports game tracking across American sports, soccer leagues, cups, and international competitions
* Fetches live game data from ESPN API with score updates, team records, and game status
* Displays popup notifications on screen for new games, score changes, and major plays
* Labels score changes by sport, including goals, touchdowns, home runs, and baskets
* Maintains live game dashboard GUI showing all tracked games with scores and team info
* Tracks game state transitions (upcoming → live → final) with event detection
* Alerts when a score is removed or overturned, and names final winners including shootouts
* Caches team logos for efficient display in popups and dashboard
* Applies color themes and accents for each sport for visual distinction
* Parses ESPN HTML/JSON to extract game data including period/inning, team records, game IDs
* Manages polling thread that continuously fetches fresh game data at configurable intervals
* Handles user configuration (API keys, custom teams, disabled sports, team removal)
* Displays daily recap of completed games from yesterday and today for favorite teams
* Supports team customization with custom team names and removal of default teams
* Screen flashing effects for major game events to grab attention
* Popup pause/resume functionality via keyboard (hold Enter 3 seconds)
* Keyboard shortcuts for dashboard (Ctrl+U) and settings (Ctrl+S)
* Runs sanity tests on startup to verify game tracking logic works correctly
* Graceful shutdown with cleanup of threads, windows, and configuration saving

VERSION HISTORY  (V1–V17 were not written down at the time; they are reconstructed from how the app grew)
─────────────────────────────────────────────────────────────────────────────
V21  ∙ SEASON PAGE     — week and day separators (week numbers where ESPN has them) and both teams' logos on every game row
     ∙ TEAM PAGES      — Players tab (click a player for season + career stats) and Team stats tab; game windows get a Players (box score) tab
     ∙ WATCHING        — mark a game 📺 Watching: no alerts of any kind, score / plays / stats hidden until you stop watching
     ∙ SITUATION       — the pinned scoreboard shows the last play, down & distance / red zone, count & runners, power play; plays show where they happened
     ∙ TIDY WINDOWS    — game / team / player windows close themselves 20 s after you click back to the main page
     ∙ COPY & PASTE    — Ctrl+A / Ctrl+C on any table or text, or "Copy all" on a page; tables paste as tab-separated text
     ∙ SAFER TESTS     — the startup self-tests run in a sandbox: your settings, files and webhook are never touched or used
     ∙ PHONE LOG       — the Log says why a phone / webhook alert was NOT sent; play text no longer shows stray "( , )"
V20  ∙ EVERY ESPN LEAGUE  — ~150 more leagues (and whatever ESPN itself lists, remembered between runs) on the Sports page: all ticked, in
                        sections with a search box; smaller leagues are checked gently so ESPN is never hammered
     ∙ SEASON TAB     — pick a league and scroll one list of all its games: future above, past below; click any game
     ∙ STEADY POPUPS    — a notification keeps its spot until it disappears (the spot is then reused); reboot opens only the dashboard;
                        closing the dashboard quits the whole app again
     ∙ TEAM PAGES      — click a team in the standings: logo, record, place in its division, every game this season; click a
                        result for its play-by-play. Upcoming-game windows show each team's last five results
     ∙ ONE SETTINGS WINDOW — every setting is a tab in one list; Sport Order tab sets the order sports are listed in, and
                        every list now has one fixed order (it no longer shuffles between refreshes)
     ∙ PLAYOFF PICTURE — brackets that needed ESPN bracket data (cups, real playoffs) are gone; the projected bracket is built from standings
     ∙ STANDINGS COLORS — playoff leagues: green = in playoff position; no-playoff leagues: gold champion + Champions League / Europa /
                        Conference / relegation
     ∙ LOGOS + CFL      — CPL / PWHL / Canadian Championship logos are looked up and cached from boot (with a crest-badge fallback);
                        the CFL left ESPN for TSN, so it now reads TSN's Bell Media feed and keeps refreshing while games are on
     ∙ POP-OUTS        — closing the dashboard hides it and closes every pop-out window (game windows, My Teams, Settings,
                        pinned scoreboard) for good; the mouse wheel scrolls every page; Canadian Championship via FotMob (opt-in)
     ∙ SCORING PLAYS  — score popups show the play ("J. Sayin pass to C. Tate for 9 yds, for a TD"); only when ESPN's
                        running score proves it is the play that moved the score, with look-back through recent plays
     ∙ ONE POPUP      — every score makes exactly one popup; a late scoring play or a football extra point / 2-pt try
                        UPDATES it in place (TOUCHDOWN -> TD + EXTRA PT) instead of adding more
     ∙ GAME WINDOW    — click a game: logos, score, scoring summary (who scored, when), team stats (possession, % as
                        percents) and play-by-play / match commentary; opens only when fully loaded
     ∙ FINAL SCORES   — after a game ends the final is double-checked against ESPN's game summary and play list for 15
                        minutes, so a goal in the last seconds is never missing from the scoreboard
     ∙ STANDINGS      — division / conference / one table, Wild Card section, full-row highlights (gold champion, blue
                        Champions League, green Europa, yellow Conference, red relegation), legend
     ∙ BRACKETS       — cups, playoffs, and "if the season ended today" projections for NFL / NBA / NHL / MLB
     ∙ NEW LEAGUES    — PWHL (HockeyTech) and the Canadian Premier League (Canada Soccer API)
     ∙ SHOOTOUTS      — shootout goals pop up; penalty kicks are labelled PENALTY GOAL
     ∙ SMOOTH UPDATES — the dashboard is never cleared: unchanged cards stay, changed ones are swapped in place; a
                        failed ESPN refresh keeps the last good data
     ∙ DAY WINDOWS    — Final tab = yesterday + today, Upcoming = today (adjustable); optional 'my teams, next 7 days'
V19  ∙ CUSTOMIZE      — Settings -> Customize: ~245 options (window colors, fonts, popup-card look, per-sport and
                        per-team colors, alert wording, timings) from one add_option(...) registry, with reset / export / import
     ∙ ALERTS         — snooze + quiet hours, game-starting-soon, close-game alerts, per-team alert levels
     ∙ DASHBOARD      — notification history, spoiler mode, pinned mini scoreboard, standings tab
     ∙ PHONE          — ntfy / Discord / Telegram / webhook alerts; start with Windows
V18  ∙ NWSL added; sports registry (add_sport) and favorite teams list; green dot / popup corner placement;
       always-on-top fixes; click a popup to dismiss it; MLB parsing fix; score-reversal alerts; shootout-aware finals
V17  ∙ Startup self-tests with a pass/fail popup; sturdier network handling (timeouts, de-duplicated plays)
V16  ∙ College football, CFL, NLL and the Canadian leagues
V15  ∙ Daily recap popup, Log tab, keyboard shortcuts, hold Enter to pause popups
V14  ∙ Team records and venues on cards, My Teams window and schedule tab
V13  ∙ Overturned-score (VAR / flag) alerts and shootout handling in finals
V12  ∙ Choice of monitor; popups stack neatly
V11  ∙ Soccer: MLS, Premier League, La Liga, Bundesliga, Ligue 1, Champions League and cups
V10  ∙ Period alerts (end of quarter / period, halftime, overtime) and game-started alerts
V9   ∙ Settings window: sports on/off, favorite teams, polling speed; settings saved to a file
V8   ∙ Favorite teams: longer popups, highlighted cards, screen-edge flash
V7   ∙ Team logos and card-style popups with fade in / out
V6   ∙ Green status dot with a live-game count; click it to open the dashboard
V5   ∙ Dashboard window with Live / Upcoming / Final tabs
V4   ∙ NBA, MLB and NHL; score labels per sport (goal, home run, basket)
V3   ∙ Game states (upcoming / live / final) and final-score alerts
V2   ∙ First on-screen popups for score changes (touchdown / field goal)
V1   ∙ The basics: poll ESPN's NFL scoreboard and print score changes to the console
