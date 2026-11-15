# sportst

**A terminal scoreboard for the NFL, college football, the NBA, the WNBA, men's and women's college basketball, the NHL, the AHL, MLB, Minor League Baseball, NCAA Division I college baseball and softball, and the Winter and Summer Olympics.** It runs on Linux, macOS and Windows.

Scoreboard, scouting reports, box scores, every team's season stats, plays, standings, brackets, betting lines with sportst's own value picks, and favorites over ESPN's public API, the AHL's own HockeyTech feed, MLB's own Stats API for the minor leagues, and Wikipedia for the Olympic sports ESPN does not cover - with the NHL's and MLB's own stats APIs and NCAA.com filling in the team numbers ESPN does not publish, and Action Network and Kalshi supplying every sportsbook's line.

Pick any scoring play on the Plays tab and hear its clip, with the broadcast call, right in the terminal - from ESPN's and MLB's free clips, the NHL's goal clips, and the NFL's and AHL's own YouTube channels.

Hockey (NHL and AHL) goes deepest: pick any player in a box score for his card - his photo, who he is, his game, his season and his last games - see a game's flow, its three stars and every shot on the rink, pick a goal for where it came from and the goalie it beat, and see the bracket the standings would make today.

It opens on an Overview of your favorite teams - each one's latest result and next game under a retro SPORTS TERMINAL title - with every league's games today underneath: live now, coming up, final. Pick any team in the standings for its team page: the whole season game by game beside a dashboard of it - every game's margin as a bar chart, the next game with its line, the division race, the season's splits, a report card and the road ahead. Press Z on any game for the Game Center, a full-screen live scoreboard drawn for its sport - the football field, the baseball diamond, the basketball court with every shot, the hockey rink with every shot on goal, the soccer match timeline - with win probability and the last plays; on an Olympic event, the podium. A BottomLine ticker pages through the day's scores while you work, a live wire crawls above it while a league's games are on - every goal and power play, every run and big night, every touchdown - as it happens, your teams' scores flash on the bottom line, and the mouse works too: click a tab, a game or a team, scroll with the wheel. A Settings tab changes every option, shows how every data source is doing, and lists every key. In Kitty or Ghostty the title is a real picture and the real team logos run down every list.

One Python file with no dependencies: the standard library only.

Free and open source under the MIT License. sportst is an independent hobby project, not affiliated with or endorsed by ESPN, any league, team or network, or any of its data sources; their names and logos belong to their owners. See section 23 for the license and disclaimers.

## Quick start

You need Linux, macOS or Windows 10 or 11, Python 3.9 or newer, and a terminal with UTF-8 and 256 colours. Nothing else - sportst is one Python file that uses only the standard library. (Windows: section 2, "On Windows".)

```bash
# get it: clone this repository, or download just the sportst file from it
git clone <this repository's URL>      # the green "Code" button on GitHub copies it
cd sportst

# install it for your user
mkdir -p ~/.local/bin
cp sportst ~/.local/bin/sportst
chmod +x ~/.local/bin/sportst

# run it
sportst --version
sportst
```

If your shell says `command not found`, `~/.local/bin` is not on your `PATH` yet - section 2 covers that, along with upgrading and uninstalling. To hear clips of scoring plays in the terminal, also install a media player such as mpv (`sudo apt install mpv` on Debian, Ubuntu or Mint). It is optional; without one, clips open in your browser.

### Your own settings

The repository ships with no one's settings and no favourite teams. sportst keeps yours in `~/.config/sportst/config.json` (or `$XDG_CONFIG_HOME/sportst/`), which it creates the first time you change something. There are three ways to set it up:

- **In the app.** Press `0` for the Favorites tab and star your teams (`L` switches league). Press `O` for the Settings tab: pick a group (General, Display ...) and enter opens its card with every option in it, its default and what it does, saved the moment you change it.
- **From a template.** `sportst --write-config` writes a config file with every setting at its default, ready to edit.
- **For one run.** `sportst -L nhl` opens a league, `sportst --config path/to/other.json` uses another config file.

A config file only needs the keys you want to change; anything it leaves out uses the default. Section 17 lists every key. Cached logos, pages and saved betting lines go in `~/.cache/sportst/`; nothing else is written anywhere, and no account or API key is needed for any of the data sources.

| Overview | Scoreboard | Game Center (Z): basketball |
| --- | --- | --- |
| ![The Overview tab: your teams' latest results and next games, and today's games across every sport](screenshots/01-overview.png) | ![The NFL Scoreboard beside a game's closing line](screenshots/02-scoreboard.png) | ![The Game Center: a finished NBA game with each team's shots and the win probability](screenshots/03-game-center-basketball.png) |

| Game Center (Z): hockey | A team's page | Standings |
| --- | --- | --- |
| ![The Game Center: a finished NHL game with every shot on goal, the goalies and the goals](screenshots/04-game-center-hockey.png) | ![A team's page: the season game by game beside its dashboard](screenshots/05-team-page.png) | ![The NFL standings by division](screenshots/06-standings.png) |

| Scouting report | Plays: shot chart | Plays: pitch by pitch |
| --- | --- | --- |
| ![A scouting report: the matchup's stat edges beside each team's leaders, injuries and news](screenshots/07-scouting-report.png) | ![The Plays tab: scoring plays with clips beside the basketball shot chart](screenshots/08-plays-shot-chart.png) | ![The Plays tab: an MLB at-bat pitch by pitch with the strike zone](screenshots/09-plays-pitch-by-pitch.png) |

| Team stats | Playoffs and championship odds | Betting |
| --- | --- | --- |
| ![NFL team stats by division](screenshots/10-team-stats.png) | ![The MLB playoff bracket beside the championship odds](screenshots/11-playoffs-bracket-and-odds.png) | ![The Betting tab: value picks, every sportsbook's line and sportst's read](screenshots/12-betting.png) |

| Ask Kim ($) | Olympics: Event Center | Calendar (C) |
| --- | --- | --- |
| ![Ask Kim: the week's three best bets in a speech bubble](screenshots/13-ask-kim.png) | ![The Event Center: the podium and results of an Olympic downhill](screenshots/14-olympics-event-center.png) | ![The pop-out calendar over the Scoreboard](screenshots/15-calendar.png) |

| Hockey's rink and game flow (7.0.0) | Baseball's diamond and strike zone (7.0.0) | Basketball's court (7.0.0) |
| --- | --- | --- |
| ![The NHL's Plays tab: every shot on the rink, the game flow as a line chart](screenshots/plays-hockey-rink.png) | ![MLB's Plays tab: the diamond, the count and the strike zone](screenshots/plays-baseball-diamond.png) | ![The NBA's Plays tab: every shot on the court](screenshots/plays-basketball-court.png) |

| The WNBA's Game Center (7.0.0) | The College World Series (7.0.0) | Minor League Baseball (7.0.0) |
| --- | --- | --- |
| ![A WNBA game in the Game Center](screenshots/game-center-wnba.png) | ![The Men's College World Series as its two double-elimination brackets](screenshots/playoffs-college-world-series.png) | ![A Triple-A game's Plays tab](screenshots/plays-minor-league.png) |


## Contents

1. [What it does](#1-what-it-does)
2. [Install](#2-install)
3. [The leagues](#3-the-leagues)
4. [The league picker](#4-the-league-picker)
5. [The Olympics](#5-the-olympics)
6. [The screens](#6-the-screens)
7. [Scouting reports](#7-scouting-reports)
8. [The Stats tab, Top 25 and conference filters](#8-the-stats-tab-top-25-and-conference-filters)
9. [The Betting tab and value picks](#9-the-betting-tab-and-value-picks)
10. [Baseball: the Plays screen](#10-baseball-the-plays-screen)
11. [Basketball: the shot chart](#11-basketball-the-shot-chart)
12. [Playoffs](#12-playoffs)
13. [Betting lines and upset watch](#13-betting-lines-and-upset-watch)
14. [Colours and logos](#14-colours-and-logos)
15. [Favorites](#15-favorites)
16. [Keys](#16-keys)
17. [Config](#17-config)
18. [Command line](#18-command-line)
19. [Troubleshooting](#19-troubleshooting)
20. [Where the data comes from](#20-where-the-data-comes-from)
21. [Privacy and API keys](#21-privacy-and-api-keys)
22. [Notes if you want to extend it](#22-notes-if-you-want-to-extend-it)
23. [License and disclaimers](#23-license-and-disclaimers)

## 1. What it does

sportst is a full-screen scoreboard that runs in a terminal window. It is one Python file with no dependencies to install, and it reads free, public sports data - no account, no sign-up, no API key.

### Leagues

NFL, college football, NBA, WNBA, men's and women's college basketball, NHL, AHL, MLB, Minor League Baseball (Triple-A, Double-A, High-A and Single-A), college baseball, college softball, and the Winter and Summer Olympics.

### For every game

Live scores and clocks, line scores, box scores, team stats drawn as two-colour bars, game leaders, and a Plays screen: scoring plays and drives for football, goals and penalties for hockey, a pitch-by-pitch strike zone for baseball, and a to-scale shot chart for basketball. Pick a scoring play and press enter to hear its clip; under the scoring summary, the whole game's highlights play in a card right on the screen, the video and all, through mpv or ffmpeg (section 6). In the NHL and the AHL, pick a player in the box score for his card along the bottom (his photo, profile, season and last games), and a goal on Plays for its spot on the rink, its shot, its strength and the goalie it beat; Game Stats adds the game's flow in shot attempts, the three stars, a shot map, the goalies by strength, the benches and the season series. In the NBA and college basketball the player's card adds his night basket by basket and his shots on a half court, the box score its starters and bench, its shooting and its double-doubles, and the top performers by game score fill the room; Game Stats adds the four factors, how the points came, a lead tracker and ESPN's win probability, and Plays the game's flow in its margin and its biggest runs. In the NFL and college football (since 6.17.0) the box score's players have cards too - his line tonight from every table he is in, his season, his last games - and the top performers by fantasy points fill the room; Game Stats adds points by quarter, who won the efficiency battles (third and fourth down, the red zone, turnovers and the points off them, 20-yard plays, yards a play, possession), field position, how each side's drives ended, the top performers and the win probability; and Plays the game's flow in its margin, its biggest swings and, for a picked score, its drive play by play on the field.

Since 7.0.0 the pictures are drawn as the real thing in Kitty and Ghostty: hockey's shots and goals on a rink with its lines, circles and creases and its game flow as a smooth line chart, basketball's shots on a hardwood court with its painted lane and arcs, baseball's runners on a diamond of grass and dirt and every pitch on a strike zone as TV draws it (as the catcher sees it, numbered, coloured by what it was), MLB's bracket drawn as MLB draws it - the American League from the left, the National from the right, the World Series in the middle - and the College World Series as its two double-elimination brackets. Hockey's and baseball's Game Stats gain new boxes (shots on goal by period, shot types and distances, special-teams time and every penalty; pitch counts and the pitch mix, balls in play, situational hitting and how the runs scored), the hockey Game Center its power play and timeouts under the logos, the box score baseball's notes (doubles, homers, RBI, with runners in scoring position, steals, errors, the pitchers' lines) with the line score and every scoring play, and the Betting tab the day's or week's finished lines in a box of their own. In any other terminal each is drawn in text instead.

Press Z for the Game Center: the game full screen in team colours, the scores and the clock in light bulbs like an old stadium scoreboard, each team's badge (or its real logo) beside its score, live every ten seconds, drawn for its sport - a football field with the ball, the line of scrimmage and the line to gain; a baseball diamond with the runners, the count and who is pitching to whom; a basketball court with each team's shots, the runs and the team fouls, every part on a card of its own and the game's top performers beside them; a hockey rink with every shot on goal, the power play and the goalies; a soccer match timeline with every goal and card - plus ESPN's win probability and how it swung, the last plays, and a banner across the screen in the scoring team's colours for every TOUCHDOWN, GOAL or RUN SCORES. Since 6.12.0 every part sits on a card of its own, and the room under the home team's logo holds what matters most in the sport: basketball's top performers, football's leaders, hockey's goals and goalies, baseball's pitching, soccer's goals and cards. Before the start it counts down to kickoff, tip-off, puck drop or first pitch; after the final it keeps the scoring summary. Since 7.0.0 hockey's has a scorebug under each logo while the game is on, as basketball's and football's do: the team's shots on goal, POWER PLAY with the time left on it (or SHORT-HANDED for the side killing it), EMPTY NET while its goalie is out, and its one timeout, kept or used (the NHL's); and its shots on goal are drawn on the real rink in Kitty and Ghostty. On the Olympic sports Wikipedia covers, Z opens the Event Center: the podium in gold, silver and bronze (section 6).

### Before every game

A scouting report: the line, ESPN's win predictor, the weather, each team's recent form, season leaders, the full injury list and the latest news, and every season stat side by side - with the matchup edges (one team's strength against the other's weakness) called out in colour so they jump off the screen. Pick a headline and press enter to read the whole story right in sportst, in a card over the report - or to play the video, when the headline is one.

### Betting

A Betting tab with every upcoming game's line averaged over FanDuel, DraftKings and BetMGM (or any one sportsbook, or the best price at any of seven), the public's bets and money, line moves, a prediction-market price, and sportst's own projection - with the bets it rates as value flagged, rated out of five stars and sized. In basketball and football the projection is drawn as a curve of the final margin, beside the two teams' tale of the tape; once games are over, the day's finals are graded against their closing lines. Press $ to Ask Kim: an 8-bit pop-up who names the week's three best bets in a comic-book speech bubble - and never explains himself.

### For every league

A Stats tab with every team's offensive, defensive and special-teams numbers on one sortable screen (the pro leagues grouped by league and division) and each team's players, last game and team page, standings, the playoff bracket (or the playoff picture during the season), betting lines with upset alerts where they are posted, and favorite teams that float to the top of every list. College sports filter by Top 25 and by conference; the pros by conference and division.

### Every team

Enter on a team in the standings opens its team page: every game of its season on the left - each result with the record after it, each game to come with its start time and TV network - and on the right the season at a glance: the team on a band in its colours with its logo and its record in big digits, a bar chart of every game's margin, the next game (the opponent's record and place, the countdown, the line, how they met already), the division race, home and away and every other split, the season's best and worst, a report card that grades the offense and defense against the league, the road ahead and the team's title odds. M opens the team's roster on a card: the players down the left, the picked one's card on the right, in boxes packed to fit the screen - his photo and who he is, the latest note on him, his numbers this season, lately, season by season and over his career, his last games, his awards and the teams he has played for.

### The Olympics

The hockey, basketball, football and baseball tournaments look like the pro leagues; every other sport lists its events with podiums and full round-by-round results; there is a medal table; your favorite nations are starred everywhere.

### Your teams first

sportst opens on the Overview: a retro SPORTS TERMINAL title, then every favorite team's latest result and next game (or the game it is playing right now), one keypress from the box score or the scouting report - and under them every league's games today, live now, coming up and final.

### Game day

A BottomLine ticker over the bottom line pages through every league's scores, your teams first. While the league you are looking at has games on, a live wire crawls across the row above it: in hockey every goal as it goes in (who, how, who set it up, the score), power plays, pulled goalies and fights; in basketball the runs, comebacks, late lead changes, close finishes and big nights; in football every touchdown and field goal and every trip to the red zone; in baseball the runs and the no-hitters; everywhere overtime, upset alerts and the finals. Your teams' games put an alert on the bottom line when they start, at every score and at the final - whatever screen you are on, in any league (the terminal bell too, if you like) - and when one of them scores, a banner in its colours flashes over the ticker for three seconds: TOUCHDOWN ARKANSAS, DETROIT GOAL, ST LOUIS HOME RUN, in basketball only a three (OKC THREE). And the mouse works: click a tab, a game, a team or a setting, click it again to open it, scroll with the wheel.

### Settings

A Settings tab that changes every option while the app runs - each group of settings, and each part of About sportst, on a card of its own - and shows sportst's version, files and cache, every free data source with how its requests are going, and every key and command-line option.

It also looks the part: every team in its own colours, meters drawn like an old stereo's LED level meter (or five other ways, a 1980s terminal's shaded blocks among them), team badges like a 1980s TV score bug - the team's letters on its colours - beside the Game Center's scores and under a final, and four retro broadcast colour schemes - ESPN, ABC Sports, CBS Sports and NBC Sports styles - or, with CRT mode on, an old green, amber or white phosphor screen with scanlines, glow, burn-in, a power-on sweep and self test, text typed out as down a slow line, blinking alerts, numbers that flash as they change, a curved face and a bezel, every effect turned up or down to taste on its own card - and the line that sets a bitmap-style font in your terminal. In a terminal that shows pictures, Kitty or Ghostty, sportst notices on its own and shows the real thing instead: the SPORTS TERMINAL title as a picture, the real team logos - big in the Game Center and on a team's page, small down the Scoreboard, the standings, the schedules and your teams on the Overview - and Kim's original portrait (section 14). Every screen can also be printed as plain text for scripts (section 18). The keys that matter on each screen are always listed along the bottom line.

## 2. Install

About five minutes, start to finish. Every command below is typed into a terminal window; lines starting with # are comments you do not type.

### What you need

A computer running Linux, macOS, or Windows 10 or 11. Since 7.0.0 the same file runs on all three: where Python comes without curses (Windows), sportst draws the screen itself with the escape codes every modern terminal reads. See "On macOS" and "On Windows" below.

Python 3.9 or newer. Most Linux distributions and macOS already have it. Check with:

```
python3 --version
```

If that prints "command not found", install it:

```
sudo apt install python3        # Debian, Ubuntu, Linux Mint
sudo dnf install python3        # Fedora
sudo pacman -S python           # Arch
brew install python             # macOS with Homebrew
```

A terminal that does UTF-8 and at least 256 colours. Any modern Linux terminal (GNOME Terminal, Konsole, Tilix, Kitty, Alacritty, WezTerm, xterm), macOS's Terminal or iTerm2, and Windows Terminal all qualify. The minimum size is 50 columns by 10 rows; 110 columns or more gives the side-by-side panes, and around 190 fits everything at once. Kitty and Ghostty can also show pictures, and sportst uses that there: the SPORTS TERMINAL title as a picture, the real team logos (small ones down every list) and Kim's original portrait. Every other terminal gets them drawn in text (section 14).

An internet connection. Nothing is downloaded at install time; the scores are fetched while it runs.

Optional, for scoring-play clips: a media player that can play a web address - mpv (recommended), ffplay (part of ffmpeg) or VLC. sportst plays the clip's sound through it right in the terminal. Without one, clips open in your web browser instead.

```
sudo apt install mpv            # Debian, Ubuntu, Linux Mint
sudo dnf install mpv            # Fedora
sudo pacman -S mpv              # Arch
brew install mpv                # macOS with Homebrew
```

### Step 1 - Get the file

Save the file called sportst somewhere you can find it, for example your Downloads folder. It is the whole program. Open a terminal and go to that folder:

```
cd ~/Downloads
```

Check that it is the right file (the first line names Python) and that it is intact (the second command prints nothing if it is):

```
head -1 sportst                 # #!/usr/bin/env python3
python3 -m py_compile sportst
```

### Step 2 - Try it without installing (optional)

You can run it straight from where it is:

```
python3 sportst --scores        # prints today's NFL slate and exits
python3 sportst                 # the full-screen app; Q quits
```

### Step 3 - Install it for your user

This puts it in ~/.local/bin, the usual place for your own programs. No sudo needed:

```
mkdir -p ~/.local/bin
cp sportst ~/.local/bin/sportst
chmod +x ~/.local/bin/sportst
```

### Step 4 - Make sure your shell can find it

Check whether ~/.local/bin is already on your PATH:

```
echo "$PATH" | tr ':' '\n' | grep -x "$HOME/.local/bin"
```

If that prints the folder, skip to step 5. If it prints nothing, add it, using the line for the shell you use (echo $SHELL tells you):

```
# bash - the default on most Linux systems
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

```
# zsh - the default on macOS
echo 'export PATH="$HOME/.local/bin:$PATH"' >> ~/.zshrc
source ~/.zshrc
```

```
# fish
fish_add_path ~/.local/bin
```

Other terminal windows that were already open need to be closed and opened again to see the change.

### Step 5 - Check it and run it

```
sportst --version               # sportst 7.0.0
sportst --scores -L nba         # plain text: a quick network check
sportst                         # the app
```

Press ? inside the app for the key list, P to pick a league, Q to quit.

### Step 6 - Check your font (optional, one minute)

Team badges, Kim's portrait, the meters and the basketball shot chart use block and braille characters, and so do team logos if you have them drawn in blocks. Almost every Linux and macOS terminal draws them, but to be sure:

```
sportst --logo-test
```

prints a team's badge, every meter look (section 14) with and without the sextant characters, then its logo drawn in five styles. If the badge, the meters and the first logo ("sextants") look clean, you are done. If a logo shows empty boxes, pick the sharpest style that does draw and put it in the config file (step 7) - the meters follow it too:

"logo_art": "quadrants"

If basketball shot charts show boxes where the court lines should be, add:

"court_lines": "dots"

### Step 7 - Settings (optional)

sportst runs with sensible defaults and no config file. To change them, write one out and edit it:

```
sportst --write-config
# that creates ~/.config/sportst/config.json
nano ~/.config/sportst/config.json
```

Section 17 explains every setting - which league opens first, refresh speed, colours, betting lines on or off, and so on. Favorites are picked inside the app on the Favorites tab and saved to the same file automatically.

### Installing for every user instead

If you would rather install it system-wide:

```
sudo install -m 755 sportst /usr/local/bin/sportst
```

Each user still gets their own settings and favorites.

### On macOS

Everything above works as written in macOS's Terminal, iTerm2, Kitty or Ghostty; zsh is the default shell, so step 4 is the zsh line. Python 3 comes with Apple's command line tools (xcode-select --install) or from Homebrew (brew install python); either is fine. For the pictures - the real logos, the rink, the court, the diamond, the strike zone, the CRT glass - use Kitty (brew install --cask kitty) or Ghostty (brew install --cask ghostty): sportst looks exactly as it does on Linux there. Apple's own Python brings a curses too old to tell the mouse wheel's two directions apart, so with it sportst uses its own screen code (Settings, About sportst, System says "sportst's own curses"); a Homebrew Python uses curses as on Linux. Clips: brew install mpv.

### On Windows

Since 7.0.0 sportst runs on Windows itself. Python on Windows has no curses module, so sportst brings its own: it draws the screen with escape codes and reads the keyboard and mouse from the console, using only what comes with Python.

1. Install Python 3.9 or newer from python.org (tick "Add python.exe to PATH" in the installer), or from the Microsoft Store, or with winget install Python.Python.3.12.
2. Use Windows Terminal (it comes with Windows 11; on Windows 10, from the Microsoft Store). The old console window works too, with fewer colours.
3. Save sportst in a folder of your own, for example C:\Users\YOU\sportst, and run it there in Windows Terminal:

```
cd $HOME\sportst
py sportst --version            # sportst 7.0.0
py sportst --scores -L nba      # plain text: a quick network check
py sportst                      # the app; Q quits
```

4. To type just sportst from anywhere, put a one-line launcher beside it, sportst.cmd, and add the folder to your PATH (Settings, System, About, Advanced system settings, Environment Variables):

```
@py "%~dp0sportst" %*
```

Settings and favorites go in C:\Users\YOU\.config\sportst, the cache in C:\Users\YOU\.cache\sportst. Clips play through mpv for Windows if it is on the PATH (winget install mpv), or open in your browser.

What looks different: no terminal on Windows shows pictures the way sportst sends them (Kitty's graphics protocol with Unicode placeholders), so the logos, the rink, the court, the diamond and the strike zone are drawn in text, and CRT mode has its colours, trails, burn-in and sweep but not the glass. If a logo or a meter shows empty boxes, the font lacks the sextant characters: set "logo_art": "quadrants" (step 6), or use Cascadia Code 2404 or newer.

For the full picture on Windows, run the Linux version in WSL 2 with Kitty: in PowerShell as administrator wsl --install (then restart), and in the Ubuntu window sudo apt install kitty python3, then start kitty from there (Windows 11 shows Linux windows on its own desktop) and follow the Linux steps above inside it. To copy the file in from Windows:

```
cp /mnt/c/Users/YOUR-WINDOWS-NAME/Downloads/sportst ~/
```

### Upgrading from an earlier version (for example 6.22.0 to 7.0.0)

Your settings and favorites live in ~/.config/sportst and are not touched by an upgrade, so this only swaps the program file. (6.15.0 changed the look a new install starts with - the Retro NBC Sports scheme on ink, logos in blocks, CRT mode on in colour; a config.json that sportst wrote keeps every setting it had, and one written by hand gets the new defaults only for what it leaves out.)

1. Quit sportst if it is running (Q), in every terminal window.

2. Find where the old copy is installed:

```
command -v sportst
# usually /home/YOU/.local/bin/sportst
# or /usr/local/bin/sportst for a system-wide install
```

3. Note the old version, then remove the old program:

```
sportst --version               # e.g. sportst 5.5.0
rm ~/.local/bin/sportst
# system-wide install instead: sudo rm /usr/local/bin/sportst
```

4. Make the shell forget the old location:

```
hash -r                         # bash and zsh; fish needs nothing
```

5. Install the new file, from the folder you saved it in:

```
cd ~/Downloads
python3 -m py_compile sportst   # prints nothing if the file is intact
cp sportst ~/.local/bin/sportst
chmod +x ~/.local/bin/sportst
# system-wide instead: sudo install -m 755 sportst /usr/local/bin/sportst
```

6. Check it:

```
sportst --version               # sportst 7.0.0
sudo apt install mpv            # optional: hear clips in the terminal
sportst                         # O for Settings: enter opens a group's card
```

7. Optional: clear the cache. Nothing in 7.0.0 needs it - what it adds, the four new leagues included, is read live while it runs - but it is safe: logos, photos and Olympic pages are simply fetched again:

```
rm -rf ~/.cache/sportst
```

The Settings tab can do this too: "Clear logo & page cache" under Actions (your line history is kept).

To go back, copy the old file in the same way; older versions ignore the settings they do not understand.

### Uninstalling

```
rm ~/.local/bin/sportst          # the program
rm -rf ~/.config/sportst         # settings and favorites
rm -rf ~/.cache/sportst          # cached logos, pages, lines
```

### Files it creates

```
~/.config/sportst/config.json      settings and favorite teams
~/.cache/sportst/lines.json        betting-line history
~/.cache/sportst/logos/            team logos, fetched once each (and a
                                   bigger copy in a terminal that shows
                                   pictures), and the hockey players'
                                   photos (photo-*.png)
~/.cache/sportst/wiki/             Olympic results pages
~/.cache/sportst/ncaa-baseball-stats.json
                                   college baseball team stats from
                                   NCAA.com, kept for 12 hours
~/.cache/sportst/ncaa-softball-stats.json
                                   college softball's (7.0.0), the same
```

Nothing else is written. While the game's highlights play in their card, their frames pass through the temporary folder on the way to the terminal (it deletes each as it reads it) and mpv keeps a control socket there; both go with the card. If you set XDG_CONFIG_HOME or XDG_CACHE_HOME, those folders are used instead.

### If something goes wrong

**"sportst: command not found"**

~/.local/bin is not on your PATH yet: do step 4, then open a new terminal.

**"Permission denied"**

The file is not marked executable: chmod +x ~/.local/bin/sportst

**"/usr/bin/env: 'python3': No such file or directory"**

Python is not installed: see "What you need" above.

**"ModuleNotFoundError: No module named '_curses'"**

A version before 7.0.0 on Windows' own Python. 7.0.0 brings its own curses there (see "On Windows").

**On Windows: boxes where the logos or meters should be**

The terminal's font lacks the sextant characters: set "logo_art": "quadrants" in the config, or install Cascadia Code 2404 or newer. Run sportst in Windows Terminal rather than the old console window for its colours.

**"sportst: not a terminal"**

The full-screen app needs a real terminal window. When piping into another program or running from a script, use the plain-text modes such as --scores (section 18).

**"Terminal too small"**

Make the window at least 50 columns wide and 10 rows tall.

**The colours look wrong or washed out**

Try running with TERM=xterm-256color sportst, or add --no-true-color. Section 14 covers colours and backgrounds.

**"Could not reach ESPN" or a DNS error at the bottom of the screen**

The network is down or blocked (a firewall, VPN or proxy). sportst retries on its own; R retries straight away.

**Clips open in the browser instead of playing**

No media player was found. Install mpv (sudo apt install mpv) and press enter again; Settings shows which player sportst found. If you chose "the browser" under Settings, Clips, set it back to auto.

**A clip plays but there is no sound**

Check the player on its own: mpv --no-video followed by any web address of a video. If that is silent too, it is the system's sound settings, not sportst.

## 3. The leagues

Press L to cycle through them, P to pick one from a menu, or start in one with -L:

```
nfl     NFL                     week based
cfb     college football        week based, FBS by default
nba     NBA                     day by day
wnba    WNBA                    day by day (7.0.0)
cbb     college basketball      day by day, every Division I game
wcbb    women's college hoops   day by day, every Division I game (7.0.0)
nhl     NHL                     day by day
ahl     AHL                     day by day
mlb     MLB                     day by day
milb    Minor League Baseball   day by day, all four levels (7.0.0)
cbase   college baseball        day by day, NCAA Division I
csoft   college softball        day by day, NCAA Division I (7.0.0)
owg     Winter Olympics         a whole Games at once; E picks the sport
osg     Summer Olympics         a whole Games at once; E picks the sport
```

Football opens in week mode; basketball, hockey, baseball and softball open on today's date. Press W to put football into day mode for a single Saturday's slate.

The four leagues 7.0.0 adds work as the leagues they are modelled on, screen for screen:

- **WNBA** as the NBA: the box score's player cards, Game Stats, the shot chart, the Game Center's scorebug (the WNBA's four quarters, its timeouts), standings with Hot and cold and Win pace over 44 games, its playoff bracket (the top eight, no play-in), betting lines from every book, and Kalshi's game and championship markets.
- **Women's college basketball** (WCBB) as men's: every Division I game, the AP Top 25 and the coaches' poll, conferences, four quarters (the bonus at the fifth foul of a quarter), the NCAA tournament's bracket, betting lines and Kalshi's markets.
- **Minor League Baseball** (MiLB) as MLB, from MLB's own Stats API: every game at Triple-A, Double-A, High-A and Single-A, pitch by pitch with each pitch's speed, kind and spot (and, where a park tracks it, its spin and the ball off the bat), the box score and its notes, Game Stats, the diamond and the strike zone, standings by league and division, every team's season numbers (the scouting report ranks a team within its own league), the scouting report, each level's playoff bracket with its champions, rosters, schedules and players' numbers. Seven-inning doubleheader games are drawn as seven. Pick your MiLB teams on the Favorites tab as in any league: by league (International, Pacific Coast, Eastern, Southern, Texas ...), then the team.
- **College softball** (CSOFT) as college baseball: every Division I game ESPN lists, its rankings on the games, the conferences, team stats from NCAA.com (batting average, ERA, fielding, runs a game), seven innings, team schedules and rosters, and the Women's College World Series. ESPN keeps a box score only for the games it covers, so many softball games have a score and no box (sportst says so).

The Olympics open on the Games under way, or starting within six weeks, or else the most recent one: Milano Cortina 2026 for the winter, Paris 2024 for the summer until LA 2028 comes round. h and l step to the previous or next Games; T comes back.

## 4. The league picker

P opens a menu over whatever you are looking at:

```
1  NFL               National Football League
2  CFB               College Football (FBS)
3  NBA               National Basketball Association
4  WNBA              Women's National Basketball Association
5  CBB               Men's College Basketball (NCAA Division I)
6  WCBB              Women's College Basketball (NCAA Division I)
7  NHL               National Hockey League
8  AHL               American Hockey League
9  MLB               Major League Baseball
0  MiLB              Minor League Baseball
a  CBASE             College Baseball (NCAA Division I)
d  CSOFT             College Softball (NCAA Division I)
f  Winter Olympics   Milano Cortina 2026
h  Summer Olympics   Paris 2024
```

j and k (or the arrows) move, enter picks, and the key beside a league jumps straight to it without enter: 1 to 9 and 0 for the first ten, a, d, f and h for the last four (7.0.0). / filters the list, esc closes it. L keeps cycling through the same fourteen in order, for when you only want the next one.

You stay on the same tab where the new league has one: looking at the NHL standings and picking the AHL takes you to the AHL standings.

## 5. The Olympics

### Picking a sport

Press E in either Olympics. The menu lists that Games' team tournaments first (hockey, basketball, football, baseball - men's and women's are separate entries), then every other sport, then the other Games on file. / filters it: type skat and you get figure skating and speed skating. The sport you picked last is where that Olympics opens next time.

### Team tournaments

ESPN covers these game by game, so they look like the pro leagues:

```
Scoreboard     every game of the tournament, dated, with the group or
               round in the detail pane and the winner's flag
Boxscore       skaters and goalies, or the basketball box, or each
               footballer's goals, assists, shots, cards and saves
Team Stats     bars for shots, possession, rebounds, corners...
Plays          hockey: goals, strength and penalties by period;
               basketball: every scoring play with the running score;
               football: goals, cards and substitutions by minute;
               baseball: the pitch-by-pitch screen
Standings      the group tables
Medal Round    the knockout bracket from the first playoff to the
               gold medal game, with the bronze game beside it
Medals         the whole Games' medal table
Favorites      nations
```

### Every other sport

Wikipedia keeps a results page for every Olympic event, updated within minutes during a Games, and sportst reads it:

```
Events         every medal event of the sport on the left, with the
               nations that took gold, silver and bronze; the right
               pane has the venue, dates and field, the medallists,
               the top of the final standings and a line about how it
               went
Results        every table on the event's page: heats, semi-finals and
               the final in athletics; both runs in the giant slalom;
               the short program, free skate and overall in figure
               skating; round robin and draws in curling
Medalists      the sport's medal summary and its schedule
Medals         the Games medal table
Favorites      nations
```

Nations show as their IOC code in their own colour (USA, CAN, NOR); medal places are gold, silver and bronze; a favorite nation's rows are starred and bold wherever they appear.

Z on an event opens its Event Center: the podium drawn in gold, silver and bronze with each medallist and nation, the final's table and the event's facts; j / k step through the events (section 6).

### Which Games are on file

Milano Cortina 2026 and French Alps 2030 (winter); Paris 2024 and LA 2028 (summer), LA with its five new sports: baseball, softball, cricket, flag football, lacrosse and squash. Games that have not happened yet show their sports with empty schedules until ESPN and Wikipedia fill them in.

## 6. The screens

### Overview (H - where sportst opens)

A retro SPORTS TERMINAL title in the colours of your scheme, then one row per favorite team, grouped by league: its latest result on the left (W or L, the score with the team's own first, vs or at the opponent, the day) and its next game on the right (the opponent with its ranking in college, the day and start time in your time zone, and the TV network). A team playing right now shows LIVE with the score and the clock instead. On a narrow terminal the next game sits on the line under the result.

Each team has two games to choose from: its latest result on the left and its next game on the right. j / k pick the team; left and right (or h and l) move the highlight between its result and its next game - the side you are on is highlighted, the other carries a faint marker. Enter (or space) on a result opens that game's Game Stats tab; enter on a next game opens its Scouting report (or its Game Stats if it is being played right now) - either way sportst switches to that team's league and day, so 1 then shows that whole slate. B opens the latest result's Game Stats from either side. Z opens the highlighted game in the Game Center over the Overview instead; esc comes back. A game whose kick-off time has not been announced shows "TBA" on its real date. In Kitty or Ghostty each team's logo sits beside its name. With no favorites yet it says how to add them (0 is the Favorites tab). Olympic nations stay on the Olympic tabs.

Under your teams, **Today across every sport**: every league's games today - NFL, college football, NBA, college basketball, NHL, AHL, MLB and college baseball - in three groups, LIVE NOW, COMING UP and FINAL, your teams first in each, then the leagues in order. Each game is one line: the league, the start time or the clock, the two teams (and their rankings in college) with the score, and the TV network. On a wide terminal it flows into two or three columns. College games are the ranked ones and your teams'; the pros show every game. j / k move down into it from your teams, h / l jump a column, and enter opens the game the way it wants to be seen: a live game in the Game Center, a game to come in its Scouting report, a final in its Game Stats. It is read in the background, one league at a time, after the screen in front of you has its own data. When the day's games leave columns of the list empty, the picked game (the first one, until you move into the list) fills them as the Scoreboard shows it: the score and the last play, the line score, the line and, once it has started, the recap and each team's leaders.

### Scoreboard (1)

The slate on the left, the selected game on the right. A red ● sits before every game being played. **o** (since 6.20.0) shows those games only - the list's top border says ● LIVE ONLY · 9, the next game to start shows when none is on, and o again (or a click on the chip) brings every game back; with every game shown the chip reads ● 9 live and a click on it does the same as o. It keeps to the conference or Top 25 filter and the / search, stays on when you change league or day, and j / k, enter and Z move through the live games only. Baseball shows innings with R, H and E, the count, the outs and who is on base while a game is live, and the probable pitchers before it starts. When a game is final the winning team's logo is drawn under the detail pane. c filters to one conference or division and F to the Top 25 in college sports (section 8). Enter on a game that has not started opens Scouting; on any other game it opens the Boxscore.

In every league but the Olympics the day's games sit in a pane of their own (in hockey and basketball with the night's top scorers so far under them when there is room), and under it, in its own pane, the **Television Schedule** - the day laid out the way a cable box's guide does it:

```
╭─ Television Schedule · Tue Nov 3 ───────────────────────────────────────────────╮
│  Tonight    │6:00 PM │6:30 PM │7:00 PM │7:30 PM │8:00 PM │8:30 PM │9:00 PM │9:30 │
│ ────────────┼────────┼────────┼────────┼───▼────┼────────┼────────┼────────┼──── │
│ ▶ COL @ CBJ  Avalanche at Blue Jackets  LIVE 2-1 2nd     │        │        │     │
│   6:00p      ESPN+ · COL Altitude Sports · CBJ CBJNHL    │        │        │     │
│   UTA @ TOR  Mammoth at Maple Leafs                      │        │        │     │
│   6:00p      ESPN+ · UTA Utah 16 · TOR TSN4              │        │        │     │
│   EDM @ NJ  │         Oilers at Devils                            │        │     │
│   6:30p     │         Disney+, ESPN+, Hulu · CAN SN               │        │     │
```

A row for each game, like a channel down the side; the evening across the top in half hours with a gridline at each; and every game a cell over its slot (as long as a TV listing gives it: three and a half hours in football, three in baseball, two and a half in the NBA and hockey, two in college basketball): its name and, once it is on, LIVE with the score and the clock, or FINAL, and on the line under it where to watch it - the national broadcasts first, then each team's local channel after its abbreviation, then CAN and Canada's national ones. ESPN lists the American channels and, in the NHL, the league's own listing adds Canada's (TSN, Sportsnet, RDS, TVA Sports) and any local one ESPN left out; the AHL streams its games on FloHockey (AHLTV). The picked game's cell is gold, the ones on now amber, the ones to come in the scheme's colour and the finals grey; ▼ and ┊ mark now. The guide follows the picked game, and a click on a row picks that game (a second click opens it). When there are more games than rows they get one line each, and the guide scrolls to keep the picked game in view; on a narrow screen it shows part of the evening, from half an hour before now - or, on a night already over, from the picked game (◂ and ▸ mark a game running off either edge). In college the cells name the teams with their rankings (#8 Tennessee).

Under a game that has started, the detail pane adds its recap's headline and each team's leaders: goals, assists and points in hockey, points, rebounds and assists in basketball (a column each), passing, rushing and receiving in football.

### Scouting (2)

The scouting report for the highlighted game - section 7. n / N pick one of the team news headlines and enter opens the whole story in the article card. Since 7.0.0 the room the report left fills up: in basketball and baseball each team's **form** (its last five games, the margin of each and the average), the **tale of the tape** (record, the run or point differential and the record it points to, home and road, the last ten, the streak) and the **meetings this season** from the teams' schedules, where ESPN has no season series. Headlines older than eight months are left out (some feeds keep years-old stories).

### Boxscore (3)

Two panes: the home team on the left, the away team on the right, both scrolling together. Baseball gets batting and pitching lines; hockey gets skaters and goalies; football gets passing, rushing, receiving and defence. Tables that are too wide for half a screen drop their least useful columns rather than running off the edge.

**A player's card (NHL, AHL, NBA, college basketball, the NFL and college football since 6.17.0, and MLB since 6.19.0).** j / k pick a player - down the home team's tables, then on into the away team's - and his card opens along the bottom of the screen:

```
╭─ #21 Garnet Hathaway · FLA ─────────────────────────────────────────────────╮
│ [photo]  Garnet Hathaway                  Tonight  G 0  A 1  PTS 1  +/- -1  │
│          #21 · Right Wing · Florida ...   Season   GP 15  G 0  A 1  PTS 1   │
│          6' 2" · 212 lbs · age 34 ...     Last 10  ▁▁▁▁▁▁▁▁▁█  1 pts        │
│          born Nov 23, 1991 in Naples, FL                                    │
│          12th season                      11/2  vs DET  L 5-3  0  1  1 ...  │
╰─────────────────────────────────────────── enter bigger · w his page · esc ─╯
```

His photo (where the terminal shows pictures; drawn in blocks when Settings has Team logos on drawn; otherwise his number on a badge in his team's colours), who he is (number, position, height, weight, age, which way he shoots, where and when he was born, his draft, his season in the league), his line in this game, his season so far (a goalie's W-L-OT, GAA, SV% and shutouts) with his league rank where he is in the top 25, his last ten as bars (points, or a goalie's save percentage) and, with the room, his games this season. Enter makes the card bigger (and smaller again), W opens his page on ESPN or theahl.com in your browser, and esc lets go of him. A click on a row picks that player; a second click makes his card bigger. The profile comes from ESPN's player pages for the NHL, basketball, football and baseball and from HockeyTech, the AHL's own stats service, for the AHL; it loads in the background and is kept for six hours.

A basketball player's card has his line tonight (points, rebounds, assists, the shooting, steals, blocks, turnovers, +/-, minutes, fouls, offensive and defensive rebounds), his season from his games (a year such as 2025-26 in its place means last season's numbers - a college player before his first game), his last ten as bars with his average, and his games. Under them, when the card has room, **his night**: his points period by period, then every basket and every assist with the clock and the score, his team's first (free throws at one stop of the clock make one row; an and-one says so) - and on a bigger card (enter) **his shots** tonight on a half court, ● made and ○ missed.

A football player's card (NFL, college football) can be opened from any of his rows - passing, rushing, receiving, defence, kicking, returns. **Tonight** is the row picked, column by column as its table has them (C/ATT, YDS, AVG, TD, INT; CAR; REC; TOT tackles ...), then his other tables short: rush 9-25 is nine carries for 25 yards, rec 5-107 five catches for 107, def 7 tkl 1 sk, kick FG 2/2 XP 2/2. **Season** is his game log's totals - his first category in full (a quarterback's passing, a receiver's catches, a linebacker's tackles), the others short - with his rank where ESPN has him in the top 25; **Last 8** (or 10) bars his yards a game in that category (a defender's tackles, a kicker's points, a punter's average) with the total; and with the room, his games this season, newest first, under each category's name (as many categories as fit across).

A baseball player's card (MLB, since 6.19.0) opens from a hitter's row or a pitcher's. Who he is adds which side he bats from and which hand he throws with (B/T R/L). **Tonight** is the row picked: a hitter's H-AB (hits-at-bats), runs, RBIs, homers, walks, strikeouts, the pitches he saw and his AVG / OBP / SLG; a pitcher's decision first (W, 2-0: the win and his record), then innings (5.2 is five and two thirds), hits, runs, earned runs, walks, strikeouts, homers, pitches-strikes and his ERA - and a two-way player's other line short. **Season** is his regular season: games, then a hitter's AVG, HR, RBI, OPS, runs, hits, steals, walks, strikeouts, OBP, SLG, doubles and triples, or a pitcher's W-L, ERA, innings, strikeouts, walks, hits, homers and WHIP; **Playoffs** the same for his postseason when he has played in one; his rank where ESPN has him in the top 25; **Last 10** bars a hitter's hits a game (a pitcher's strikeouts) with the total; and his games, newest first, the postseason's with the rest (a pitcher's W(2-0) is a win and his record after it).

With nobody picked, the room the tables leave holds the game's **three stars** - the NHL's own, from the NHL's game center, or the AHL's - each with his photo (in Kitty or Ghostty), his line tonight, his season and his last ten; click one for his card. Basketball fills it with the game's **top performers**: its best three by game score (John Hollinger's one number for a box score line - points, shooting, rebounds, assists, steals and blocks, less misses, fouls and turnovers; 10 is a solid night, 20 a great one). Football's box score runs long, so on a tall screen (36 rows or more) its top three get a box along the bottom anyway, the tables scrolling above: the best by **fantasy points** (half-point PPR - a point per 25 passing yards, 4 a passing TD and -2 an interception; a point per 10 rushing or receiving yards, half a point a catch, 6 a TD; -2 a fumble lost; on defence a point a solo tackle, half an assisted one, 2 a sack, 1 a tackle for loss or a pass defended, 3 an interception, 6 a TD; 3 a field goal, 1 an extra point - 20 is a big game, 30 a great one), each opening on the table that earned him the most. Baseball (since 6.19.0) does the same with its top three by fantasy points in the usual daily-game scoring: a hitter gets 3 a single, 10 a home run, 2 an RBI, a run or a walk (the box score has no doubles or triples a player, so they count as singles); a pitcher 0.75 an out, 2 a strikeout and 4 a win, less 2 an earned run and 0.6 a hit or a walk - 10 is a good night at the plate, 20 a fine start.

Under each basketball team's table: what the **starters** and the **bench** put up (points and their share, FG, 3PT and FT, rebounds, assists), the team's **shooting** (FG%, 3PT%, FT%, effective field goal % - a three counts one and a half - and true shooting, points per two shots with free throws in) and anyone with a **double-double** (or a triple-double).

Since 7.0.0 a baseball box score (MLB, Minor League, college baseball and softball) carries the notes a printed box score does under each team's tables: **batting** (doubles, triples, home runs with the inning, the pitcher and the men on, total bases, RBI, two-out RBI, runners stranded with two out, sacrifice flies, double plays hit into, with runners in scoring position, left on base), **baserunning** (steals, caught stealing, picked off), **fielding** (errors, double plays, outfield assists) and, under the home side's, the game's **pitching** (pitches-strikes, ground balls to fly balls, batters faced, inherited runners, hit batters, wild pitches, a starter's game score; the Minor Leagues' pitch-timer violations and automated ball-strike challenges too). Under the visitors' notes: the **line score** and every **scoring play** with the score after it.

### Game Stats (4)

This game's comparison card (called Team Stats before 4.2), in two sections: the teams on the left, the leaders on the right (the right one has no title of its own since 6.16.0 - its first box, GAME LEADERS, says what it is). Since 6.14.0 each part is a box of its own with its name in the border, and the boxes are packed side by side wherever they fit - a short table beside another, a long one flowing into columns - and a part moves to the other section when that evens the two out, so a game's whole card fits on a 190x48 terminal without scrolling (j / k and PgDn scroll whatever a smaller one cannot hold):

```
TEAM STATS         one line a stat: the two teams' numbers either side
                   of a two-colour bar in their own colours
MORE TEAM STATS    the rest of the team numbers - the away team's, what
                   it is, the home team's - in two to four columns side
                   by side when they fit
GAME LEADERS       a category a row (passing, rushing, receiving; points,
                   rebounds, assists; goals, assists, points; hitting,
                   pitching), the away team's leader beside the home
                   team's: his name, his number, the rest of his line
```

Baseball compares runs, hits, home runs, extra-base hits, walks, strikeouts, stolen bases, runners left on base and errors, and its leaders are the best hitter and pitcher on each side, taken from the box score.

Hockey (NHL and AHL) fills the rest of the screen, each part a box: under the team stats, side by side: goals and shots **by period**; **shot attempts** both ways - on goal, missed, blocked, each team's share of all attempts as a percentage, shooting and save percentage; and **how the goals came** (even strength, power play, short-handed, empty net). Under the game leaders: the **three stars**, **goaltending** with each goalie's saves at even strength, on the penalty kill and on the power play, **behind the benches** (the head coaches, the scratches and the officials) and the **season series**. The shot map and the game flow are on the Plays tab. J / K scroll.

Basketball (NBA, college) does the same, each part a box. Under the team stats: points **by quarter** (by half, in college); the **four factors** - Dean Oliver's four things that win basketball games: shooting (eFG%), turnovers per possession, offensive rebounding (the share of its own misses a team got back) and free throws per field goal tried - each a pair of meters facing each other, the better number in green; and **how the points came**: in the paint, on the fast break, off turnovers, from three, at the line and, in the NBA, from the bench, each a meter split between the teams. Under the game leaders: the **top performers** by game score, a **lead tracker** (each team's biggest lead and longest run, the share of the game it led, the lead changes and ties), ESPN's **win probability** play by play with the play that swung it most, the **officials** and the **season series**.

Since 6.22.0 two more parts, from the box score's players and showing nothing the screen shows elsewhere, fill the room at the bottom, each a team a row as the points by period are: **bench and depth** (the bench's points - unless how the points came already has them - and rebounds, how many players scored, how many reached 10 points and a double-double, and how many fouled out when one did; the better number bold), beside the points by period where it fits, and **more leaders** (each team's best at steals, blocks, threes, free throws, plus-minus in the NBA and minutes, as many as fit across).

Football (NFL, college, since 6.17.0) too. Under the team stats: points **by quarter**, then three parts that compare the teams row by row, a ◀ or ▶ in the winner's colours pointing to the side that won each row: **efficiency** (3rd and 4th down made/tried and the rate; red zone touchdowns/trips inside the opponent's 20 - ESPN's count where it publishes one, the NFL's, else counted from the drives; turnovers and the points the other side scored off them, on the return and on the drive it gave them; 20-yard runs and catches; yards a play; time of possession), **field position** (of the drives that are over: the average start - own 28, opp 45 - drives begun at midfield or better, plays, yards and points a drive, three-and-outs) and **drive results** (touchdowns, field goals, punts, turnovers, on downs, missed field goals, safeties, the ends of halves). Under the game leaders: the **top performers** by fantasy points (the Boxscore's measure), each with every line he put up, ESPN's **win probability** with its biggest swing, and the **officials**. At 190x48 a football game's whole card fits without scrolling.

Since 6.22.0 the room under the points by quarter and the efficiency holds three more parts, built from the box score's team totals and showing nothing the screen shows elsewhere: **defense** (sacks, tackles for loss, QB hurries in college or QB hits in the NFL, passes defended, defensive touchdowns - sacks and defensive touchdowns only where ESPN's team stats do not already show them, as the NFL's Sacks-Yards Lost and Defensive / Special Teams TDs do), **special teams** (extra points when one was missed, the punts' average and how many ended inside the 20, kick and punt returns as returns-yards, the arrow for the better average a return) and **longest** (each side's longest pass, run, return, field goal and punt, in as many column groups as fit). The longest plays go wherever the two sides even out, and are left out when the screen would scroll with them and not without.

Since 7.0.0 hockey's card adds, where the game's feed has them: **shot types** (each team's shots on goal by kind - wrist, snap, slap, backhand, tips and deflections, wraparounds - with the goals each brought), **where the shots came from** (inside 20 feet, 20 to 40, beyond 40, the average distance and the goals'), **special-teams time** (from the skaters' ice time: the power play's minutes, shifts and the average shift) and **penalties** (each team's minors, majors, misconducts and fights, who took and who drew the most, and what they were called for). Baseball's (MLB, Minor League, college baseball and softball) adds **pitch by pitch** (each side's pitchers' first-pitch strikes, called and swinging strikes, fouls, batters taken to three balls, pitches a batter), the **pitch mix** (where the play by play has the pitches: each kind's share and average speed, the fastest), **balls in play** (ground balls, fly balls, line drives and pop-ups, ground outs to air outs, where the hits went), **situational hitting** (with runners in scoring position, two-out runs, innings the leadoff man reached, scoring innings and the biggest, innings down in order) and **how the runs scored** (homers, other hits, outs, walks and hit batters, errors, wild pitches and the rest). The less important of them go first when the screen would scroll.

Baseball (since 6.19.0) as well. Under the team stats: runs **by inning** with R, H, E and the runners each side left on base (an x where the home team did not need its last turn); **at the plate**, row by row with the ◀ ▶ arrows (hits, extra-base hits, home runs, walks, strikeouts, stolen bases, runners left on base, double plays hit into - fewer is better for those three - the pitches each lineup saw and its AVG/OBP/SLG for the game); and **on the mound**, each team's starter and its bullpen: innings, hits, runs, earned runs, walks, strikeouts, pitches-strikes and the decisions. Under the game leaders: the **top performers** by fantasy points (the Boxscore's measure) with their lines (2-4, HR, 3 RBI, R; 6.0 IP, 4 H, 1 ER, 2 BB, 7 K, W), ESPN's **win probability** with its biggest swing and its half-inning (top 2nd), the **umpires**, and the **playoff series** in the postseason (its record counted from its games) or the season series.

### Plays (5)

One line at the top for the score, status, venue, crowd and weather, then two panes. Since 6.19.0 every part of both panes sits in a titled box of its own, as on the Game Stats tab - THE GAME, GAME FLOW, SCORING, GAME HIGHLIGHTS and WIN PROBABILITY beside DRIVES, BIGGEST SWINGS and OFFICIALS in football; AT THE PLATE, THIS AT-BAT and RECENT PLAYS beside STRIKE ZONE, ON THE BASES, SCORING PLAYS, BIGGEST SWINGS and WIN PROBABILITY in baseball; and so on in every sport - while picking plays, the clips, J / K, the wheel and clicks work as before. Football: the **game's flow** (since 6.17.0: the margin through the game in braille, the home team's lead above the line in its colours and the visitor's below, each quarter marked, the lead changes and ties under it), every score on one line each (quarter, clock, team, kind, score, what happened) and the win-probability chart on the left; every drive (quarter, team, result, plays, yards, time, start), the **biggest swings** - the plays after which ESPN's win probability moved most, who gained and by how much, the quarter and clock and the play - and the officials on the right. j / k pick a score and **its drive** fills the bottom of the screen, as tall as the drive: each play a row on the field (as the Game Center's drive chart draws it, the away team's end zone on the left), from where it began to where it ended in the offense's colours, ▶ / ◀ the way it went, a loss in grey, an incompletion, no gain or a kick a dot; the down and distance before it, the yards and what happened after it, the score itself in bold; the title says how the drive ended, when, the score after it and its plays, yards and time. Enter plays the score's clip, esc lets go. Hockey (NHL, AHL, Olympic): goals one line each with their strength and assists, and the three stars, on the left; shots on goal by period, penalties and officials on the right. In the NHL and the AHL, with no goal picked, the room under the lists holds two boxes side by side: the **shot map** - the rink from above with every shot on goal and goal of the game in the shooting team's colour - and the **game flow**, each team's running count of shot attempts across the game in braille in its own colours, with every goal marked under the minute it came (the AHL's play by play has shots on goal only, so its chart counts those). On a narrow or short screen they follow the lists instead: J / K scroll down to them. j / k pick a goal and its card fills the bottom: the rink with the goal ringed (◉) among the game's shots, when it came and the score after it, what it did (opened the scoring, tied it, put them ahead, the game-winner), the scorer and his goals this season, the assists, the shot's type and distance, the strength and the goalie it beat, and under it, with the room, the game flow with ◉ at this goal; esc lets go. Baseball gets the pitch-by-pitch screen (section 10) with the game's scoring plays under the strike zone, then (since 6.19.0) its **biggest swings** - the plays that moved ESPN's win probability most, with the half-inning - and the **win probability** chart; basketball gets the scoring plays and the shot chart (section 11), with the game's flow and its biggest runs over the scoring plays.

Since 7.0.0 hockey's **shot map** and the Game Center's shots on goal are drawn on a real rink in Kitty and Ghostty - the boards rounded at the corners, the red and blue lines, the faceoff circles and dots, the goal creases in blue, every shot a dot and every goal a ring in its team's colours - and the **game flow** is a line chart, each team's running count of shot attempts a smooth line over its shaded area in its colours, every goal a ringed dot on its line. In other terminals both are drawn in text as before.

Since 6.21.0 the **game flow** (football and basketball) is a column chart - each column the margin at the end of its stretch of the game, up in the home team's colours while it led and down in the visitor's - drawn in Kitty and Ghostty as a picture under its labels with every column outlined and set apart from the next, the zero line and the periods' starts dashed (half-cell blocks with a gap between columns elsewhere); and football's **win probability** is the same area chart as Game Stats' - a smooth line over the share of whoever led, shaded in that team's colours from the dashed 50% line (braille dots filled out to the 50% line in text). Football's scoring plays take one line each where they can: a routine extra point - (… Kick) - is left off a line that would otherwise wrap, while a missed or two-point try stays; with that, the whole left pane fits at 190x48.

### The game's highlights (on Plays)

At the foot of the scoring summary, in every league, a little section of its own holds the whole game's highlights:

```
Game highlights  y picks · enter plays it here
▶ Utah Mammoth vs. Montreal Canadiens: Game Highlights  1:15  ESPN
```

y picks them (in MLB, y again picks the other one), and j / k run on to them past the last scoring play; enter - or a click on them and a second click - plays them in a card over the screen, the video inside it:

```
╭─ Game highlights ──────────────────────────────────────────────╮
│ Utah Mammoth vs. Montreal Canadiens: Game Highlights           │
│ ESPN · 1:15 · mpv                                              │
│ ┌────────────────────────────────────────────────────────────┐ │
│ │                        the video                           │ │
│ │              (16:9, as big as the screen allows)           │ │
│ └────────────────────────────────────────────────────────────┘ │
│ 0:23 / 1:15  ▌▌▌▌▌                                             │
│ space pause · ← → 10 s · r from the start · esc close          │
╰────────────────────────────────────────────────────────────────╯
```

```
space, enter       pause / play on; at the end, play them again
← →  h l           back / on ten seconds
R                  from the start
n N                the other video, where there are two
esc, q, X          close (a click outside the card too; a click
                   inside it pauses)
```

The highlights are the whole game's, not one play: ESPN's "Game Highlights" video (college football, NBA, WNBA, college basketball, NHL - ESPN posts it soon after the final, and not for every game), MLB's recap and condensed game, and the NFL's own on its YouTube channel. Until there are any, the section says so and offers a YouTube search (it opens in your browser).

A terminal cannot play video by itself, and sportst decodes none: an installed player does it, and the card shows what it plays.

```
Kitty with mpv        mpv draws the video into the card itself,
                      sound and all (its own Kitty output)
ffmpeg                sportst draws ffmpeg's frames into the card -
                      as pictures in Kitty or Ghostty, in coloured
                      half blocks in any other terminal - and ffmpeg
                      plays the sound itself, from the same stream,
                      so the two keep time (through PulseAudio or
                      PipeWire, ALSA, or macOS's own sound)
mpv, no pictures,     the video plays in mpv's own window
  no ffmpeg
neither               the highlights open in your browser
```

sudo apt install mpv ffmpeg (Debian, Ubuntu, Mint) puts both in. The NFL's YouTube video plays in the card only with yt-dlp as well (sudo apt install yt-dlp, or the yt-dlp project's own download); without it, it opens in the browser. In CRT mode the video takes the phosphor's colour and the glass - scanlines, the curve, the bezel - lies over it too. While the card plays, sportst draws nothing else (the data keeps loading underneath), and leaving the card, or sportst, stops the player. Settings → Clips → Play highlights with picks the way: auto, mpv, ffmpeg, a player's own window, or the browser.

### Scoring-play clips (on Plays)

j / k highlight a scoring play - every touchdown and field goal, goal, run or basket - and enter plays its clip. The mark beside each play says what enter will do:

```
♪   a clip with sound: it plays right here, sound only, through
    mpv, ffplay or VLC (whichever is installed), and the bottom
    line shows what is playing
↗   a clip on a web page (the NHL's video player or YouTube): it
    opens in your browser
▶   the play whose clip is playing now; enter on it again, or X,
    stops it
(no mark)  no free source has a clip of that play; enter opens a
    YouTube search for it in your browser
```

n and N jump straight to the next or previous play with a clip - in basketball, with well over a hundred scoring plays, that is the quick way round. Y picks the whole game's highlights, at the foot of the scoring summary (above). J and K scroll the screen while j and k move between plays.

Where the clips come from - all free, no account, no key:

```
College football, NBA,   ESPN's one-play clips, the same ones
college basketball,      espn.com shows.  ESPN clips the big
college baseball         moments, so a touchdown usually has
                         one; an ordinary field goal or basket
                         often does not.
NHL                      ESPN's goal clips, played here; for a
                         goal ESPN did not clip, the NHL's own
                         clip of it in the NHL's video player,
                         in the browser - that one clip, not a
                         playlist that runs on into the next.
MLB                      MLB's own highlight clips (the MLB Stats
                         API), played here; most scoring plays
                         have one.
NFL, AHL                 the league's official YouTube channel,
                         in the browser.  Its public feed lists
                         only the most recent uploads, so this
                         works best on game day; older plays get
                         a YouTube search instead.
```

Clips are matched to plays by the players' names, the distance and the kind of play (a dunk's clip is never paired with a jumper), so a play is left unmarked rather than given someone else's clip. A play's clip is the play itself - what led up to it and what followed, usually a minute or two: only videos of known length up to two and a half minutes are matched to a play, so a condensed game or a full replay never is, and mpv, ffplay and VLC stop a play's clip at two and a half minutes. (The game's highlights, Y, play in full in their own card.) The commentary is whichever broadcast the clip was cut from - usually the national or one team's TV call - not a particular local radio call, which no free service publishes.

Settings, Clips chooses the player (auto, mpv, ffplay, VLC, or always the browser), whether the player opens a video window as well as the sound, and whether YouTube is used for the NFL and AHL. Leaving sportst stops whatever is playing.

### Standings (6)

Divisions flow into as many columns as your terminal fits. At 190 columns the entire NFL fits on one screen. c shows a single conference or division and / finds a team by name - handy in college basketball's 32 conferences.

College football and college basketball (since 6.21.0) fit on one screen instead of a long scroll of tables. Since 6.22.0 it is a grid of boxes, every column the same height:

- on the left, the **conferences** - the one picked lit, each with its leader and record and its **margin**, how many points a game its teams win or lose by on average, with a small meter (green ahead, red behind);
- beside them, **the picked conference's table** in a box of its own: the poll's rank before each ranked team, the conference and overall records, home, away and against ranked teams (the columns a narrower screen gives up first), points (or points a game in basketball), the streak and a bar of each team's margin a game; in the room left under it, the scoreboard's **games for the conference's teams** - the week's in football, the day's in basketball - with the score, the clock or the kickoff;
- under both, **Hot and cold** for the whole division (football's short list of conferences shares a row with the table; basketball's thirty-two take the left side's whole height and Hot and cold goes under the table);
- on the right, **the poll**, with the **ranked teams by conference** under it - how many each conference has, and its best.

j / k walk every team, conference by conference (the list and the table follow), h / l jump to the previous / next conference, a click on a conference picks it, and enter opens the picked team's page as before. A narrower screen drops the poll's column (the poll goes last) and then stacks the boxes. With a conference filter (c) or a search (/) the tables show as they always have.

In the NHL and the AHL two panes of their own hold the league at a glance. **Points pace** - every team by points %, as a meter (a row of blocks in the team's colour, one a segment), with the points it would finish on at that rate over the season - sits beside the division tables when they leave a column free, and under them otherwise. **Hot and cold**, under the tables, names the league's five hottest teams and its five coldest four ways: over the **last ten games** (W-L-OTL, the points those earned and the streak), by **goal differential** (each a meter against the biggest), **at home** (Hot at home, Cold at home, by points %) and **on the road** (Hot on the road, Cold on the road). On a smaller screen they sit under the tables: J / K scroll down to them, while j / k still move the pick.

In the NBA, the NFL and MLB three panes sit under the tables. **Hot and cold** names the five hottest and coldest teams over the last ten (with the streak; the NFL has no last ten), by point (in baseball run) differential a game (each a meter), at home and on the road. **Win pace** ranks every team by win %, a meter each, with the record it is on pace for over the season (82 games, 17, 162). **Offence and defence** places every team by the points it scores a game (across) and allows (down, the fewest on top) on lines through the league average: the top right does both (both ends), the top left wins low-scoring games (stingy), the bottom right plays shootouts, the bottom left neither.

College basketball and college football, with so many conferences of tables, put their panes above them: the **Top 25** (the latest poll ESPN lists first - in football the Playoff Committee's once it is out - with each team's move since the last one, its record today and its first-place votes), **Hot and cold** (point differential, at home, on the road) and, under it, **Conference strength** - each conference's average margin a game so far, its record and a meter, best first.

**A team's page.** j / k move a highlight (▌) through the teams - down a division, then on into the next column - and enter opens that team's page: its season game by game on the left, the season at a glance on the right (below). There j / k pick a game and J / K jump ten, enter opens it (its scouting report before the start, its box score once it is under way or played), Z puts it in the Game Center, T jumps back to the next game, M opens the team's roster (below) and esc (or backspace) comes back to the standings. With the mouse, click a team to pick it and click it again to open its page. College baseball has no team schedules at ESPN and the Olympic tournaments publish none, so there the Scoreboard has the games (and in college baseball the calendar, C).

The season at a glance, top to bottom (the Info pop-up, I, says the same on the screen):

```
the band           the team's name on its colours, the season and its
                   place in the standings; under it the team's logo
                   (its badge in text-only terminals), its record in
                   big digits, the streak and the last five, home and
                   away, points (runs, goals) for and against a game
THE SEASON SO FAR  one bar a game: up for a win, down for a loss, as
                   tall as the margin; ◆ a tie, · a game to come;
                   football's week numbers or the months underneath
NEXT UP            the next game: the opponent's record and place,
                   when (today, tomorrow, in 5 days) and where, the
                   betting line, and the result if they met already;
                   LIVE NOW while it is on, SEASON OVER at the end
the standings      the team's division (its conference, in college),
                   the team marked ▶, your teams ★
SPLITS             home, away, division, conference, against teams at
                   .500 or better (and ranked teams, in college), the
                   last few, one-score games (within five points,
                   one goal, one run), overtime or extra innings
BY THE NUMBERS     the biggest win, the worst loss, the most scored,
                   the fewest allowed, the longest runs, shutouts
REPORT CARD        where the offense, the defense and the margin rank
                   in the league, as a grade from A+ to F
THE ROAD AHEAD     games left, home and away; the opponents' win %
                   so far and to come; how many teams over .500 are
                   left; the toughest three in a row
TITLE ODDS         the team's chance to win it all, and its place
```

On a terminal at least 120 columns wide the games and the dashboard sit side by side; on a narrower one the page shows the games and V switches to the dashboard (j / k scroll it) and back. In Kitty or Ghostty every opponent's logo runs down the schedule.

**The roster (M, since 6.13.0).** M on a team's page - or a click on **M roster** at the top right of it - opens the team's roster on a card over the page. Down a thin list on the left go the players with their numbers and positions: football's by side of the ball (offense, defense, special teams, then injured reserve and the practice squad), each side by position; hockey's and baseball's by position, as ESPN groups them; basketball's by number. j / k (or a click) pick a player, tab and shift-tab jump to the next or previous group, g and G to the first and last. On the right is the picked player's card, read from ESPN's public player pages a moment after the pick rests (the AHL's from HockeyTech). It is a set of boxes, each with its title in its border, packed side by side so that as much as possible is on the screen at once:

```
#15 NAME           who he is, beside his photo (the headshot in Kitty
                   and Ghostty; drawn in blocks when Team logos is
                   drawn; else his number on a badge in the team's
                   colours): position and team, then HT/WT, AGE (and
                   birthday), FROM, COLLEGE, B/T or SHOOTS / CATCHES,
                   EXP (CLASS in college), DRAFT, and a STATUS other
                   than active (injured, out ...) in orange
LATEST             the newest note on him - RotoWire's, as ESPN
                   carries it - or his latest headline; the story
                   under it as far as there is room
STATS              this season, his last five games and his career
                   (the playoffs too, where he has them), in the
                   columns ESPN uses for his position; football's
                   split under PASSING, RUSHING, RECEIVING ... side by
                   side, or one under the other when narrow
LAST GAMES         his last five: the date, the opponent, the result,
                   then his line, under the same headings
BY SEASON          every season of his career, newest first, with the
                   team he played for, and his career total (college
                   players' seasons are the rows of STATS instead)
AWARDS             the awards on file (MVP, Silver Slugger, Hart Trophy,
                   All-Star ...), how many times, and the seasons;
                   college players seldom have any
TEAMS              the teams he has played for, and when
```

On a terminal of about 120x36 or more everything fits. When it does not, the card makes room a step at a time, least important first: a shorter story, fewer old seasons, the awards and teams run together on a line, the headline alone, the games' columns cut to one band instead of wrapped, three rows of numbers and games, the lists cut short ("… more on his page (W)"); then it gives back whatever still fits. Only past all that - a small terminal and a well-known player - does the card run long: then J / K (PgDn / PgUp, the wheel over the card) scroll it, and the bottom line says so. W opens his page (ESPN's, or the AHL's) in your browser, and esc or M closes it. No free source lists the preseason watch lists (the Maxwell, the Naismith ...), so the card has none; the awards are the ones a player has won. College baseball has no rosters at ESPN and the Olympic tournaments publish none, so their team pages have no M.

### Stats (7)

Every team in the league, one row each, with a column per season stat - offense and defense side by side on a wide terminal. The pro leagues are grouped by league and division. Enter on a team opens its players; g then steps to its last game and its team page - section 8.

### Playoffs (8)

The bracket, or the playoff picture while the season is on, with the championship odds and a chart of them beside it (the top 25 since 6.21.0, the rest counted in a line). In college football and basketball the picture is the polls (since 6.21.0): the Playoff Committee's (the AP's until it is out) as a single column of 25 with the playoff field ruled off, and beside it the AP Top 25 and the coaches' poll, as many as fit across, each rank with how far it moved since the last poll (the lower divisions' polls, under them in 6.21.0, were left out in 6.22.0). In the NFL and MLB (since 6.19.0), the NHL, the AHL and the NBA the picture is followed by the playoffs **if they started today**, with sportst's chance for each game or series (the NFL's top seeds sitting out the wild-card round and the rest reseeded after it; MLB's top two in each league sitting out the best-of-three wild-card series; in the NBA the play-in too: 7 v 8, 9 v 10 and the game for the eighth seed). College basketball follows its poll with the poll's top 24 as the tournament's **top six seed lines** and how many ranked teams each conference has. See section 12.

### Betting (9)

Every upcoming game's line and sportst's value picks, and $ to Ask Kim for the week's three best bets - section 9. In the NHL and the AHL the game's detail adds the **tale of the tape** (the two teams from the standings, side by side) and the **score odds** (how many goals the projection points to, the likeliest scores, the chance of overtime). In basketball and football it adds the tale of the tape (record, points for and against a game, the differential, the last ten, the streak, home and road) and the **margin odds**: the projected final margin as a curve three rows tall with the spread marked (since 6.21.0 a smooth shaded curve four rows tall in Kitty and Ghostty, the spread a gold dashed line, its caption on the heading's line and the cover beside the total), each side's chance to win and to win by 1-5, 6-10 or 11 and up (football's key numbers: 1-3, 4-7, 8 and up), the chance to cover and the over at the posted total and five (football: three) either side. In every league, once some of the day's games are over (the week's, in football), **how the day's lines did** grades the finals against their closing lines (the books' consensus): who covered, over or under, the upsets and the day's tally - under the picked game's detail, or on its own when nothing is left to bet. Since 7.0.0, where the panes stand side by side, it has a box of its own under the lines, as tall as it needs up to half the detail, scrolling on its own (tab moves from the lines to it to sportst's read).

### Favorites (0)

Pick two or three teams per league; they float to the top of every list and fill the Overview. Since 6.21.0 the teams are grouped by conference, each shut until you open it (section 15).

### Settings (O, the last tab)

The tab is a list of titles, and each one opens a card (since 6.12.0). On the left, the settings in their groups - General, Display, Game day, Data sources, Betting, Upset watch, Clips and Actions - each with how many settings it holds and, in gold, how many of them differ from their default ("this run" in orange when A, + or - changed one for this run only). On the right, About sportst: its version, then its parts - System, Data sources, Recent problems, Controls and Command line - each with a word on how it stands (how many sources this run used and whether one is failing, the latest problem). Below 110 columns About sportst sits under the settings. j / k pick a title, up and down through both sides; l (or →) goes over to About sportst and h (or ←) back; the picked title is explained at the foot of its side - a group's settings by name, what a part holds. Enter or space opens its card over the tab, and so does a click on a title and a second click.

A group's card lists its settings with their current values; a gold value differs from the default. Under the list the picked setting is explained, with its default, its config.json name and whether it takes effect now or at the next start. j / k move, enter or space changes it (switches it, lists the choices, or asks you to type a number, a colour or the sportsbooks), h / l step it down or up, R puts it back to its default. Tab and shift-tab go on to the next or the previous group without closing the card; esc (or Q, or a click outside the card) closes it. Every change is saved to config.json at once, and all but the start-up league take effect immediately - a new colour scheme repaints the screen behind the card as you step through them. In Display, enter on CRT effects opens the CRT effects card, every CRT effect with its own level (section 14); esc there comes back to Display.

Actions, the last group: save now (which also keeps the auto-refresh state and interval set with A, + and -), reload config.json after editing it by hand, refresh all data, clear the logo and page cache, clear the betting-line history, and reset every setting to its default (favorites and team colour overrides are kept). The clearing and the reset ask you to type yes first.

About sportst's cards scroll with j / k (J / K, PgDn and PgUp a page, g and G the top and the end), and tab goes on to the next part. System: sportst's version, Python, the terminal's size and colour depth and whether it shows pictures (section 14), CRT mode, how long it has been running and how many requests it has made, the league, where config.json and the cache are and how big the cache is, how clips and highlights play here, and your favorites. Data sources: every data source - what it supplies, its host, and how this run's requests to it have gone (worked, failed, how long the last one took, how long ago), with the sources the current league uses in bright text and the last failure in orange. Recent problems: the requests that failed lately and have not worked since. Controls: every key. Command line: every command-line option.

### The Game Center (Z, on any game)

Z puts the highlighted game - on the Scoreboard, Scouting, Boxscore, Game Stats or Plays, and the game picked on the Overview, the Betting tab or a team's page - full screen, and keeps it live: every ten seconds while it is being played. It opens over the screen you are on, and esc brings you back there. It works in every league and every Olympic tournament, and each sport gets its own picture. Since 6.12.0 everything under the score sits on cards, each with its name in its top border, and the room under the home team's logo - empty before - holds what matters most in the sport.

```
top        the two teams in their colours, the scores and the clock
           between them (the inning in baseball) in light bulbs like
           an old stadium scoreboard (since 6.18.0, every sport):
           each digit an 8 of bulbs, the lit ones warm white and
           the rest dark in their sockets, a single-figure score
           with its tens unlit; a score flashes its bulbs white and
           after the final the loser's burn low. In Kitty or Ghostty
           a picture of real glowing bulbs; elsewhere ● bulbs in
           text from 120x34, the plain digits on a smaller screen.
           The period under the clock, the records under the
           scores; on a big screen each team's badge beside its
           score, or its real logo in Kitty or Ghostty (a
           three-letter badge needs about 130 columns)
football   DRIVE CHART (since 6.15.0): every drive of the game on
           the field, a row each, oldest at the top - the offense,
           a bar in its colours from where the drive began to where
           it ended with the yards in it, an arrow the way it went,
           the end zones in the teams' colours, then how it ended
           (TD and FG with the score after it, PUNT, INT, FUMBLE,
           DOWNS, MISSED FG, END HALF) and its plays, yards and
           time; since 6.17.0 each result is on a chip in the
           offense's colours, so it says whose drive it was, and a
           score the defense made on it (INT TD, FUM TD, RET TD,
           SAFETY) is on the defense's, with its name - every chip
           names its team when the two wear the same colours; the
           drive under way runs to the ball (●) with the line to
           gain (┃) ahead of it, marked NOW, and moves with every
           refresh; as many of the latest drives as fit. In Kitty
           and Ghostty (since 6.20.0) a picture under it outlines
           each drive's bar and sets a strip of grass between it
           and the next, and puts each result on an outlined card
           of its own (section 14). Where the
           screen has no room for it (under about 34 rows), THE
           FIELD: end zones in the teams' colours, the ball, the
           blue line of scrimmage and the yellow line to gain, the
           down and distance under it.
           Over it, since 6.17.0, a row of cards: BY QUARTER; while
           the game is on DOWN & DISTANCE - the down and the
           distance in big digits in the colours of the team with
           the ball (1ST & GOAL spelled out), who has it, where,
           RED ZONE (between plays, what is happening and the last
           play); THE LINE - the book's spread and total and how
           the score stands against them: who is covering and the
           points' pace while it is played, who covered and over or
           under once it is over, the moneylines; and in the room
           left BIGGEST PLAY, the play that swung ESPN's win
           probability most (THE GAME - where, the crowd, the
           weather - without one).
           In the score band, while it is played, a football
           between the logo and the score of the team that has it
           (a college ball with white stripes; in Kitty or Ghostty
           a picture of a real football, elsewhere drawn in
           blocks), moving across when the ball changes hands, and
           each team's timeouts left under its logo (● left, ○
           used).
           LEADERS under the home team's logo (since 6.18.0): the
           game's top three players by fantasy points (the
           Boxscore's measure), each with his name and points, his
           number, position and team (#12 Quarterback · Alabama
           Crimson Tide since 6.19.0, from the teams' rosters; on a
           narrow screen the position shortens to QB and the number
           stays) and his line
           in every table he is in - PASS 17/24, 206 YDS, 3 TD;
           RUSH 8 CAR, 25 YDS; DEF 9 TKL, 1 SACK - in his photo in
           Kitty or Ghostty
baseball   THE DIAMOND: runners in the batting team's colour, the
           count, balls, strikes and outs, the pitcher's and the
           batter's day so far, who is on which base, the last pitch;
           after the final, SCORING PLAYS in its place; BY INNING
           over it; PITCHING under the home team's logo - each
           team's pitchers in the order they came in, innings,
           hits, runs, earned runs, walks, strikeouts and pitches,
           W, L and S marking the decisions
basketball under the scores while the game is on (NBA, college,
           since 6.19.0) a TV-style scorebug under each score: P
           when that team has the ball, its FOULS this quarter (this
           half in college) and BONUS when the other side has fouled
           enough to send it to the line (2X BONUS in college from
           the other side's 10th foul), with each team's timeouts
           left under its logo (● left, ○ used) - all worked out
           from the play by play
           every part on a card of its own: SHOT CHART, each
           team's shots on its own half court (● made, ○ missed);
           BY QUARTER (BY HALF in college) over THE GAME - the run
           (points unanswered), lead changes and ties, the biggest
           leads, team fouls this quarter (half), points in the
           paint and on the break, turnovers; TOP PERFORMERS in the
           room under the home team's logo - each team's best by
           game score with his line, foul trouble flagged while the
           game is on, each team's best in his photo in Kitty or
           Ghostty; then WIN PROBABILITY across the screen, and TEAM
           STATS beside LAST PLAYS. Before tip-off: THE MATCHUP and
           SEASON LEADERS
hockey     SHOTS ON GOAL, the rink from above: every shot on goal
           (•) and goal (●), the away team shooting at the left net
           and the home team at the right (the AHL's shots come from
           its own play by play); BY PERIOD over THE GAME - shots,
           who is on the power play, power plays, faceoffs, hits;
           GOALS under the home team's logo - period, time, team,
           scorer, PP, SH or EN and the assists - over GOALIES,
           each one's saves. The Olympics have no shot locations,
           so there THE GAME BY PERIOD, the goals on a timeline,
           runs across the screen instead
soccer     THE MATCH, the timeline from kick-off to the final
           whistle (extra time too): goals (●) and cards (▮) above
           the line for the away side, below it for the home side;
           possession as a two-colour bar, shots and shots on
           target, corners, fouls, saves and offsides under it;
           GOALS and CARDS under the home team's logo; the minute in
           big digits
football   after the final: the drive chart stays, and SCORING
           SUMMARY - every score with its quarter, team, kind and
           the score after it - takes the drive's place beside the
           team stats (in the field's place when there is no chart)
win odds   WIN PROBABILITY across the screen: ESPN's live chance
           as a meter in the two teams' colours (LED segments, or
           whichever meter look Settings picks; since 6.16.0), the
           away team's share from the left, the home team's from
           the right, a │ where they meet; and the whole game's
           swing as a line under it
below      TEAM STATS as two-colour bars on the left (the score by
           quarter, period, inning or half over them when there was
           no room up top); LAST PLAYS on the right (football: DRIVE,
           the current one; soccer: COMMENTARY)
```

Every score flashes a banner across the screen in the scoring team's colours - TOUCHDOWN, FIELD GOAL, EXTRA POINT, GOAL, RUN SCORES - and FINAL when it ends. Before the start the middle counts down to kickoff, tip-off, puck drop or first pitch, and under it are THE MATCHUP - the line, ESPN's predictor, the weather, the probable pitchers, each team's form, the venue and the TV - and SEASON LEADERS. After the final it keeps the result, the line score, the stats and the last plays (the game's leaders when there are none).

j / k (or h / l, the arrows, or the mouse wheel) step through that day's other games without leaving the Game Center; enter opens the game's box score (its scouting report before the start); R refreshes; X stops a clip that is playing; esc, Q or Z closes; ? and I open the key list and the Info pop-up over it. It needs 50 columns by 10 rows and uses everything above that: the big digits, the field, the court, the rink and the win-probability line grow with the terminal, and below about 30 rows the sport's picture gives way to the score, the line score and the plays. The cards make room the same way: a short screen gets a smaller shot chart or rink, then no top row (the score by period moves over the team stats), then no win probability; TEAM STATS and LAST PLAYS always stay. The card under the home team's logo needs about 110 columns in football (104 in baseball, 100 in soccer, 82 beside hockey's numbers); basketball's TOP PERFORMERS needs about 125, and without it each side's top scorer moves into THE GAME.

**TOP PERFORMERS** (basketball, since 6.12.0) ranks each team's players by game score, John Hollinger's one-number box score (points + 0.4 × field goals made − 0.7 × field goals tried − 0.4 × free throws missed + 0.7 × offensive rebounds + 0.3 × defensive rebounds + steals + 0.7 × assists + 0.7 × blocks − 0.4 × fouls − turnovers), the same measure as the Boxscore's top performers: up to four a team, each with his game score and his line (points, rebounds, assists, steals and blocks when he has two, field goals). While the game is on, a player two fouls from fouling out (four in the NBA, three in college) shows his fouls in amber, one foul away in red, and a player who has fouled out says so. On a narrower card a line keeps points, rebounds and assists. In Kitty or Ghostty each team's best is in his photo beside the team (ESPN's headshot).

**The Event Center.** On the Olympic sports Wikipedia covers - swimming, athletics, skiing, curling, tennis and the rest - Z on an event opens its Event Center instead: the event's name across the top, the podium in gold, silver and bronze with each medallist and nation in its colours (team events name the nation), the final's table and the event's facts (venue, dates, competitors, the winning time or mark). j / k step through the sport's events and enter opens every round's results.

### The BottomLine

A ticker on the row above the bottom line, like the one along the bottom of a sports channel: one league at a time behind its name, a new page every five seconds, your teams' games first under ★ YOUR TEAMS. A game reads away team first, like `KC 24 BUF 21 2:13 4th`, `MSU 10 9 UCLA 28 F` (9 is UCLA's ranking) or `HOU ATL 7:30p`. The page count sits at the right end (4/14). Click a game on it to open it, as on the Today list. Settings → Game day → BottomLine ticker: auto (the default) shows it on terminals 30 rows or taller, on always, off never.

### The live wire (every league)

While the league you are looking at has a game on - and for five minutes after the last one ends - a crawl runs right to left across the row above the BottomLine, behind a NHL LIVE (CBB LIVE, NFL LIVE …) bug, the way a broadcast's crawl does. College shows the ranked games and your teams'. In hockey:

```
 NHL LIVE   GOAL  COL  N. MacKinnon (12), power-play goal, from C. Makar  puts them ahead   COL 2  CBJ 1  12:34 2nd  ◆
```

News goes first, newest first, and stays on it for fifteen minutes (a power play for two, a puck drop for five): **GOAL** (the scorer and his goals this season, how - power play, short-handed, into the empty net, on a penalty shot - who set it up, whether it tied the game or put them ahead, a HAT TRICK, and the score after it, and the time into the period, as on the scoresheet), **POWER PLAY** (who, and the time left), **EMPTY NET** (a goalie pulled for an extra attacker in the third period or overtime, his team behind; not the few seconds of a delayed penalty), **FIGHT**, **MAJOR**, **GAME MISCONDUCT**, **MATCH PENALTY** and **PENALTY SHOT**, **PUCK DROP** (with the channels carrying it), **OVERTIME** and **SHOOTOUT**, **▲ UPSET WATCH** (an underdog by the betting line in front, section 13) and the **FINAL**. A new item goes on just past the right edge, so it is the next thing on. Then every game being played, with PP and the team and time left on a power play, tonight's finals and the games still to come.

The other sports get their own news, the same way:

```
 CBB LIVE   RUN  UK  on a 12-0 run  MAN 38  UK 61  8:12 2nd  ◆  FINALS  WOF 59  TENN 90  ◆
```

- **Basketball**: TIP-OFF (with the channels), a **RUN** of 10-0 or more, a **COMEBACK** (back in front from 15 down in the NBA, 12 in college), a **LEAD CHANGE** or **TIED** in the last five minutes, a **CLOSE FINISH** (two minutes left, three points or fewer), a **BIG NIGHT** (30, 40, 50 points in the NBA; 25 and up in college) and **OVERTIME**; a run of eight or more shows beside its game.
- **Football**: KICKOFF, **TOUCHDOWN**, **FIELD GOAL** and every other score, **RED ZONE** (who has the ball, the down) and **OVERTIME**; beside each game who has the ball and the down.
- **Baseball**: FIRST PITCH, **RUN SCORES** (2 RUNS SCORE …), a **NO-HITTER WATCH** from the sixth on, **EXTRA INNINGS**.
- **Every sport**: ▲ UPSET WATCH, and in college **▲ UPSET ALERT** when an unranked team (or one ten places lower) leads a ranked one in the second half; ▲ UPSET and the FINAL.

Click an item to open its game. The NHL's items come from its own scoreboard and game centers (api-web.nhle.com), the AHL's from HockeyTech, the other leagues' from ESPN's scoreboard; they are read every 20 to 60 seconds while games are on. Settings → Game day → Live wire turns it off.

### Score alerts

Your favorite teams' games are watched in the background whatever you are looking at, in any league. When one starts, when someone scores and when it ends, a line in gold takes the bottom line: `★ BUF TOUCHDOWN! BUF 21, KC 24 · 2:13 4th`, then `★ FINAL: BUF 28, KC 24 - BUF win`. Basketball would alert on every basket, so it says CLOSE FINISH once instead, when a game is within five points in its last two minutes. Settings → Game day turns the alerts off, or rings the terminal bell with each one.

**The banner (since 6.13.0).** When one of your teams scores, a banner takes the BottomLine's row for three seconds, flashing between the team's colours and gold every quarter second - `★  TOUCHDOWN ARKANSAS  ★` - and then the ticker comes back. Football says TOUCHDOWN, FIELD GOAL or SAFETY and the team (an extra point or a two-point try flashes nothing); hockey and soccer DETROIT GOAL; baseball ST LOUIS HOME RUN (GRAND SLAM, when the scoreboard's last play says so), else ST LOUIS RUN or ST LOUIS 2 RUNS. Basketball scores too often, so only a made three flashes - OKC THREE - read from the game's play by play. Teams go by their place (ARKANSAS, TENNESSEE, ST LOUIS, DETROIT), or by their abbreviation when the place is long (OKC). Two scores at once flash one after the other. When the ticker is not shown, the banner takes the live wire's row, or the bottom line. Settings → Game day → Flash your teams' scores turns it off; the score alerts must be on.

### The mouse

Click a tab to open it; click a game, a team (on the Overview, Standings, Stats and Favorites tabs), a title on the Settings tab or a setting on its card to pick it, and click it again (or double click) to open it, as enter would. A row of the Television Schedule picks its game the same way; an item on the BottomLine or the live wire opens its game at once. A menu item or a calendar day is chosen with one click. The wheel moves through the list under the pointer - or scrolls the pane under it: the game detail beside the Scoreboard, the books under the Betting list, an About sportst card. A click outside a menu, a card or the calendar closes it; a click closes help and the I pop-up. While the mouse is on, the terminal leaves text selection to shift: hold shift and drag to select. Settings → Game day → Mouse turns it off.

### The calendar (C, on any tab)

A month calendar pops out over whatever you are looking at. Days with games in the league on screen are lit (on a tint of the scheme's colour, with a dot); days one of your favorite teams plays carry a ★; today is underlined, and the day on screen now is in [brackets] - in football's week view, every game day of the week on screen, the calendar opening on the first. Under the month, the highlighted day is spelled out with your teams' games on it - opponent and start time, or the result.

```
← → (h l)        a day back / forward
↑ ↓ (k j)        a week
[ ]  PgUp PgDn   a month (< > and , . too)
n N              the next / previous day with games
F                your teams' next game
T                today
enter or space   go to that day
esc, Q or C      close
```

Going to a day opens that day's games. On a game's tabs (Scouting, Boxscore, Game Stats, Plays, Betting) you stay put and the first game of the day - or your team's, when it plays - is the one shown; from Overview, Standings, Stats, Playoffs, Favorites and Settings the Scoreboard opens. Football switches to day view for the date; W goes back to weeks. Game days come from ESPN's season calendar (for football, that month's schedule) and HockeyTech's season schedule for the AHL; your teams' days from each team's own schedule. The Olympic sports already show their whole schedule, so C does nothing there.

### The bottom line

Next to the name and version, the bottom line always lists the keys that matter on the screen in front of you - j/k game, enter open, h/l week, c conference, U upset, R refresh and so on - changing as you move between tabs, a team's players, Settings and pop-ups. Messages take the right-hand end; when one needs the room the last hints step aside.

A key shown as a capital works in either case: U and u both jump to an upset, R and r both refresh, so Caps Lock never gets in the way. The small letters that stay small - c g h j k l n o s - are the ones whose capital is a different key (C calendar, G end, H Overview, J K scroll, L next league, N previous clip, O Settings, S next sort column), and in a Settings card R puts a setting back to its default rather than refreshing.

### Info (I, on any screen)

A pop-up that explains the screen you are on: every column heading and abbreviation, every symbol and colour, how each number is worked out (the Betting tab's edge, stars and stake included), and the sport's own terms. It is built for the screen in front of you - the league, the game, the player view, a team's page, the Game Center - and the box-score and standings abbreviations come with ESPN's own descriptions. j / k scroll it, any other key closes it (every key, when it all fits).

The Olympics add Medals, swap Playoffs for Medal Round and have no Betting tab (no sportsbook feed covers them); the sports Wikipedia covers have their own screens between Overview and Settings. See section 5.

## 7. Scouting reports

Highlight a game that has not started on the Scoreboard and press enter, or press 2 at any time. Every league has it, the Olympic tournaments included. The screen is two panes, each scrolling on its own since 6.22.0 (one stacked pane on a narrow terminal).

### Left pane - the matchup

The start time, venue and TV; the betting line; ESPN's matchup predictor; the forecast for outdoor games; the season series.

Stat edges counts how many season stats each team ranks better in, and how many of those are big gaps.

Matchup advantages to watch lists the places one team's strength meets the other team's weakness - a top-five rushing attack against a bottom-ten run defence, a hot power play against a leaky penalty kill - strongest first. Each is printed in the team's colour; a filled triangle marks the biggest ones. Ranks are league-wide (#1 of 32 in the NFL, #1 of 365 in college basketball).

Below that, every season stat side by side, grouped into Offense, Defense, Special teams and so on: each team's number and league rank, with the better number lit in that team's colour. An orange arrow points at the side of a big gap (a third of the league or more apart).

### Right pane - each team

Form: the last five results (in basketball a table of them from the team's schedule, newest first: the opponent, the score and the margin, with the run and the average margin). Season leaders (passing, rushing, receiving, sacks, tackles; points, rebounds, assists; goals and points; batting and pitching). The full injury list from the team's roster, grouped Out, IR, Doubtful, Questionable, Day-to-day. The latest headlines from ESPN's team news, with their age - the team's own news, not the league-wide roundups ESPN tags with every team - with ▼ in red on bad news (ruled out, hurt), ▲ in green on good (back, activated) and an orange ▶ before a video.

The AHL report comes from the league's own game preview instead: last ten, streak, home and road records, power play and penalty kill (home and road too), leading scorers, players on a point streak, the top rookie, records when leading or trailing after two, and the season series.

Before a season's first games the season numbers are last season's where the source still serves them; the records read 0-0. College teams rarely publish injury reports, so an empty list there means "none listed".

### Reading a headline: the article card

Every headline in the report can be opened. Press n to light up the first headline (n again for the next, N for the one before - both teams' headlines, top to bottom, round and round) and press enter: the article card opens over the report with the whole story - the headline, the byline and when it was posted, then the story itself, paragraph by paragraph, with its headings, lists and quotes. Pictures, embedded players and ads are left out. The mouse works too: click a headline to pick it, click it again (or double-click) to open it.

In the card, j / k scroll a line, space or PgDn a page, G and Home jump to the end and the top. o opens the story on espn.com in your browser. n / N go straight to the next or previous headline without closing the card, and esc, Q, backspace or a click closes it.

A ▶ headline is a video: the card shows what it is and how long it runs, and enter plays it with your clip player, the same one the Plays tab uses - mpv, ffplay or VLC, sound only unless Settings has Show the video on (section 6, Scoring-play clips). A story that carries a video says so at the top, and enter plays that one. X stops it.

The story comes from ESPN's content API, free and keyless like every other source (section 20); sportst lays the HTML out itself, so no text browser - w3m, lynx - is needed. A few items have no text to show (an interactive page such as bracketology, or a gallery): the card says so, and o opens them in the browser. An ESPN+ story is marked ESPN+; if ESPN sends only its opening, the rest is on espn.com for subscribers.

## 8. The Stats tab, Top 25 and conference filters

The Stats tab (7) puts every team in the league on one screen: a row per team, a column per season stat, with the league's best fifth in green and worst fifth in red. As many stat groups as fit sit side by side - on a wide terminal, offense and defense together. The # column is the team's league rank in the column you sort by. ] and [ narrow it to one conference or division at a time (see "One conference or division" below). The top line and the two header rows stay put while the teams scroll.

The pro leagues (NFL, NBA, NHL, AHL, MLB) list every team grouped by league and division, the way the standings are laid out - a heading for each league or conference (American Football Conference, American League, Eastern Conference ...), the division's name over its teams, and the teams best-first inside each division by the sort column:

```
   #  team                         record PTS▼    YDS   PASS ...
── American Football Conference ──────────────────────────────
   AFC East
   1  Buffalo Bills                   5-1 32.8  399.5  238.8 ...
  17  New England Patriots            4-3 22.9  383.4  253.0 ...
```

College football, basketball and baseball rank the whole league best-first, with a conf column naming each team's conference, and add the Top 25 filter. s switches either way: by league and division (or by conference), best-first across the whole league, or A-Z.

### Players

j / k move the highlight down the teams; enter opens that team's player statistics for the season:

```
left     offense - football passing, rushing and receiving;
         basketball scoring per game; hockey scoring; baseball
         batting
right    defense - football tackles, sacks, TFL, passes defended,
         interceptions, forced fumbles; basketball rebounds,
         steals, blocks, fouls; hockey goaltending and plus-minus,
         ice time and penalty minutes; baseball pitching
bottom   special teams - football kicking, punting and returns;
         hockey power play, short-handed and faceoffs; basketball
         minutes and usage; baseball fielding
```

[ and ] step to the previous or next team in the table's order, j / k scroll, and esc (or enter or backspace) goes back to the table. The numbers come from ESPN's team-stats pages (the AHL's from HockeyTech); the Olympic tournaments publish none.

### Season, last game, schedule

g steps the player screen through the whole season, the team's last game and its team page, and back round. The last game is the most recent one completed - in the postseason, regular season or preseason, whichever is latest, or last season's final game before a new one starts - named at the top right ("Sat Oct 17 · W 31-21 at VAN"). Its box score is laid out the same way: offense left (passing, rushing, receiving and fumbles; points, shooting, assists and turnovers; goals, assists, shots and ice time; batting), defense right (tackles, sacks and interceptions; rebounds, steals and blocks; goaltending, blocks, hits and takeaways; pitching), special teams underneath (kicking, punting and returns; power-play and short-handed ice time and faceoffs). Players who did not record anything are left out, bench players are dimmed, and each table ends with the team's total. [ ] keep whichever view you are in. College baseball has no team schedule at ESPN, so its last game and schedule are on the Scoreboard and the calendar instead.

The schedule is the team's page (section 6, Standings): its whole season, one game a line, opening on the game under way or the next one, with the season at a glance beside it on a wide terminal (V switches to it on a narrow one):

```
 WEEK    DATE        OPPONENT              RESULT        RECORD   TV
 Wk 6    Sun Oct 18  at Falcons            W 31-23       4-2
 Wk 7    Thu Oct 22  vs Patriots           W 30-24       5-2
▌Wk 8    Mon Nov 2   at Seahawks           7:15 PM                ESPN
 Wk 9    Sun Nov 8   vs Buccaneers         7:20 PM                NBC
 Wk 10   BYE
```

Football numbers the weeks and shows the bye; every other sport puts the month over its games. A result reads W 27-20 OT, the team's score first, with the record after that game beside it; a game to come shows its start time in your time zone and its TV network; postponed games say so. In the playoffs the record column follows the series instead: up 2-1, tied 2-2, won 4-2. j / k pick a game (J / K ten at a time) and enter opens it - its scouting report before the start, its box score once it is under way or played - Z puts it in the Game Center, and T jumps back to the next game. It comes from ESPN's team schedule (HockeyTech's for the AHL); ESPN's default season part (preseason, regular season or postseason) gets the regular season added, so the postseason and the season it followed are on one list.

```
g        next stat group.  On a wide terminal everything fits side by
         side; on a narrower one g steps through the groups (Offense,
         Defense, Special teams, Batting, Pitching, Fielding ...),
         showing as many neighbours as fit, then all of them.
[ ]      one conference (college) or division (pros) at a time: ] shows
         the next one and only its teams, [ the previous; stepping
         past the last comes back round to All teams
c        pick the conference or division from the full list
s        pick the column to sort by from a list; best is always first,
         so for points allowed or ERA the lowest is #1.  The same list
         orders the teams by league and division (the pros' default),
         by conference, best first across the league (college's
         default) or by team name A-Z, and its "Only one
         conference" entry opens the c list
S        sort by the next column (in the s list too)
/        find a team by name: "new york" leaves the Giants and the
         Jets; an empty search shows everyone again
```

### One conference or division

The top line of the Stats tab always says what is on screen:

```
◂ SEC ▸  Southeastern Conference · 16 of 138 teams
```

] and [ step through the league's conferences or divisions in the order the c list shows them - for the NFL: AFC, AFC East, AFC North ... NFC West; for the NHL: Eastern Conference, Atlantic, Metropolitan, Western Conference, Central, Pacific; for college: every conference, A-Z - and only that group's teams are listed. # then becomes the team's place within the group in the sort column, and lg beside it its rank in the whole league; green and red still mark the league's best and worst fifth. The conf / div column drops out when every team on screen shares it. The choice also filters the Scoreboard, Standings and Betting tabs, as c always has, and it is kept per sport while the app runs.

### What the columns are

```
Football    points, yards, passing and rushing yards, yards per carry
            and per pass, completion %, passer rating, third downs,
            sacks allowed, giveaways; the same allowed by the defence
            plus sacks, interceptions and takeaways; field goal and
            extra point %, net punting, kick and punt returns,
            penalty yards.  All per game.
Basketball  points, FG%, 3P%, threes made, FT%, assists, offensive
            rebounds, turnovers; opponent points, FG% and 3P%,
            rebounds (all and defensive), steals, blocks, forced
            turnovers; margin and
            assist-to-turnover ratio.
NHL         goals for and against, shots for and against, shooting
            and save %, power play and penalty kill, power-play goals,
            faceoff %, shutouts, short-handed goals, penalty minutes.
AHL         points %, goals for and against, power play and penalty
            kill with their goals, short-handed goals for and
            against, penalty minutes.
MLB         runs, AVG, OBP, SLG, OPS, home runs, steals and strikeouts
            per game; ERA, runs allowed, WHIP, K/9, BB/9, HR/9 and
            opponent average; fielding % and errors.
College     runs per game, AVG, OBP, SLG, home runs per game, ERA,
baseball    WHIP and fielding % for every Division I team (NCAA.com).
Olympics    win %, margin, goals or points for and against.
```

### Top 25 and conferences

On the Scoreboard and the Stats tab, c opens a list of the league's conferences and divisions:

```
College football, basketball, baseball   every conference (SEC,
                                         Big Ten, ACC ...), plus
                                         divisions where one has
                                         them
NFL                                      AFC, NFC and the eight
                                         divisions
NBA, NHL, MLB                            both conferences or
                                         leagues and their divisions
AHL                                      the four divisions
```

Pick SEC and the scoreboard shows only games with an SEC team in them, and the Stats tab only SEC teams. "All teams" clears it. The choice is kept per sport while the app runs, and shows in the top-right corner ("· SEC").

In college football, basketball and baseball the **Top 25** is a conference of its own (since 6.17.0; it was the F key): first under Conferences on the c list, and the first stop after All teams for [ ]. It is the ranked teams - the AP poll for football and basketball, the D1Baseball.com Top 25 for college baseball: on the Scoreboard and the Betting tab the games with a ranked team in them, on the Stats tab the ranked teams, and on the Standings tab one table of them in the poll's order.

College baseball's table is read from NCAA.com a page at a time, so the very first load takes up to a minute; after that it is kept on disk for 12 hours. ESPN's college baseball standings cover a handful of conferences, so the rest are filled in from each school's basketball conference; a few schools play baseball in a different one.

## 9. The Betting tab and value picks

Tab 9 lists every game on the current day (or football week) that has not started, one line each, with the selected game's detail underneath. Since 6.21.0 the detail is built to fit a screen (at 190x48 it does, all but the fine print): the list takes a quarter of the screen (it scrolls with j / k); the public sits beside the tale of the tape; the bets without an edge share one line; the margin odds (or hockey's score odds) and how the day's lines did each go in whichever pane keeps the two shortest; and the keys and the fine print come last, under the shorter pane. The same filters work here: c for a conference or division (in college sports the Top 25 is one of them), and h / l to move the day or week.

### The list, left to right

Columns: # (a value pick's rank), time, game, spread (the favourite's number and price), total, moneyline (away/home), win% (the market's chance for the favourite, vig removed, then sportst's), proj (projected score, away-home), bets·$ (the side most bettors are on: % of bets · % of money, lit when the money runs 10 points ahead of the bets), move (how far the line has moved since it opened: ▲ the favourite got stronger, ▼ weaker, ◆ the favourite flipped), best bet, edge, the ★★★☆☆ rating (out of five) and stake. Columns drop away, least useful first, on a narrow terminal.

### Which lines (B)

```
Top-3 average   FanDuel, DraftKings and BetMGM averaged - spreads and
                totals to the nearest half point, prices averaged as
                probabilities.  The default.
Best price      every bet checked at every book, and the best price
                shown with the book's name (FD, DK, MGM, CZR, 365, BR,
                BOV).  This is line shopping, the one edge anyone can
                take.
One sportsbook  FanDuel, DraftKings, BetMGM, Caesars, bet365,
                BetRivers or Bovada alone - the lines you would
                actually get at your book.
A book's total, spread or moneyline far from every other book's
(a different market filed under the game, like a 16.5 "total"
for an NBA game) is left out, so it cannot skew the average or
pose as a huge edge.
The choice is saved.  Change the three averaged with
"betting_top_books" (section 17).
```

### The detail

Left: every book's spread, total and moneyline (the best moneyline price in green), Action Network's consensus and the opening line, Kalshi's prediction-market price and how much has traded on it, and the public's share of bets and of money on each side of each market.

Right: sportst's read - the projected margin, win chances and score; the four estimates behind it with their weights; the adjustments; the market signals; and every bet with sportst's probability, its edge and a rating, then why the pick was made (the signals for and against). Since 6.21.0 the bets without an edge share one line, each with its edge (their prices are in the books' table on the left).

### How sportst projects a game

The margin is a weighted blend of four estimates:

```
Market          55%   the consensus spread (or, in hockey and
                      baseball, the no-vig moneyline)
Kalshi          15%   the prediction market's price
ESPN predictor  15%   ESPN's matchup predictor (FPI / BPI)
Season stats    15%   each side's scoring for and against, the
                      home edge, and the adjustments below
```

The market carries the most weight because it is the hardest number to beat. The season-stats estimate is adjusted for what season numbers cannot know: a team's season leaders on the injury report (a starting quarterback is worth about 4 points; others less, scaled by Out / Doubtful / Questionable), back-to-backs in the NBA and NHL, short weeks and byes in football, recent form against the season average, and for outdoor football totals, wind, cold and rain. Each team's numbers are shrunk toward the league average until it has played enough games to trust them.

Win and cover chances start from the market's own no-vig probability and move only as far as sportst's margin differs from the market's, so sportst never disagrees with the market by accident of arithmetic. Totals work the same way: the market's total, nudged toward the season numbers and the weather.

### Value picks and the stars

A bet's edge is its expected return per $1 at the price shown: sportst's probability times the payout, minus the stake. A bet is a value pick when its edge clears "betting_min_edge" (3% by default), and every value pick is rated out of five stars - up to three for the edge:

```
★☆☆☆☆   edge at or above 3%
★★☆☆☆   6% or more
★★★☆☆   10.5% or more
```

and up to two more for the independent signals - Kalshi, ESPN's predictor, the season numbers, sharp money (money running well ahead of bets), reverse line moves (most bets on one side, the line moving to the other) and line moves:

```
+★★     three or more agree and none disagree
+★      more agree than disagree
-★      more disagree than agree
```

So five stars is an edge of 10.5% or more that everything sportst reads agrees with, and a 3% edge the signals all back is worth as much as a 10.5% edge on its own. Moneylines at +300 or longer are never picked, and an edge over 15% or a price of +200 or more is held to two stars: at those prices a big edge usually means news the model has not seen. The stars are drawn out of five everywhere they appear - ★★★★☆ - with the ones a bet did not earn hollow.

Stake is an eighth of the Kelly-criterion stake, in units of 1% of a bankroll, capped at 2 units - deliberately small, because the edges are estimates.

A game's best bet is the one with the most stars, then the biggest edge. The list opens with the value picks first, ranked best to worst - most stars, then the biggest edge - each numbered in the # column and lit on an orange band so they are the first thing you see; the other games follow, best remaining edge first. s switches to plain start-time order (the picks keep their rank numbers and highlight) and back; M shows value picks only; enter opens the game's scouting report, where a one-line summary of sportst's read also appears.

### Ask Kim ($)

Press $ on the Betting tab and a pop-up opens with an 8-bit portrait - pixel art drawn for its size: the big hair, the big glasses, the grin and the high collar, two pixels to a character with half blocks, in 14 exact colours, with three mouths for talking - beside a comic-book speech bubble: a solid yellow outline around the colour scheme's own dark background. While Kim thinks, the dots go round; then his mouth moves while the bubble types out the three best bets of the week, scrolling along like an old console's text box. Kim does not explain himself - he just knows. (Kim is a parody character, for fun; see section 23.) In Kitty or Ghostty the portrait is his original 8-bit picture instead, in the NES palette, pixel for pixel, its mouth moving the same way (section 14).

```
KIM'S PICKS · NBA · NOV 5 – NOV 11

1  UTAH ML +165 · avg FD·DK·MGM  ★★★★★
   LAL @ UTAH · Sun 4:00p
   "You bet now!"

2  BKN +7.5 -102 · avg DK  ★★★★☆
   DET @ BKN · Fri 6:30p
   "Approved unanimously, as always."

3  Over 228.5 -110 · avg DK  ★★★☆☆
   MIA @ ORL · Sat 6:00p
   "A glorious bet, inspected by Kim."
```

Each pick is the bet, its price, the book (or the books averaged, as chosen with B) and its stars out of five - or lean, for a bet with no star - then the game, when it starts, and Kim's decree. His number one pick - the best bet of his week - is the one he says "You bet now!" about, and he never says it about anything else (nor about a lean). The others get a decree for their stars:

```
★★★★★   "So decrees the Supreme Leader."
★★★★☆   "Approved unanimously, as always."
★★★☆☆   "A glorious bet, inspected by Kim."
★★☆☆☆   "Kim permits the people this bet."
★☆☆☆☆   "A modest bet for loyal citizens."
lean    "A lean. The revolution waits."
```

There is a second decree at each level, for when two picks share a rating. The week is football's current week, or today and the next six days in the other leagues. When fewer than three bets clear his bar, he gives fewer.

Behind the curtain it is the same model as the rest of the tab, run over every game in the week that has a line with each game's ESPN file - the injury report against the season leaders, form, rest, ESPN's predictor, the weather, every book's line, the public and sharp money and Kalshi - and the best bets are read against the league's news wire from the last 72 hours. One bet a game, the one with the most stars; Kim ranks them the same way - the most stars first, then the biggest edge with the most signals for it - and the news can move a pick within its star rating or knock it out, but never past a pick with more stars. An edge over 15% or a price of +200 or more is skipped, because at those numbers the model is usually missing something.

```
enter    skip the talking; enter again closes
j k      scroll the bubble
R        ask again - fetches everything fresh
esc Q $  close
```

The pop-up keeps to about half the screen: the small portrait beside a bubble up to 42 columns wide, 77 x 21 at most; a terminal smaller than 71 x 23 gets the bubble alone. sportst --kim -L nfl prints the same picks - the portrait and the bubble side by side in colour, the words alone in a pipe. These are estimates, not guarantees.

### Coverage

NFL, college football (FBS), NBA, men's college basketball (Division I), NHL and MLB get every book, the public numbers and Kalshi. College baseball gets ESPN's single line where it has one; the AHL has no betting feed, so it gets sportst's projection only. Lines usually appear a few days before a game; early-season college basketball and far-off games may have none yet.

### Please bet responsibly

These are statistical estimates for entertainment, not guarantees and not betting or financial advice, and no model beats the market every week. Bet only what you can afford to lose, and only where sports betting is legal for you and you are of legal age. Help is available at 1-800-GAMBLER. See section 23.

## 10. Baseball: the Plays screen

Select an MLB, Minor League, college baseball or college softball game and press 5. The screen splits in two. In Kitty and Ghostty (since 7.0.0) the diamond is a picture - the grass, the dirt, the bases with a runner's on each one taken, the mound - and so is the strike zone, a TV broadcast's: the zone's nine boxes, the plate below it, each pitch a numbered ball in its colour. Elsewhere both are drawn in text, as below.

Left, the live picture:

```
Top 7th        CHC 3  -  BOS 4
```

```
   o          2-1  count    OO. outs
*     o       third: C. Wong
   home
```

```
P  Aaron Civale            AB  Adley Rutschman (L)
```

```
This at-bat
  1  92 mph  Four-seam FB   Strike Looking    0-1   2,388 rpm
  2  86 mph  Splitter       Foul Ball         0-2   1,937 rpm
  3  79 mph  Curve          Ground Out        0-2   3,148 rpm
       97 mph off the bat   0 degree launch   40 ft
```

Rutschman grounded out to second, Wong to third.

Recent plays ...

A filled diamond is an occupied base, and the runner's name is beside it. The count and the outs come from the live game state while a game is in progress, and from the play stream otherwise.

Right, the strike zone as the catcher sees it, with every pitch of the at-bat numbered in the order it was thrown and coloured by what it was:

```
red      called strike
orange   swinging strike
green    ball
gold     foul
blue     in play
```

The box is the rule-book zone. For MLB it is the zone measured for that batter's stance on that pitch; college baseball has no such measurement, so a standard zone is drawn instead. Under the zone: how many pitches, the fastest and average speed of the at-bat, the fastest pitch of the game, the hardest ball hit, then home runs and everything that happened on the bases - steals, caught stealing, pick-offs, wild pitches, balks.

Press , and . to step back and forward through the at-bats. The screen always opens on the most recent one, and returns to it when you step past the end.

What each league gives you:

```
MLB               pitch type, speed, location, spin rate, exit
                  velocity, launch angle, distance, per-batter strike
                  zone, count, outs, runners, steals
Minor League      the same from MLB's Stats API (7.0.0): type, speed
                  and location of every pitch, the zone for each
                  batter, and spin and the ball off the bat where the
                  park tracks them (Triple-A's do)
college softball  as college baseball, seven innings (7.0.0)
college baseball  pitch location, result, count, outs, runners,
                  steals, hits.  No speeds or spin: nobody publishes
                  Statcast for college baseball.
```

Set "mlb_statcast": false in the config to skip MLB's feed and use ESPN's numbers alone. You lose spin rate, exit velocity, launch angle, distance and the per-batter zone; everything else stays.

## 11. Basketball: the shot chart

Press 5 (Plays) on any basketball game - the NBA, the WNBA, men's or women's college basketball. In Kitty and Ghostty (since 7.0.0) the court is a picture: hardwood, the painted lane in the home team's colour, the arc, the circles and the rim, every shot a ring or a dot in its team's colours. Elsewhere it is drawn in braille, as here. The left pane is the game's flow, its biggest runs and the game; since 6.22.0 the **scoring plays** by quarter (or half, in college) with the running score are hidden until **s** shows them - then they are the whole left side, j / k picking one, and s hides them again. The right pane is the shot chart:

```
⡏⠉⢹⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⢹⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⢹⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⠉⢹⠉⢹
⡇●⢸           ⢸    ⣀⣀⣀●⣀⡀   ⢸           ⢸●⢸
⡇●⢸ ○         ⢸   ●●●●●○⢀⡆  ○      ●    ⢸●⢸
⡇●⢸ ○      ○● ⢸   ●○●○●⣠●○  ⢸ ○         ⢸●○
⡇○⢸           ⢸     ●○⠉ ●   ⢸     ●     ⢸ ⢸
⡇ ⢸           ⢸  ○ ●● ○    ○⢸           ⢸○⢸
⡇●⠘⡆          ⢸ ○   ○   ○ ○○⢸○          ⡞ ⢸
⡇  ⠘⣆     ○   ⢸         ● ● ⢸○        ⢀⡞  ⢸
⡇  ○⠈⢢⡀  ○    ⠘⠒⢲⠒⠒⠒⠒⠒●⠒⠒⠒⢲⠒⠚ ●      ⣠●   ⢸
⡇     ○⢤⡀       ●⢆  ●    ⢀○    ●   ⣠●⠁○   ⢸
⡇     ● ⠙⠦⣀       ⠑⠤⣄●⣀⡤○⠁      ⢀⡠⠞●●     ⢸
⡇       ○ ●⠑⠲⢄⣀             ⢀⣀⠴⠒⠉○●       ⢸
⡇         ○ ●○○⠉○⠒⠒⠤⠤⠤⠤⠤⠔⠒⠒⠉⠁○●●●         ⢸
⡇               ○ ●○ ○●○●   ○             ⢸
⡇                                         ⢸
⡇                       ○   ○             ⢸
● made  ○ missed   SA 36/86   NY 36/78
```

The basket is at the top. ESPN records where every field-goal attempt was taken from, in feet, and both teams are put on the same half court. The court is drawn to regulation: the NBA's 23-foot-9 arc and 16-foot lane, college's 22-foot-1¾ arc and 12-foot lane, FIBA's for the Olympics. Free throws have no location and are left out; heaves from beyond 31 feet are counted under the chart instead of drawn.

Where two shots land in the same character cell, a make wins over a miss, and the team with more shots there gives the colour. Press V for one team at a time when both teams' colours are close.

By zone, under the chart:

```
Rim        within 4 feet of the basket
Paint      the rest of the lane
Mid        every other two-point attempt
Corner 3   threes from below the point where the arc meets the
           straight corner line
Arc 3      every other three
```

The court lines are drawn in braille dots, which put two by four dots in each character cell. Braille has been in Unicode since 1999 and Linux terminals fall back to a font that has it even when your own font does not, so it draws cleanly almost everywhere. If you see boxes instead, set "court_lines": "dots" for plain middle dots.

Over the scoring plays, the **game flow**: the score margin from the tip to now in braille, the home team's lead above the line in its colour and the visitor's below in its own, with each side's biggest lead at the end of the scale, a tick at each quarter (or half) and the lead changes and ties counted under it. Then the game's **biggest runs** - eight points or more without an answer - with when each started and ended. j / k pick a scoring play; its shot is ringed (◉) where it was taken on the chart.

## 12. Playoffs

Press 8 (the Medal Round tab in an Olympic tournament). Rounds run left to right, each series wired back to the ones it came from - the wire leaves from the winner's line - so you can follow a team across the page:

```
    1st Round            2nd Round           Conf Finals

 (D1) BUF      4✓──┐
 (WC1) BOS     2   ├─ (D1) BUF      3
                   │  (D3) MTL      4✓──┐
 (D2) TBL      3   │                    │
 (D3) MTL      4✓──┘                    ├─ (D1) CAR      4✓
                                        │  (D3) MTL      1
 (D1) CAR      4✓──┐                    │
 (WC2) OTT     0   ├─ (D1) CAR      4✓──┘
```

Seeds are in brackets, the series score or the game score is on the right, a check marks the winner, losers are dimmed, and once the final is decided the champion is named at the top with a ♛. Your favorites are starred. A team that skipped a round (a bye in the NFL, the AHL or MLB's top seeds) starts in the round it joined, level with the series it meets; an Olympic tournament's gold medal game has the bronze medal game under it. The caption names the season: last season's bracket stays up through the off-season, until the new season's first games.

Where each bracket comes from:

```
NFL               ESPN postseason weeks, seeds from the standings
college football  ESPN bowl-season games, the twelve-team CFP only
NBA               ESPN's playoff games by month, folded back into
                  series with ESPN's own series scores
college hoops     the NCAA tournament from the round of 64, region by
                  region in seed order (the First Four is left out so
                  the bracket lines up)
NHL               the NHL's own published bracket, with its seeds
AHL               HockeyTech's Calder Cup bracket, with series wins;
                  the first round is best of three, the division
                  rounds best of five, the last two best of seven
Olympics          the knockout games, from the qualification playoffs
                  to the gold medal game, on the Medal Round tab
MLB               MLB's postseason schedule, folded back into series
college baseball  the Men's College World Series as its two
                  four-team double-elimination brackets (7.0.0): the
                  opening games, the winners' game, the elimination
                  games and the bracket final, each game wired to the
                  next, the championship final beside them
WNBA              ESPN's playoff games (7.0.0): the top eight, best of
                  three, then five, then seven for the title
women's college   the NCAA tournament, region by region, as men's
Minor League      MLB's Stats API (7.0.0): a bracket a level, Triple-A
                  first - its two league championship series and the
                  one-game Triple-A final; below it each league's
                  division series and championship series - each
                  champion named with a ♛
college softball  the Women's College World Series stage by stage
                  (7.0.0): the opening round, the winners' games, the
                  elimination games, the semifinals and the finals.
                  Its brackets cross over after the winners' games, so
                  the games are not wired together.
```

Since 7.0.0 MLB's postseason is drawn as MLB draws its own where the screen is wide enough: the American League's rounds from the left edge in (wild card, division series, ALCS), the National League's from the right edge in, the World Series between the two pennant winners in the middle.

### Championship odds

Beside the bracket (below it on a terminal narrower than 150 columns) every team's chance of winning the title - the Super Bowl, the national championship, the NBA title, the Stanley Cup, the World Series - from the latest prices:

```
Kalshi market   the team's price on Kalshi's championship market,
                a live prediction market, as a probability (the
                middle of the bid and the ask)
DraftKings      the sportsbook's futures odds as ESPN carries them
                (+450 pays $450 on $100), with the bookmaker's
                margin taken out before blending
```

The chance column blends the two and scales the field to 100%. At the top, the whole field is drawn as one strip to scale - each contender's share in its own colours, the long shots together in grey - and every team below gets a meter against the favourite's (a row of blocks in the team's colour, one a segment), with the market's price (mkt) and the book's odds beside it. Teams that are out drop off. The NHL has no sportsbook board on ESPN yet this season, so its odds are Kalshi's alone. The WNBA's and women's college basketball's come from Kalshi (and, for the WNBA, a sportsbook's futures as ESPN carries them) like the others (7.0.0); Minor League Baseball (four levels, four champions) and college softball have no odds panel. The AHL and college baseball have no market or sportsbook at all, so sportst estimates theirs - the AHL from the standings (points percentage, pulled toward .500 early in the season), college baseball from the D1Baseball Top 25 - and says so above the chart. Prices refresh every 10 minutes (the book every 30); the panel shows when. The Olympics have no odds panel.

Once a new season has games, and until its postseason starts, the screen shows the playoff picture instead: who would be in if the season ended today, conference by conference by seed (division by division in the AHL, whose playoffs run that way), with the record (hockey adds the points) and the streak, and a dashed line across the cut. In the NBA a second line marks the play-in: seeds 7 to 10 play for the last two places. College football has no seeds in September, so it shows the AP Top 25 with the line drawn after the twelfth team.

### If the playoffs started today (NFL, MLB, NHL, AHL, NBA)

During the season the NHL's playoff picture is followed by the bracket the standings would make now, in the NHL's own format: in each conference the top three of each division and two wild cards, the better division winner meeting the second wild card (A1 is the Atlantic's first place, M the Metropolitan, C the Central, P the Pacific). Each team carries sportst's chance of winning the series - one game from the gap between the two teams' points %, pulled toward the middle early in the season, a little home ice for the higher seed, then best of seven - and in the later rounds each series' favourite goes through, so they show the likeliest path rather than a prediction of every result. The AHL gets each division's first round in the Calder Cup format (the Atlantic's top six, the North's and the Central's top five and the Pacific's top seven, best of three, the top seeds on a bye), the same chances, and the first team out with how far it trails. The NBA's starts with the play-in: in each conference seeds 1 to 6 go straight in, 7 meets 8 for the seventh seed, 9 meets 10, and the loser of 7-8 meets the winner of 9-10 for the eighth, each game with sportst's chance (from win %, the same way); then 1 v 8, 4 v 5, 3 v 6 and 2 v 7, best of seven. These are estimates, not a market.

The NFL's (since 6.19.0) uses the standings' own seeds: in each conference the four division winners 1 to 4 and three wild cards 5 to 7. The 1 seed sits out the wild-card round - 2 v 7, 3 v 6, 4 v 5 - and the field is then reseeded, the 1 seed meeting the lowest seed left; the higher seed is at home until the Super Bowl, which is on a neutral field. Each game's chance comes from the two records (log5 on win %, each pulled toward .500 by 11 games' worth, since a record is part luck) and 5 points of home field, and each favourite goes through.

MLB's (since 6.19.0, while the season is on - after it the real bracket is there) works the same way from its own seeds: in each league the three division winners 1 to 3 and three wild cards 4 to 6. The top two sit out the best-of-three wild-card series (3 v 6 and 4 v 5, every game at the higher seed's park); the winners meet them without reseeding (1 v the 4-5 winner, 2 v the 3-6 winner) over five games, then seven for the pennant and for the World Series, where the better record is at home. Each series' chance comes from one game's (log5 on win %, each record pulled toward .500 by 70 games' worth, and home field) played out over three, five or seven.

### College basketball's seed lines

Under the AP poll, **if the season ended today** lays the poll's top 24 out as the NCAA tournament's top six seed lines, four teams a line, each with its record today, and counts how many of the 25 each conference has as a meter. A picture of where the top teams stand, not a bracketology: the committee seeds by its own resume measures.

## 13. Betting lines and upset watch

Every game carries its line: the spread (the run line in baseball, the puck line in hockey), the over/under and both moneylines, with the opening number beside the current one and an arrow when it has moved.

In football the spread says who the favourite is. In hockey and baseball the spread is fixed at 1.5, so the moneyline decides it instead.

Upset watch: when a real favourite is losing, tied late, or barely ahead late, the game is tinted orange on the scoreboard and listed in the footer. Press U to jump to the next one. The line columns are always on (6.17.0 took away o, which hid them).

"Real favourite" means a spread of at least 3 points or a moneyline of -150 or shorter; both are adjustable. A three-run lead counts as safe in baseball, two goals in hockey, eight points in football.

ESPN drops the odds from its scoreboard the moment a game starts, so sportst keeps its own copy in ~/.cache/sportst/lines.json, recording every change it sees. If a game started before sportst ever saw the line, it asks ESPN's core endpoint, which still has it.

Run this from cron to keep tracking lines while the app is closed:

```
*/30 * * * * /home/you/.local/bin/sportst --scores -L nfl > /dev/null 2>&1
```

## 14. Colours and logos

### Team colours

Every team prints in its own primary colour, everywhere it appears. NFL, NHL, AHL, MLB and the college tables are built in, and Olympic nations have their national colours; anyone else falls back to the colour ESPN ships. College baseball uses the college football table, since they are the same schools.

Teams whose primary is black or near-black are drawn in their secondary instead, so they stay readable: Raiders, Bruins, Penguins, Kings, White Sox, Padres, Missouri, Iowa, UCF, Vanderbilt.

Two keys change this:

"team_color_overrides": { "mlb": { "SD": "#FFC425" } } "color_floor": 0.62

color_floor is how bright the strongest channel of a team colour must be, 0 to 1. Lower it to stay closer to the official values; raise it if your background is not very dark. "team_colors": false turns the whole thing off.

### Team badges

Two places show a team's mark: the bottom left of the Scoreboard's detail pane when a game is final (the winner's), and each side of the Game Center's score on a big screen. By default it is the team's badge, framed like a 1980s TV score bug: the team's letters in a bold pixel font on the team's colour, in whichever of white, its second colour or near-black reads best on it, with a rim and a bottom bar in its second colour (the rim turns light grey when that colour is too dark to see). It is six rows tall, needs nothing fetched, so it is there at once, and every team gets one - the AHL, college teams and Olympic nations too.

```
"team_logos": "badges"   the team's letters on its colours (the
                         default)
"team_logos": "drawn"    the logo itself, drawn in blocks (below);
                         it needs room to read
"team_logos": "off"      neither
```

The Settings tab has it under Display, Team logos. In a terminal that shows pictures the real logo takes the badge's place (below).

### Logos drawn in blocks

With "team_logos": "drawn", the winner's logo is drawn in colour at the bottom left of the detail pane, at most 8 rows by 24 columns, shrinking if the pane is short, and in the Game Center beside each score. It is ESPN's own artwork, fetched once per team and kept in ~/.cache/sportst/logos/. AHL logos come from the league's own site; in the Olympics it is the nation's flag.

It is drawn with Unicode sextant characters: each character cell holds a 2 x 3 grid of pixels, in two exact colours. If your font draws it badly, run

```
sportst --logo-test
```

which prints a team's badge and then its logo in every style, and set the sharpest one that draws cleanly:

```
"logo_art": "sextants"    2 x 3 per cell (Unicode 13, 2020);
                          "blocks", the default, means this too
"logo_art": "octants"     2 x 4 per cell (Unicode 16, 2024) -
                          sharper where the font draws all 256
"logo_art": "quadrants"   2 x 2 per cell, classic Block Elements
                          (Unicode 1.0, 1991) - lower resolution
                          but every monospace font draws it evenly
"logo_art": "halfblocks"  2 x 1 per cell, works anywhere
"logo_art": "ascii"       .:-=+*#%@ in the logo's colours
"logo_art": "off"         no logo and no badge
```

sportst picks between ESPN's normal and dark-background version of each logo by which one reads better on black, so Clemson's paw stays orange and Iowa's hawk is gold rather than black. Anything black inside a logo is lifted to charcoal so the shape does not vanish.

### College baseball logos

College baseball has two things the other sports do not. ESPN numbers its college baseball teams apart from its other college sports, so a team's baseball number cannot be put into ESPN's usual logo address - Arkansas is team 58 in baseball, and 58 in that address is South Florida's logo. sportst takes each baseball team's logo from ESPN's baseball data itself (or its list of baseball teams), so every school shows its own.

And many programs have a baseball mark of their own, the one on their caps. Those show it instead of the school's logo: Arkansas's A, LSU's interlocking LSU, Mississippi State's M-over-S, South Carolina's script SC, Clemson's C, Florida State's FS, Arizona State's AS, Kansas State's KS, Fresno State's FS and Ole Miss's baseball script - the marks their programs' Wikipedia articles use, fetched once from Wikimedia Commons and kept with the other logos. Every other team shows the school's own mark from ESPN, which is what most power-conference programs wear on their caps anyway (Tennessee's T, Michigan's block M, Oregon's O, North Carolina's interlocking NC ...). A baseball mark Wikimedia cannot send at that moment is tried again the next time; until then the school's logo stands in. A mark drawn on a white sheet (LSU's) has the white around it made see-through, so it sits on the dark screen like the others.

Logos kept by 6.0.0 for college baseball were the mixed-up ones; 6.1.0 keeps its college baseball logos under new file names, so they are all fetched again and the old files are simply never read (deleting ~/.cache/sportst/logos/cbase-*.png is safe).

### Real pictures in Kitty and Ghostty

Kitty and Ghostty can show real images inside the terminal, and sportst uses them when it finds itself in one:

- **The title.** The Overview's SPORTS TERMINAL is drawn as a picture at the terminal's own pixel size: the same block letters, leaning forward in a chrome blend of your colour scheme's colours with a bright glint, a light rim and a deep shadow, speed lines behind and racing stripes underneath. It takes the same rows as the text title, and it is redrawn when you change the scheme.
- **Big logos.** The real team logos in place of the badges (or the logos drawn in blocks): beside the Game Center's score, under a final on the Scoreboard and on a team's page.
- **The scoreboard's bulbs.** Every Game Center's scores and clock as a picture of an old stadium scoreboard's light bulbs - each lit bulb warm white with a shine and a glow, the unlit ones dark glass in their sockets - drawn by sportst at the terminal's own pixel size (since 6.18.0; ● bulbs in text elsewhere).
- **The football.** In a football game's Game Center (NFL, college), the ball beside the score of the team that has it is a picture of a real-looking football (redrawn in 6.20.0) - tipped a little as if on a tee, its four leather panels pebbled and lit from the upper left with a soft sheen, a small hot spot and a warm rim light, the seams pressed in tip to tip, the laces raised over the top seam (eight rounded stitches over the long lace, each going into its hole) and, on a college ball, a painted stripe round each end, with a soft shadow under it - drawn by sportst itself at the terminal's own pixel size, so it is sharp and nothing is downloaded for it (since 6.17.0; drawn in blocks in other terminals).
- **Small logos down every list.** A logo beside every team on the Scoreboard, in the standings, down a team's schedule (each opponent's) and beside your teams on the Overview - a whole column of them is one picture, so a long list costs the terminal no more than one logo. The highlighted row's logo sits on the highlight.
- **Kim.** Ask Kim's original 8-bit portrait, pixel for pixel, in place of the one drawn in text.
- **Players' photos.** On a Boxscore with players' cards (the NHL, the AHL, basketball and, since 6.17.0, football), the picked player's headshot on his card and the three stars' (the top performers') beside their lines; on hockey's Plays, the scorer's beside the picked goal. (In text, a player's card shows his photo drawn in blocks when Team logos is drawn, else his number on a badge in his team's colours.)

- **Pictures under the text (since 6.20.0).** Some charts get a picture laid under their text, the text still drawn over it: the Game Center's **drive chart** - the grass in ten-yard stripes with its yard and goal lines, the end zones striped in the teams' colours, each drive a bar outlined in a light shade of the offense's colours with a point where it ended and a strip of grass between it and the next, a small football and a yellow line to gain on the drive under way, and each drive's result on an outlined card of its own with its chip in the colours of whoever it was for - and every **win probability** (the Game Center's, and Game Stats' and Plays' in football, basketball and baseball): the meter a rounded bar in the two teams' colours split where their chances meet, the game's swing a smooth line over the share of whoever led, shaded in that team's colours from the dashed 50% line. Since 6.21.0 also the Plays tab's **game flow** (football and basketball) - a column chart, each column outlined in a light shade of its team's colours and set apart from the next, the zero line and the periods' starts dashed - and the Betting tab's **margin odds**, a smooth normal curve shaded in the two teams' colours either side of even, with a crisp line along its top, the even line dashed and the spread a gold dashed line. A pop-up over them takes them away until it closes.
- **Rounded shapes (since 6.20.0).** Kitty and Ghostty draw the Powerline half circles themselves, whatever the font, so there the picked tab, the chips (the ticker's league, LIVE ONLY and upset watch, STILL TO COME, the drive chart's results without pictures, the Game Center's own) and the keys on the bottom line (each on a keycap, the app's name on a chip of its own) have rounded ends; other terminals keep them square, as before.

Everything else on the screen stays text and works exactly the same. Setting Team logos to off (Settings, Display) takes the logos away; the title picture and the football stay.

How it knows: before the full-screen app starts, sportst asks the terminal its name and version, asks whether it can take a picture (a Kitty graphics query), and then asks one question every terminal answers, so the wait ends as soon as that answer comes back. Pictures are used when the terminal says it can take them and it is Kitty or Ghostty - the two known to show them the way sportst sends them, as Unicode placeholder cells that curses can draw like any other text. Every other terminal gets text art, and so does Kitty or Ghostty inside tmux or screen, which do not pass the question on. The System card on the Settings tab (About sportst) says what it found, for example "Pictures: real images (kitty answered) · kitty(0.32.2)".

```
"pictures": "auto"     ask the terminal when sportst starts (the
                       default)
"pictures": "images"   send pictures anyway - for another terminal
                       that shows Kitty-protocol images
"pictures": "text"     text art only
```

On the Settings tab (Display, Pictures), text art takes the pictures off the screen at once; turning them on takes effect at the next start, when sportst asks the terminal again. The terminal keeps the pictures while sportst runs, twelve at most, and forgets them when it quits. Logos for pictures are fetched once more, bigger (256 pixels from ESPN), and cached beside the others.

### Meters

Wherever a chart is drawn as a meter - the pace ladders, the differentials and the rest of Hot and cold, championship odds (and a team's title odds on its page), the four factors and how the points came, conference strength, the ranked teams by conference, every Game Center's win probability (since 6.16.0), the CRT effects card - it is a row of segments, one a cell, in the team's colour (green and red for good and bad). Only the lit segments are drawn: the rest of the scale is left empty, never shown unlit. Settings → Display → Meters (or the Meters row of the CRT effects card) picks one of six looks for all of them, and ← → there shows each at once:

```
LED segments    an old stereo's level meter: a tall lit segment, a
                dark gap, the next (the default)
LED dots        a row of small square lamps
bricks          blocks with a sliver of gap after and above each,
                so a chart's rows stack like bricks (6.5.1 to 6.7.0)
raised blocks   blocks with a little depth: a darker edge down the
                right side and along the foot, as though lit from
                the top left
solid bar       one bar, the lower three quarters of each cell
shaded blocks   a 1980s terminal's full blocks, the last three shading
                off  █████▓▒░
```

Every look leaves a gap above its row, so the rows of a chart stand apart. The segments are characters the sextant logos use (Unicode's Symbols for Legacy Computing, drawn by Kitty, Ghostty and VTE terminals themselves). With "logo_art" set to quadrants, halfblocks or ascii (step 6 of the install), each look is drawn in plainer block elements instead: LED segments as half blocks, LED dots as quadrants, bricks as three-quarter blocks, raised blocks with the shaded side only; those rows touch. In CRT mode the glass's bloom makes LED segments and dots glow like the real thing. The two-colour bars that split a game between its teams - win probability, possession - are shares, not meters, and stay solid. Shaded blocks are full blocks and shades, in every font, and keep their look with any "logo_art". In config.json: "meter_style": "led", "dots", "bricks", "raised", "solid" or "shade".

### Colour schemes

The app's own colours - titles, headings, borders, the cursor bar, the tab bar, the Overview title - come from one of four schemes, each in the spirit of a network's sports graphics from the 1970s to the 90s:

```
Retro ESPN         flagship red titles and cursor bar, ticker gold
                   headings and active tab, cream text, on black
Retro ABC Sports   bright yellow headings and cursor bar, white
                   titles, royal-blue borders, on deep blue
Retro CBS Sports   royal-blue titles and cursor bar, silver
                   headings and active tab, white text, on
                   blue-black
Retro NBC Sports   gold headings, orange titles, peacock-teal
                   borders and active tab, a purple cursor bar,
                   on ink (the default since 6.15.0, on the ink
                   background #0A0A10)
```

Pick one on the Settings tab (Display, Colour scheme): h / l step through them and the screen repaints as you go. In config.json it is "color_scheme": "espn", "abc", "cbs" or "nbc". Team colours are drawn on top of whichever you choose. The schemes are colour palettes only; sportst is not affiliated with any network.

### CRT mode

Settings → Display → CRT effect turns sportst into an old phosphor terminal - and since 6.15.0 a new install starts with it on: the colour phosphor (the scheme's own colours), every effect at the standard but a finer aperture grille, less bloom and softer focus (4), lighter grain (3) and a faint hum bar (2). A config.json from an earlier version keeps its own settings; Settings → Display → CRT effect turns it off. It comes in two layers, like the real thing: what sportst draws in the text itself, in any colour terminal, and the glass - see-through pictures laid over the text - in a terminal that shows pictures (Kitty, Ghostty).

```
Everywhere (any colour terminal)
  Phosphor colours   everything in one phosphor colour, brighter or
                     dimmer as it was: green (P1), amber (P3) or
                     white (P4); or colour, the scheme and team
                     colours as they are (CRT phosphor)
  Raised blacks      the background is a lit tube's faint glow, not
                     true black
  Power-on           a dot, a line across the middle, then the
                     picture opening out from it (any key skips it)
  Persistence        text that moves away leaves a trail that fades
                     in a fraction of a second; a moving cursor bar
                     too
  Burn-in            the tab bar and the borders on screen longest
                     (a minute and a half, all told) leave a faint
                     ghost wherever the screen is dark there
  Sync slips         now and then a row or two jumps a cell to the
                     right and back
  Typewriter         new text arrives a character at a time, as down
                     a slow serial line: a whole screen in under a
                     second, a changed number in a blink
  POST screen        a power-on self test before the first screen,
                     a line at a time: the processor and Python, the
                     memory, the display, the glass, the phosphor,
                     the font, the config, the cache, the leagues and
                     the network, then the league booting (any key
                     skips it)
  Blinking alerts    a score or upset alert on the bottom line blinks
                     until you press a key - and nothing else ever
                     blinks
  Update flash       a number that changes when fresh data arrives -
                     a score, a clock, a line - flashes bright for a
                     moment (never a number you changed with a key)
Kitty and Ghostty, on top
  Scanlines          a thin dark gap between every few rows of pixels
  Aperture grille    a fine red, green and blue stripe, close up
  Bloom              a wide glow round bright text, meters and bars
  Soft focus         a tight haze over every lit cell, the beam a
                     little out of focus: it softens the text itself
  Colour fringes     red off the left edge of each word, blue off its
                     right, as from misaligned colour beams
  Vignette           the edges and corners darker than the middle
  Grain              faint moving grain over the whole picture
  Flicker            a light, uneven flicker of the whole picture
  Hum bar            a faint brighter band drifting down the screen
  Curvature          the tube's face bulging out: the picture's edges
                     and corners fall away round a curved rim, and
                     the bezel's edges bow with it
  Glare              a soft oval of the room's light on the glass,
                     high on the left - on a curved face or a flat one
  Bezel              a dark frame round the picture, its opening's
                     corners rounded, the tube set back behind it
```

Two of those are as near as a terminal gets. Curvature bends the glass, not the text: the characters and the scanlines stay on their grid, and the rim and the bezel give the bulge. (Until 6.10.2 the scanlines bowed too, but lines that fine, bent across the screen's pixel grid, broke their rhythm into wavy creases - so they stay straight.) The bezel needs room of its own, so while it shows (a screen of 64 columns and 16 rows or more) sportst gives it the outer ring of cells - a row at the top and the bottom, two columns at the left and one at the right - and draws everything inside it.

#### The CRT effects card (Settings → Display → CRT effects)

Every effect but the phosphor's colour has a level from 0 to 10. 5 is the standard - the look described above - 0 turns that effect off and 10 makes it twice as strong. Since 6.8.1 the glass's standard is a gentler one: the aperture grille, bloom, soft focus, colour fringes and grain at two fifths of 6.8.0's and the hum bar at a fifth (6.8.0's 2 and 1 are today's 5, and a config.json from 6.8.0 is read onto the new scale, so the screen looks as it did). Since 6.10.0 the light on the glass has a row of its own, Glare, so the face can be curved without it or flat with it; a config.json from before 6.10.0 has Glare at its Curvature level, so the screen looks as it did there too. Turned up to 10, for example: a darker gap between the scanlines, a wider glow, a trail that lasts twice as long, burn-in in 45 seconds instead of 90, rows slipping twice as often, a slower power-on. On the Settings tab open Display and press enter on CRT effects, and a card opens over the screen with all of them, each with its level as a meter (up to ten segments, lit ones only, in the Meters look you chose), and at the top the CRT effect switch, the phosphor, a bitmap-style font and its size, and the meters' look:

```
╭─ CRT effects ───────────────────────────────────────╮
│   CRT effect       on   the glass on top            │
│   Phosphor         ◂ green (P1) ▸                   │
│   Font             ◂ IBM 3270 ▸   in use            │
│   Font size        ◂ 16 pt ▸   set by sportst       │
│   Meters           ◂ shaded blocks █▓▒░ ▸   ███▓▒░  │
│                                                     │
│  On every screen                                    │
│ ▌ Raised blacks    ▌▌▌▌▌       5  standard          │
│   Power-on         ▌▌▌▌▌▌▌     7                    │
│   ...                                               │
│  On the glass  Kitty, Ghostty                       │
│   Scanlines        ▌▌▌▌▌▌▌▌    8                    │
│   Hum bar                      0  off               │
│   ...                                               │
│ Raised blacks · a black of #06160C                  │
╰─────────────────────────────────── saved as you go ─╯
```

```
j k  up down       pick an effect
h l  left right    less / more (- and + too)
0 ... 9            that level at once (l goes on to 10)
enter or space     switch the effect off, and back to its level
T                  see it now: power-on again (Power-on), a row
                   slips (Sync slips), the screen typed out again
                   (Typewriter), the self test (POST screen), a test
                   alert (Blinking alerts), every number on the
                   screen flashing (Update flash), the hum bar from
                   the top (Hum bar); on Burn-in, wipe what has burnt
                   in
h l on Font        the bitmap-style fonts; enter switches Kitty to
                   the picked one (elsewhere it copies the line
                   that sets it in your terminal)
h l on Font size   half a point smaller / bigger in Kitty; enter
                   sets it at once, R back to Kitty's own
h l on Meters      the meters' look, everywhere in sportst
R                  this effect back to the standard, 5
A                  every effect back to the standard
U                  undo: every level as it was when the card opened
esc, c, Q          close
```

Every change shows on the screen at once, behind and on the card itself, and is saved to config.json as you go, so the levels are there the next time sportst starts. The line under the list says what the picked effect's level comes to (how long the power-on takes, how soon a border burns in, how often a row slips). A click on a meter's block sets that level; the mouse wheel moves through the list. The glass's effects can be set in any terminal and take effect wherever there is glass. In Settings' Display card, R on the CRT effects row puts every effect back to the standard, and Actions → "Reset settings to defaults" does too.

#### A bitmap-style font and its size (the card's Font and Font size rows)

The last touch is a font from the terminals of the day. Pick one on the Font row with h / l and sportst looks for it among the fonts installed (fontconfig's list) and says whether it is there - and "in use" when the terminal's config already sets it:

```
VT323              Google Fonts (fonts.google.com, VT323)
Glass TTY VT220    sudo apt install fonts-glasstty
                   (or github.com/svofski/glasstty)
IBM 3270           sudo apt install fonts-3270
                   (or github.com/rbanffy/3270font)
Px437 IBM VGA      the Ultimate Oldschool PC Font Pack
                   (int10h.org/oldschool-pc-fonts)
Terminus           sudo apt install fonts-terminus-otb; Kitty draws
                   no bitmap fonts, so there it needs the TrueType
                   copy, Terminus (TTF), files.ax86.net/terminus-ttf
the terminal's own sportst leaves the font alone (the standard)
```

On Linux Mint or Ubuntu, this installs all of them (the last line lists the six families it put in place):

```bash
sudo apt update && \
sudo apt install -y fonts-3270 fonts-glasstty fonts-terminus-otb curl unzip && \
mkdir -p ~/.local/share/fonts/sportst-crt && \
tmp=$(mktemp -d) && \
curl -fsSL -o ~/.local/share/fonts/sportst-crt/VT323-Regular.ttf \
  https://raw.githubusercontent.com/google/fonts/main/ofl/vt323/VT323-Regular.ttf && \
curl -fsSL -o "$tmp/oldschool.zip" \
  https://int10h.org/oldschool-pc-fonts/download/oldschool_pc_font_pack_v2.2_linux.zip && \
unzip -j -o -q "$tmp/oldschool.zip" 'ttf - Px (pixel outline)/Px437_IBM_VGA_8x16.ttf' \
  -d ~/.local/share/fonts/sportst-crt && \
curl -fsSL -o "$tmp/terminus-ttf.zip" https://files.ax86.net/terminus-ttf/files/latest.zip && \
unzip -j -o -q "$tmp/terminus-ttf.zip" '*.ttf' -d ~/.local/share/fonts/sportst-crt && \
rm -rf "$tmp" && \
fc-cache -f && \
fc-list : family | grep -E '^(VT323|Glass TTY VT220|IBM 3270|Px437 IBM VGA 8x16|Terminus|Terminus \(TTF\))$' | sort -u
```

**In Kitty, sportst switches the font itself (since 6.11.0).** Enter on the Font row puts the font at the end of kitty.conf, in a block of sportst's own, and has Kitty read the file again (the SIGUSR1 signal, as ctrl+shift+F5 does): the whole terminal changes font at once, and stays that way the next time Kitty starts. The Font size row does the same for the size - h / l make it half a point smaller or bigger and sportst tells Kitty a moment after the last step, enter sets it at once, R takes it back out; Settings → Display → Font size is the same control (enter there types a size). Bitmap-style fonts are drawn small at Kitty's usual 11 points: most look best a few points bigger. The block looks like this, and nothing else in the file is touched:

```
# sportst: the font and size from its CRT effects card - delete these lines to undo
font_family VT323
font_features VT323-Regular -liga
font_size 16
```

font_features turns the font's ligatures off - VT323 draws "fi" as one letter otherwise, leaving a gap in a terminal's grid. Before it first adds its block sportst keeps a copy of the file as kitty.conf.sportst-backup. "the terminal's own" plus enter on the Font row, and R on Font size, take sportst's lines back out (or delete the block yourself). Because it is the last thing in the file, sportst's block wins over font settings earlier in kitty.conf and in files it includes; a font Kitty is given on its command line (kitty -o font_family=..., or another --config file) wins over kitty.conf, and then nothing changes. sportst sets the font only in Kitty running on the same machine (it finds Kitty by its KITTY_PID): over ssh, and in other terminals, it does not touch the terminal's config and enter copies the line that sets the font to the clipboard instead (OSC 52), ready to paste:

```
Kitty     font_family IBM 3270          in ~/.config/kitty/kitty.conf
          (ctrl+shift+F5 reloads it)
Ghostty   font-family = "IBM 3270"      in ~/.config/ghostty/config
          (ctrl+shift+, reloads it)
```

Kitty puts its own colour palette back whenever it reads kitty.conf, so sportst gives it its colours again straight after. The POST screen's Font line says what the terminal's config sets.

The glass keeps the terminal redrawing about ten times a second, which a graphics card does not notice but a laptop's battery might: Grain, Flicker and the Hum bar at 0 on the card leave it nothing that moves on its own, and Settings → Display → Pictures → text art takes the glass away (and the real logos with it) and leaves the rest. Since 6.10.1 everything that moves on the glass - the hum bar, the flicker and the grain - steps together in one write, so the terminal redraws for them ten times a second rather than on three clocks of their own, and sportst works out the glow only for the rows of the screen that changed. Every time the terminal redraws, it lays all of the glass over the text again; with a graphics card that is quick, but in a terminal drawn without one (a virtual machine, say) it is the heavy part - there Flicker, Grain and the Hum bar at 0, or Pictures → text art, make the biggest difference. The typewriter and the update flash keep it drawing a little more often while they run, and the POST screen adds about two seconds to the start; all three are on the card. CRT mode needs colour, so --no-color turns it off. In config.json: "crt": true, "crt_phosphor": "green", "amber", "white" or "colour", "crt_font" and "crt_levels" (section 17).

### Everything else

Orange marks upset watch in every scheme. The app paints a solid background (each scheme brings its own), including the margins and the gaps between panes; changing the scheme moves the background with it unless you have chosen your own. "background": "terminal" gives your own terminal background back; any hex works too.

## 15. Favorites

Press 0 (in any league), or tab across to Favorites. The top of the screen lists what you have picked in all fourteen leagues (the WNBA, women's college basketball, Minor League Baseball and college softball since 7.0.0); below it is the team list for whichever league you are editing. Minor League teams are listed by their league (International, Pacific Coast, Eastern, Southern, Texas, Midwest, Northwest, South Atlantic, California, Carolina, Florida State), softball's and women's basketball's by conference.

```
j k              move through the list
enter or space   on a conference: open or shut it; on a team: star
                 or unstar it
l / h            open the conference under the cursor / shut the
                 one you are in
/                search the list - type chie, get the Chiefs
X                clear the search
L                switch which league you are picking for
```

Since 6.21.0 the list is grouped by conference (a pro league's conference, a college's own conference, the AHL's division): your teams first, always open, then each conference as a heading with how many teams it has and how many of them you starred (★ 2) - shut until you open it, so the list is a screen of headings rather than hundreds of teams. Teams in no conference (in college football, everyone outside the top division) sit under Other teams. A search opens every conference it finds teams in. The Olympics keep their one list of nations.

Starred teams float to the top of every list, in the order you added them: your games lead the scoreboard marked with a star, your team is starred in the box score and in the bracket, and the division holding a favorite is drawn first in the standings. Rows inside a division keep their real order, because that order is the standing.

In the Olympics the list is nations, not teams. A nation starred in the Winter Olympics is starred in every winter sport of every Games: its games lead the hockey scoreboard, its medals are marked in the event lists and results, and it heads the medal table under "Your nations".

Changes save to ~/.config/sportst/config.json immediately, and your teams appear on the Overview straight away.

## 16. Keys

### Moving around

```
j k   down up      next / previous game, or scroll a panel
J K                scroll the game detail on the right; a page of
                   Scouting, Boxscore and Game Stats
enter              scouting report for a game not yet played, the
                   box score for any other
Z                  the Game Center: the highlighted game full screen,
                   live (below) - from any tab, for the game picked
                   there (the Overview, a team's page, Betting ...)
PgDn PgUp          jump ten games, or scroll a panel by a page
Home End, G        first / last
```

Since 6.22.0 a screen of two panes side by side - Game Stats, the Boxscore, Plays, Scouting, Betting's detail, the Playoffs - scrolls each pane on its own. The keys above scroll the lit pane (its border in the accent colour, shown only when there is something to scroll); tab moves over to the right pane when it has more to show, and from there on to the next screen; shift-tab comes back; the mouse wheel scrolls the pane under the pointer and lights it. A cursor that moves into a pane - a player on the Boxscore, a play, a headline - lights it too.

### Screens

```
H                  Overview, where sportst opens
1 ... 9            the tabs after Overview, in tab-bar order:
                   1 Scoreboard, 2 Scouting, 3 Boxscore ... 9 Betting;
                   what they are depends on the league
0                  Favorites, in every league
O                  Settings
tab / shift-tab    next / previous screen, from any tab (on two panes
                   with more to show: the other pane first)
```

The bottom line always lists the keys for the screen you are on. Since 6.22.0, when they do not all fit on one line they take turns, a few seconds each, with the turn's number at the end (›2/3).

### Leagues and sports

```
P                  league picker: jump straight to any league
L                  cycle NFL, CFB, NBA, WNBA, CBB, WCBB, NHL, AHL, MLB,
                   MiLB, CBASE, CSOFT, the Olympics
E                  Olympic sport picker (Winter or Summer Olympics)
```

### In a picker

```
j k  down up       move (tab, shift-tab too)
PgDn PgUp          ten at a time
Home End, g G      the top / the bottom
enter, space       pick
1 ... 9, 0         jump straight to that league (league picker)
/                  filter; backspace edits the filter
esc                clear the filter, then close; the key that opened
                   the picker (P, E, c, s, B) closes it too
ctrl-u             at any prompt (D, /, a setting): clear the line
```

### Time

```
h l  left right    previous / next day, week in week mode, or Games in
                   the Olympics
[ ]                the same
T                  back to today, the current week, or the current Games
D                  jump to a date: 2026-09-13, 09/13, 13, yesterday,
                   tomorrow
C                  the calendar (below)
W                  week mode / day mode (football only)
```

### Baseball

```
, .                step back / forward through at-bats on Plays
```

### Boxscore tab: a player's card (NHL, AHL, NBA, CBB, NFL, CFB, MLB)

```
j k                pick a player: his card along the bottom
enter              make his card bigger; again, smaller (in
                   basketball the bigger card has room for his shots)
W                  open his page (ESPN, theahl.com) in the browser
esc                let go of him (the three stars, or basketball's,
                   football's and baseball's top performers, come back)
J K, PgDn PgUp     scroll the box score
click              pick a player; click him again for a bigger card
```

### Plays tab: clips

```
j k                pick a scoring play (in hockey, its goal card
                   fills the bottom of the screen; in football,
                   its drive, play by play on the field)
n N                next / previous play that has a clip
enter              play its clip (again, to stop)
esc                hockey and football: let go of the score
Y                  pick the whole game's highlights, at the foot of
                   the scoring summary (j k run on to them too)
enter on them      play them in a card (a second click too)
X                  stop the clip that is playing (on any tab but
                   Favorites, where X clears the search)
J K                scroll the screen
```

### The highlights card

```
space, enter       pause / play on; at the end, play them again
← →  h l           back / on ten seconds
R                  from the start
n N                the other video, where there are two
esc, q, X          close (a click outside the card; a click inside
                   pauses)
```

### Scouting tab: headlines

```
n N                pick the next / previous headline (▶ is a video)
enter              read the picked headline in the article card
                   (with none picked, enter picks the first)
esc                let go of the picked headline
click              pick a headline; click it again to open it
```

### The article card

```
j k  ↓ ↑           scroll a line
space  PgDn PgUp   a page down / up (J and K too)
G  End             the end of the story
g  Home            the top
o                  open the story on espn.com in your browser
enter              play the video (a video headline, or a story that
                   carries one); with no video, close the card
n N                the next / previous headline, without closing
X                  stop the video that is playing
esc  Q  backspace  close the card (a click does too)
```

### Basketball

```
V                  shot chart on Plays: both teams, away team only,
                   home team only
s                  Plays: the scoring plays as the whole left side,
                   or hidden again (6.22.0)
```

### Betting

```
U                  jump to the next game on upset watch
o                  Scoreboard: the games being played only (again: every
                   game)
```

### Filtering

```
/                  find a team: type part of a name ("new york"
                   finds the Giants and the Jets) and the Scoreboard,
                   Standings,
                   Stats and Betting tabs show only the teams that
                   match (Olympic events: by name or nation); an empty
                   search clears it
c                  conference / division list (Scoreboard,
                   Standings, Stats, Betting); in college football,
                   basketball and baseball the Top 25 is one of them
```

### Overview tab

```
j k                pick a favorite team, then on down into Today
left right, h l    its latest result / its next game (in Today: the
                   next column)
tab, shift-tab     the next / previous screen, as on every tab
enter, space       a result: that game's Game Stats; a next game:
                   its Scouting report (Game Stats once it is live);
                   in Today: a live game's Game Center, a game to
                   come's Scouting report, a final's Game Stats
Z                  the highlighted game in the Game Center
B                  the latest result's Game Stats, from either side
```

### Game Center (Z)

```
j k  h l           the day's next / previous game (the arrows and the
                   mouse wheel too); in the Event Center, the next /
                   previous event
enter              its box score (its scouting report before the start);
                   in the Event Center, every round's results
R                  refresh now
X                  stop a clip that is playing
? I                the key list, the Info pop-up (over the Game Center)
esc, Q or Z        close
```

### Standings tab

```
j k, enter         pick a team; enter opens its team page
h l                college: the previous / next conference in the
                   list (6.21.0)
J K                scroll the screen: the league's own panes (Hot
                   and cold, the pace, the poll ...) sit under the
                   tables (over them in college)
```

### A team's page

```
j k, J K           pick a game; jump ten games
enter              open it: its scouting report, or its box score
Z                  put it in the Game Center
T                  back to the next game
M                  the team's roster on a card (a click on M roster
                   at the top right too)
V                  (narrow terminal) the games / the season at a
                   glance; j k scroll it
esc, backspace     back to the standings (or to the Stats table)
```

### A team's roster (M on its page)

```
j k                pick a player: his card on the right
g G, Home End      the first / last player
tab, shift-tab     the next / previous group (offense, defense ...;
                   centers, left wings ...)
J K, PgDn PgUp     scroll his card when a small terminal cannot
                   hold it all (space too)
W                  his page (ESPN's, or the AHL's) in your browser
esc, M             close (Q and backspace too)
```

### The calendar (C)

```
h l  left right    a day back / forward
j k  down up       a week
[ ]  < >  , .      the previous / next month (PgUp PgDn too)
n N                the next / previous game day
F                  your teams' next game
T                  today
enter, space       go to that day
esc, C, Q          close
```

### Mouse

```
click              a tab: open it; a game, team, Settings title or
                   setting: pick it; a menu item or calendar day:
                   choose it; a row of the Television Schedule: pick
                   its game; outside a menu, a card or the calendar:
                   close it
click again        open what is picked, as enter would (a double
                   click too)
click (roster)     M roster on a team's page: open the roster; a
                   player in its list: his card
click (wire)       an item on the BottomLine or the live wire: open
                   its game
wheel              move through the list, or scroll the pane under
                   the pointer
shift-drag         select text while the mouse is on
```

### Stats tab

```
j k, enter         pick a team; enter shows its players
[ ]  (table)       one conference / division at a time: previous /
                   next (back round to All teams)
c                  pick the conference / division from the list
esc, [ ]           back to the table; previous / next team
                   (in a team's player view; backspace and enter
                   go back too)
g (a team)         its season totals, its last game, its team page
g (table)          next stat group, then all of them
s                  choose the sort column (best first), or the
                   order: by league and division (pros), by
                   conference, best first, or team name A-Z
S                  sort by the next column (in the s list too)
```

### Betting tab

```
j k / J K          pick a game / scroll its detail
$                  Ask Kim: the week's three best bets (section 9)
B                  lines from: top-3 average, best price, one book
s                  best bets first (ranked) or start-time order
M                  value picks only
enter              the game's scouting report
```

In Ask Kim: enter skips to the end of his picks and then closes, j k scroll the bubble, R asks again, esc, Q or $ close.

### Favorites tab

```
j k                move through the conferences and teams
enter or space     a conference: open or shut it; a team: star it
l / h              open the conference under the cursor / shut the
                   one you are in (6.21.0)
/  X               search the list / clear the search
L                  the league you are picking for
```

### Settings tab

```
j k                pick a title: a group of settings or a part of
                   About sportst
h l  left right    over to About sportst / back to the settings
enter or space     open the title's card
```

In a group's card:

```
j k                pick a setting
enter or space     change it: switch it, list the choices, or type
                   a value (an action: do it; CRT effects: its card)
h l  left right    step a value down / up, or the previous / next
                   choice
R                  back to its default (capital R only)
tab, shift-tab     the next / previous group
esc                close the card
```

In an About sportst card: j k scroll a line, J K (PgDn PgUp, space) a page, g G the top and the end, tab and shift-tab the next and previous part, esc closes.

On the CRT effects card: j k pick an effect, h l less / more, 0-9 a level at once, enter switches it off and back, T shows it now, R the standard, A every effect standard, U undo, esc closes; on the Font row h l pick a font and enter switches Kitty to it (elsewhere it copies the line that sets it), on the Font size row h l make Kitty's font smaller / bigger, enter sets it at once and R puts Kitty's own back, on the Meters row h l pick the look (section 14).

### Everything else

```
R                  refresh now
A                  auto-refresh on or off (off: nothing is fetched
                   until you press R or open something new)
+ -                refresh interval up or down five seconds (= works
                   as +); live games refresh twice as often
ctrl-l             repaint, if something garbles the screen
any key            skips CRT mode's power-on sweep (section 14)
I                  Info: what every column, symbol, colour and number
                   on the screen in front of you means
?                  key list (in the Game Center too)
Q                  quit; in a pop-up or the Game Center, close it
```

Capitals and small letters: a key listed as a capital works in either case (U or u, R or r, Z or z, Q or q ...), so Caps Lock does no harm. The keys listed as small letters - c g h j k l n o s - keep their case because their capital is another key: C, G, H, J, K, L, N, O and S each do something of their own. In a Settings card R puts a setting back to its default; on the tab itself R refreshes, as everywhere.

## 17. Config

```
sportst --write-config        # writes ~/.config/sportst/config.json
```

Almost everything below can be changed on the Settings tab (O) instead, which saves the file for you; a group's card shows each setting's config name.

A config file only needs the keys you want to change; any key it does not have uses the default below.

```
league                 nfl          which league opens first: nfl, cfb,
                                    nba, wnba, cbb, wcbb, nhl, ahl,
                                    mlb, milb, cbase, csoft, owg, osg
refresh_seconds        30           poll interval; live games poll
                                    twice as often (every 10 to 60
                                    seconds)
auto_refresh           true         poll in the background, or only on R
rounded_borders        true         curved or square box corners
cfb_group              80           ESPN conference group: 80 FBS,
                                    81 FCS, 8 SEC, 4 Big 12
favorites                           per-league lists (one per league,
                                    milb, wnba, wcbb and csoft too),
                                    managed on the Favorites tab
color_scheme           nbc          espn, abc, cbs or nbc (section 14)
team_colors            true         false turns team colouring off
color_floor            0.62         legibility floor for dark colours
team_color_overrides   {}           pin any team to any hex, per league
background             #0A0A10      app background (ink); terminal to show
                                    your own through
court_lines            braille      braille or dots, for the shot chart's
                                    court lines
team_logos             badges       badges, drawn (the logo, in
                                    blocks) or off (section 14)
logo_art               blocks       how a drawn logo is built:
                                    blocks (or sextants), octants,
                                    quadrants, halfblocks, ascii; off
                                    hides every logo and badge. The
                                    meters follow it (section 14)
meter_style            led          how every meter is drawn: led
                                    (LED segments), dots, bricks,
                                    raised or solid (section 14)
pictures               auto         the real logos and Kim's portrait
                                    in a terminal that shows pictures:
                                    auto (Kitty, Ghostty), images or
                                    text (section 14)
crt                    true         CRT mode: an old phosphor screen
                                    (section 14); false turns it off
crt_phosphor           colour       green, amber, white or colour
crt_levels             see right    each CRT effect from 0 (off) to 10
                                    (grille, bloom and focus 4, grain
                                    3, hum 2, the rest 5):
                                    blacks, power, trails, burn,
                                    slips, type, post, blink, flash,
                                    scanlines, grille, bloom, focus,
                                    fringes, vignette, grain,
                                    flicker, hum, curve, glare,
                                    bezel - e.g. {"hum": 0,
                                    "type": 0}; anything left out of
                                    a config.json is 5 (section 14),
                                    and a
                                    config from before 6.10.0
                                    takes Glare from Curvature.
                                    sportst adds "scale": 2, 6.8.1's
                                    standard
crt_font               own          the bitmap-style font picked on
                                    the CRT effects card: vt323,
                                    glasstty, ibm3270, px437,
                                    terminus or own; enter there
                                    sets it in Kitty's kitty.conf
                                    (section 14; the font size
                                    lives there too, not here)
olympic_events         {}           the sport each Olympics opens on,
                                    saved when you pick one with E
mlb_statcast           true         use MLB's own feed for spin, exit
                                    velocity and the per-batter zone
extra_stat_sources     true         fill the Stats and Scouting tabs
                                    from the NHL, MLB, AHL and NCAA
                                    stats services as well as ESPN;
                                    false uses ESPN alone (no college
                                    baseball stats then)
scouting_news          4            headlines per team on Scouting;
                                    0 hides the news
betting_book           avg          avg (top-3 average), best, or one
                                    book: FanDuel, DraftKings, BetMGM,
                                    Caesars, bet365, BetRivers, Bovada;
                                    set from the app with B
betting_top_books      FanDuel,     the three books averaged
                       DraftKings,
                       BetMGM
betting_min_edge       3.0          edge (%) a bet needs to be a value
                                    pick (one star of five); two at
                                    2x, three at 3.5x, then up to two
                                    more as the signals agree
betting_sources        true         false: no Action Network or Kalshi,
                                    only ESPN's own line
betting_lines          true         false turns off lines and upset
                                    watch entirely
odds_provider          ""           prefer a sportsbook by name
upset_alerts           true         the orange highlight and the footer
upset_color            #FF6F00      the upset-watch orange
upset_min_spread       3.0          smallest spread that counts as a
                                    real favourite
upset_min_moneyline    -150         moneyline at or below which a team
                                    counts as a real favourite
upset_close_spread     7.0          how big a favourite must be for the
                                    CLOSE alert
upset_bell             false        ring the bell on a new alert
line_history_days      21           how long saved lines are kept
timeout_seconds        15           per-request HTTP timeout
api_host               site.api.espn.com   which ESPN host to try first
clip_player            auto         auto, mpv, ffplay, vlc or browser:
                                    what plays a scoring play's clip
clip_video             false        true: the player opens a video
                                    window as well as the sound
highlight_player       auto         how the game's highlights play:
                                    auto, mpv or ffmpeg (in their
                                    card), window or browser
youtube_clips          true         false: no YouTube for NFL and AHL
                                    clips, and no YouTube searches
ticker                 auto         the BottomLine: auto (terminals 30
                                    rows or taller), on or off
live_wire              true         the crawl over the BottomLine
                                    while games are on, every league:
                                    goals, runs, touchdowns, runs
                                    scored, upsets, finals; false
                                    hides it
score_alerts           true         your teams' starts, scores and
                                    finals on the bottom line
score_bell             false        ring the terminal bell with each
                                    score alert
score_flash            true         flash a banner in the team's
                                    colours over the BottomLine for
                                    three seconds when one of your
                                    teams scores (basketball: a three)
mouse                  true         clicks and the wheel; false leaves
                                    the mouse to the terminal
```

## 18. Command line

Every view also prints as plain text, in full colour when the output is a terminal and plain when it is a pipe.

```
sportst --today                       every league's games today: live,
                                      coming up, final; your teams first
sportst --scores                      today's slate with lines and IDs
sportst --scores -L mlb
sportst --scores -L cfb -w 4
sportst --scores -L nhl -d 2026-10-14
sportst --box 401817104 -L mlb        box score
sportst --team-stats 401817104 -L mlb one game's stats and leaders
sportst --plays 401817104 -L mlb      the pitch view as text
sportst --plays 401872924 -L nfl      scoring plays and drives
sportst --standings -L mlb            uses your full terminal width
sportst --stats -L nfl                every team's season stats
sportst --stats -L cfb --conference SEC   one conference
sportst --stats -L nhl --conference "Metropolitan Division"
sportst --stats -L cbase --json       the merged table as JSON
sportst --bets -L nfl                 lines, projections, value picks
sportst --bets -L cfb -w 9 --book best   next week, best prices
sportst --bets -L nba --book FanDuel  one sportsbook
sportst --kim -L nfl                  Ask Kim: the week's three best bets
sportst --kim -L nba --book best      ... at the best price anywhere
sportst --playoffs -L nhl             the bracket (the playoff picture
                                      while the season is on)
sportst --odds 401872933              line, movement, result
sportst --favorites                   your saved teams
sportst --logo-test -L mlb            a badge, the meter looks and the logo styles
                                      your font draws
sportst --scores -L ahl               today's AHL games
sportst --box 1028697 -L ahl          an AHL box score (HockeyTech id)
sportst --standings -L ahl
sportst --playoffs -L ahl             the Calder Cup bracket
sportst -L owg --list-events          every sport and its -E name
sportst --scores -L owg -E hockey-m   the Olympic men's hockey games
sportst --standings -L owg -E hockey-w   the women's groups
sportst --playoffs -L osg -E basketball-m   the medal round
sportst --scores -L osg -E swimming   every swimming event and podium
sportst --medals -L owg               the Games medal table
sportst --scores -L nba -d 2026-06-10
sportst --plays 401859966 -L nba      scoring plays and the shot chart
sportst --standings -L cbb            every conference
sportst --playoffs -L cbb             March Madness
sportst --scores -L wnba -d 2026-07-15   a WNBA night (7.0.0)
sportst --scores -L wcbb              women's college basketball today
sportst --scores -L milb -d 2026-09-12   every minor-league game that day
sportst --playoffs -L milb            each level's bracket and champions
sportst --standings -L milb           every league and division
sportst --playoffs -L csoft           the Women's College World Series
sportst --medals -L osg --games 2024
sportst -L owg -E figure-skating      open the app on that sport
sportst -E alpine-skiing              the same: -E alone finds its Games
sportst --scores --json | jq '.events[].id'
```

An -E name or a --games year that is not on file stops with a list of the ones that are (--list-events gives the sports by name).

--json prints ESPN's raw payload instead of the rendered view, for --scores, --box, --team-stats, --plays, --standings and --odds; with --stats it prints sportst's merged table of every source.

## 19. Troubleshooting

**The logo is a scatter of empty boxes, or looks glitchy or uneven.**

Run sportst --logo-test and set logo_art to the sharpest style that draws cleanly. "quadrants" uses only classic Block Elements from 1991, which every monospace font renders evenly.

**Kitty or Ghostty shows text art instead of pictures.**

The Pictures line on the Settings tab's System card (About sportst) says why. Inside tmux or screen the terminal never hears sportst's question, so it keeps to text art; run sportst outside them to get pictures. If Pictures is set to text art, set it back to auto.

**Empty boxes, stray marks or a blank square where a logo or Kim should be.**

The terminal was sent pictures it cannot show, usually because Pictures is set to real images in a terminal without Kitty-style images. Set Pictures to auto or text art on the Settings tab, or "pictures": "text" in the config file.

**A college baseball team shows the wrong school's logo (6.0.0) or its school logo instead of its baseball mark.**

6.0.0 could show another school's logo for a college baseball team (Arkansas got South Florida's); 6.1.0 fetches every college baseball logo again under new file names, so updating is the whole fix. The ten programs with a baseball mark of their own (section 14) get it from Wikimedia Commons; if Wikimedia did not answer that time, the school's logo stands in until the next start, when the mark is fetched again. If it never arrives, check that upload.wikimedia.org is reachable from your computer.

**The game's highlights open in the browser instead of their card, or the card says it could not play them.**

The card needs mpv or ffmpeg (sudo apt install mpv ffmpeg), and the NFL's YouTube video needs yt-dlp too; the Highlights line on the Settings tab's System card says which way they play here. "no sound: ffmpeg could not reach the sound server" means ffmpeg found no PulseAudio, PipeWire or ALSA to play through; mpv (in Kitty) uses its own. In tmux or screen there are no pictures, so the card draws in half blocks. ESPN posts a game's highlights soon after the final, and not for every game: until then the section offers a YouTube search.

**The font did not change after picking one on the CRT effects card.**

Picking one with h / l only chooses it: press enter. In Kitty that switches the terminal at once - unless Kitty was started with a font of its own (kitty -o font_family=..., or a --config file other than ~/.config/kitty/kitty.conf), which wins over kitty.conf; the card says "Not installed here" when the font is missing. Kitty draws no bitmap fonts: for Terminus there, install the TrueType copy, Terminus (TTF). Elsewhere enter copies the line: paste it into the terminal's config and reload it (Ghostty: ctrl+shift+,).

**The article card says "Could not load the story".**

ESPN's content API did not answer, or the story has been taken down. The summary from the feed is still shown, o opens the story on espn.com, and sportst asks again a minute later.

**No pitch data on a baseball game.**

ESPN publishes pitch locations only for games it covers pitch by pitch. Spring training, some college games and older games have none; the screen says so rather than drawing an empty zone.

**Speeds are missing in college baseball.**

Nobody publishes pitch speeds for college baseball. Locations, counts, results, runners and steals are all there.

**The bracket is empty.**

Either the postseason has not started, in which case the playoff picture is shown instead, or that league's bracket is not published yet. College baseball's bracket only covers the College World Series and the championship series.

**The footer says DNS lookup failed.**

Your computer briefly could not look up an ESPN hostname. Each request retries once quietly, and the warning clears as soon as one succeeds. If it persists, check: resolvectl query site.api.espn.com

**Team colours look approximate.**

Your terminal does not allow palette redefinition, so colours map onto the 256-colour cube. Check that echo $TERM reports something ending in -256color. Nothing breaks either way.

**Colours look washed out or too bright.**

Lower color_floor toward 0.45.

**CRT mode: the scanlines or the glow sit a little off the text, or the terminal feels sluggish.**

The glass (section 14) is drawn to the terminal's cell size, which sportst reads when the screen changes size; ctrl-l sends it again. It keeps the terminal redrawing about ten times a second, which a slow or software-only graphics setup feels - on the CRT effects card (Settings → Display → CRT effects) Grain, Flicker and the Hum bar at 0 stop everything that moves on its own, Settings → Display → Pictures → text art takes the glass away and keeps the rest of CRT mode, and CRT effect off takes all of it away. One effect too much or too little - the scanlines too dark, the glow too wide, the slips too often - is a level on that card. Outside Kitty and Ghostty there is no glass at all: the phosphor colours, the power-on sweep, the trails, the burn-in and the slips are the whole effect there.

**My terminal's colours look odd after a crash.**

```
printf '\033]104\007' resets the palette.  A normal quit handles it.
```

**Boxes drawn with qqqq.**

The terminal is not in UTF-8; check echo $LANG, or set "rounded_borders": false.

**Nothing loads and the footer shows an HTTP error.**

ESPN rate-limits occasionally. Press R. If one host is blocked on your network, set api_host to site.web.api.espn.com.

**College football is missing games.**

The default group is FBS only. Change cfb_group.

**An Olympic sport says "HTTP 429 from en.wikipedia.org".**

Wikipedia asks clients to slow down now and then. sportst makes one request a second at most and retries on its own; the page appears on the next refresh. Finished Games are kept on disk for a week in ~/.cache/sportst/wiki/, so each page is fetched once.

**An Olympic event shows no results table.**

Wikipedia fills the results in as the event happens; before then the page has the schedule and the entry list only. The medallists in the event list come from the sport's own page and usually appear first.

**College baseball's Stats tab says it is loading for a long time.**

The first load reads NCAA.com page by page through ncaa-api.henrygd.me, which allows a few requests a second; it takes up to a minute, once every 12 hours. The other leagues load in a second or two.

**A Stats or Scouting number shows "-".**

That source has no figure for that team yet - early in a season, for a team that has not played, or for a stat a league does not keep.

**The stats look like last season's.**

Before a new season's first games most sources still serve last season's totals; they switch over on their own.

**The Betting tab shows only one line, or "-" in every column.**

Action Network has not posted lines for those games yet (they usually appear a few days ahead), or api.actionnetwork.com is unreachable from your network. sportst falls back to ESPN's single line, and the projection still runs.

**A game shows no Kalshi row.**

Kalshi lists a market only for some games, and sportst ignores one whose bid and ask are too far apart to give a real price.

**The c list says it is still loading.**

The conference list comes from the standings, fetched in the background when a scoreboard opens. Try again a second later.

**The AHL shows "Could not reach HockeyTech".**

lscluster.hockeytech.com is the AHL's stats server. If it is down, so is the league's own website; try again in a minute.

### Which source is failing?

The Settings tab (O) has every data source on its Data sources card with this run's requests to it - how many worked, how many failed, the last error and when - and the recent problems on a card of their own. If one ESPN host is blocked on your network, switch "ESPN host tried first" (Settings → General).

## 20. Where the data comes from

### ESPN's public site API

Scoreboards, box scores, team stats, standings, team lists, rankings, betting lines and play-by-play for the NFL, CFB, NBA, WNBA, CBB, WCBB, NHL, MLB, CBASE and CSOFT - including every shot's location for basketball - and the Olympic hockey, basketball, football and baseball tournaments (those on site.web.api.espn.com). Each league's news wire, every item tagged with its teams and players, is what Ask Kim reads for late injury news. No key, no account.

### ESPN's team statistics, rosters and news (site.web.api.espn.com)

Every team's season numbers for the NFL, CFB, NBA, CBB and NHL - their own and their opponents', which is where the defence columns come from - every player's season numbers for the Stats tab's player screen, plus each team's roster with its injuries (for the Scouting tab and the roster card on a team's page - the whole squad since 6.18.0, where ESPN's first answer stops at a hundred players - and the positions in football's Game Center LEADERS) and the team news feed for the Scouting tab.

### ESPN's core API

Betting lines after a game has started, which the scoreboard drops, a sportsbook's championship futures (the Playoffs tab's odds), and the date windows of college baseball's championship rounds.

### MLB Stats API (statsapi.mlb.com)

Statcast for MLB only: pitch speed and spin, exit velocity, launch angle, distance and the strike zone measured for each batter. The game is matched to ESPN's by date and the two team names. No key, no account. Turn it off with "mlb_statcast": false.

### MLB Stats API, team totals (statsapi.mlb.com)

Every MLB team's hitting, pitching and fielding numbers for the Stats and Scouting tabs. No key.

### MLB Stats API, the minor leagues (statsapi.mlb.com, img.mlbstatic.com)

Everything for Minor League Baseball (7.0.0), from the same public API MiLB.com uses: each day's games at all four levels, every game's live feed (pitch by pitch, the box score and its notes, the officials, the weather), standings by league and division, each team's schedule and active roster, every team's and player's season numbers, and each level's postseason. Team logos come from img.mlbstatic.com. No key, no account.

### The NHL's own APIs (api-web.nhle.com, api.nhle.com/stats)

The playoff bracket, with the seeds and series scores the scoreboard does not carry, and team shots, faceoff %, power play and penalty kill for the Stats and Scouting tabs. Each game's three stars, head coaches, scratches and officials come from its game center (the game found by its date and teams), and the stars' headshots from assets.nhle.com. The day's scoreboard (/v1/score) gives the Television Schedule Canada's channels and the live wire each game's goals, clock, power play and empty net; each live game's game center gives the wire its fights and majors. No key.

### ESPN's player pages (site.web.api.espn.com)

An NHL, NBA, college basketball, NFL, college football or MLB player's card on the Boxscore: his profile, his season with his league ranks, and his game log, from the same public player pages espn.com uses; his headshot from ESPN's image CDN (a.espncdn.com). The roster card on a team's page (M) reads the same pages for every player in the NFL, college football, the NBA, college basketball, the NHL and MLB - the athlete, his overview, his bio and his stats: who he is, the latest note on him (RotoWire's, which ESPN carries), his numbers this season, lately, season by season and over his career, his last five games, his awards and the teams he has played for. His night and his shots come from the game's own play by play. No key.

### NCAA.com via ncaa-api.henrygd.me

College baseball's team stats for all of Division I and the D1Baseball.com Top 25, and since 7.0.0 college softball's team stats (batting average, ERA, fielding percentage, runs a game). ncaa-api is a free, open-source service that reads NCAA.com's public stats pages and returns them as JSON. No key, no account; it asks clients to stay under five requests a second, which sportst does.

### HockeyTech (lscluster.hockeytech.com)

Everything for the AHL: scores, the live clock, box scores, goals and penalties, the play by play with every shot's spot on the rink (for the shot maps, the game flow and the goal cards), standings, teams, special-teams stats, player stats, each team's roster, each player's profile, season, game log and photo for his card (on the Boxscore and on the roster), game previews for the Scouting tab and the Calder Cup bracket. It is the league's own stats service, open, with the public key theahl.com uses (see section 21). Logos come from assets.leaguestat.com.

### Action Network (api.actionnetwork.com)

Every game's spread, total and moneyline at FanDuel, DraftKings, BetMGM, Caesars, bet365, BetRivers and Bovada, plus the consensus, the opening line and the public's share of bets and money, for the NFL, CFB, NBA, WNBA, CBB, women's college basketball, NHL and MLB. The consensus stays on a game after it ends, and is the closing line the Betting tab grades the day's finals against. It is the public JSON the Action Network website itself loads; no key and no account, but it is not an official, documented API, so it could change without notice - if it does, the Betting tab falls back to ESPN's line. Turn it off with "betting_sources": false.

### Kalshi (api.elections.kalshi.com) - game and championship markets

Prediction-market prices for game winners and for each league's champion, from Kalshi's public market-data API - since 7.0.0 the WNBA's and women's college basketball's too. No key or account needed to read prices.

### Wikipedia (en.wikipedia.org)

The Olympic sports ESPN does not cover: each sport's page for its events and medallists, each event's page for its results, and each Games' medal table. Pages are read as rendered HTML with the standard library's html.parser, one request a second at most, and kept in ~/.cache/sportst/wiki/. The IOC's own live results feed is licensed to broadcasters only.

### ESPN's content API (content.core.api.espn.com)

The whole story behind a Scouting headline, for the article card: every item in an ESPN news feed links to it, and it sends the story itself as HTML - the headline, byline, date and text - or, for a video, the clip's description, length and video file. sportst lays the HTML out with the standard library's html.parser and keeps each story for an hour while the app runs. No key, no account. The video itself is played by your media player straight from ESPN's video servers, as clips are.

### ESPN's image CDN

Team logos and national flags - 128 pixels for drawing in text, 256 for a terminal that shows pictures - cached in ~/.cache/sportst/logos/.

### Wikimedia Commons (upload.wikimedia.org)

The baseball marks of the college baseball programs that wear one of their own - Arkansas's A, LSU, Mississippi State's M-over-S and the others in section 14 - the image files their Wikipedia articles use, fetched once as 250-pixel PNGs and cached with the other logos. No key, no account.

### ESPN's team schedules (site.api.espn.com)

Each favorite team's latest result and next game for the Overview, the last game a team played for the Stats tab's player screen, and each team's whole season for its team page (from the standings or the Stats tab). AHL teams use HockeyTech's schedule. The Overview's Today list, the BottomLine and the score alerts read each league's ordinary scoreboard for today.

### The game's highlights

The same lists carry the whole game's highlights: ESPN's game summary marks its "Final Game Highlight" video, MLB's content list its recap and condensed game, and the NFL's YouTube feed its game-highlights video. As with the clips, sportst reads only the lists: mpv or ffmpeg fetch the video itself, straight from ESPN's or MLB's video servers (yt-dlp finds YouTube's), while the card is open, and nothing is saved. A frame sportst draws as a picture goes to the terminal through a temporary file in your temporary folder, which the terminal reads and deletes at once (over ssh, through the terminal line instead).

### Scoring-play clips

ESPN's game summaries list its one-play clips with a direct video address; MLB's Stats API lists every game's highlight clips the same way (statsapi.mlb.com/api/v1/game/.../content); the NHL's API gives every goal its own clip, which opens in the NHL's video player (players.brightcove.net) in your browser; and YouTube's public channel feeds (www.youtube.com/feeds/videos.xml, no key) list the NFL's and the AHL's latest uploads. sportst reads only those lists. The clip itself is fetched by your media player straight from ESPN's or MLB's video servers, or shown by your browser, when you press enter - sportst never downloads or saves a clip.

The Settings tab's Data sources card lists every one of these with its host and how this run's requests to it have gone.

Nothing else is contacted, and nothing is sent anywhere. The only files written are your config, the saved betting lines, the logo cache, the Wikipedia cache and the college baseball and softball stats caches (and, while a highlight plays, its frames on their way to the terminal and mpv's control socket, both in the temporary folder and gone with the card). Setting "extra_stat_sources": false keeps the Stats and Scouting tabs to ESPN.

## 21. Privacy and API keys

sportst needs no account, no sign-in and no API key of your own. Nothing in it identifies you, and it sends nothing about you anywhere: it only asks the services below for sports data, and everything it saves stays in the two folders listed under "Files it creates" in section 2.

The clip sources added in 4.8 need no key either. When a clip opens in your browser, the NHL's video player (players.brightcove.net) or YouTube sees an ordinary visit from your browser, exactly as if you had clicked a link.

The extra stats services added in 4.2 (the NHL's and MLB's stats APIs and ncaa-api for NCAA.com) and the betting sources added in 4.3 (Action Network and Kalshi) need no key either. sportst only reads prices; it cannot place bets and never touches a sportsbook account.

ESPN's content API, which the article card reads stories from, and Wikimedia Commons, where the college baseball marks come from (both new in 6.1.0), need no key either.

The program does contain one key: HockeyTech's AHL feed key (50c2cd9b5e18e390). It is not a secret and not tied to anyone. It is the public key the AHL's own website, theahl.com, sends from every visitor's browser to load its scores. The file is safe to share as is. The Settings tab's Data sources card shows it beside HockeyTech.

## 22. Notes if you want to extend it

Adding an ESPN league is one entry in LEAGUES plus, optionally, a colour table in TEAM_COLOR_TABLES. Teams with no entry fall through to ESPN's own colour, so a new league is coloured before you type a single hex code.

Colour flows through a single style token. Renderers emit (text, style) spans, where a style is either a name like "header" or a literal "#0076B6", with ~b bold, ~s on the cursor bar, ~d for a team that lost and ~u on the upset tint. Logo art uses "@RRGGBB" or "@RRGGBB:RRGGBB" for an exact pair with no legibility lifting. The curses palette and the ANSI printer each resolve those tokens their own way, which is why the same renderer drives both the full-screen app and the command line.

Betting lines come through parse_line_item, which reads both of ESPN's shapes - the scoreboard's moneyline / pointSpread / total blocks with open and close strings, and the core endpoint's numeric moneyLine with open / current blocks - so a new league's odds work without new parsing. ESPN's spread is home-relative everywhere: negative means the home team lays the points.

Logos decode with a small PNG reader built on zlib (png_decode), so they need no imaging library.

Curses can only use about 250 colour pairs, so logo art gets its own block of 48, recycled for each new logo. Browsing any number of games never takes pairs away from team colours. Badges (render_badge) are drawn the same way, from a 5 x 7 pixel font (BADGE_FONT, with BADGE_BOLD for the letters that do not survive a doubled stroke), two pixels to a cell.

Real pictures use the Kitty graphics protocol's Unicode placeholders. A picture is sent once into one of twelve numbered slots (200 to 211), and the screen shows it wherever cells hold U+10EEEE with that number as their 256-colour foreground and combining marks for the cell's row and column (past the 64th column the mark is left off and the terminal counts on from the cell to the left, so a picture can be up to 400 cells wide). To curses those cells are just text, so pop-ups, scrolling and redraws need nothing special; image_cells() returns them as ordinary Lines, and Graphics.flush() sends any new pictures after curses has drawn the frame. A slot is keyed by what is in the picture, so a changed picture needs a new key, and the least recently shown slot is reused when all twelve are taken. A list's small logos are one picture per column (logo_strip), each logo shrunk with scale_rgba; cells on a highlighted row ask for the highlight's background (the ":s" on their style). The title is drawn by title_picture() a row of spans at a time, so it takes a few hundredths of a second in pure Python.

A team's page is built from season_numbers() (the season so far from the schedule's games), standings_index() (every team's standings row by id) and opponent_numbers() (the schedule against the standings), then one function per panel - team_card, chart_panel, next_up_panel, division_panel, splits_panel, numbers_panel, report_panel, road_panel, odds_panel - each returning Lines for a given width, laid out by team_page_lines(). A new panel is one more function and one more entry in that list.

Baseball pitch locations arrive in ESPN's pixel grid, seen from behind the plate. x = 117 - 38.118 * pX and y = 238.78 - 27 * pZ convert MLB's own feet-from-the-plate coordinates into it; px_to_feet goes the other way. That is how ESPN's locations and MLB's measured strike zones end up on the same picture.

Brackets are one small model - rounds of series, each with two sides, a seed, a score and a winner - with a builder per league feeding it. Adding a league's bracket means writing one builder that returns that shape. bracket_rows() lays any of them out as a tree from the final back, matching each series to the ones whose winners it holds, so the order a builder lists its series in does not matter; a series nothing fed takes the next free slot, and a game between losers (a bronze medal game) goes under the final.

A league from somewhere other than ESPN is an adapter that speaks ESPN. Every API method returns (source, [fallbacks]), and a source is either a URL or a Loader - a function that makes whatever requests it needs and returns ESPN-shaped JSON. The AHL adapter turns HockeyTech's games, summaries and standings into ESPN's scoreboard, summary and standings payloads, which is why every NHL screen works for the AHL unchanged. Loaders go through the same cache and background threads as plain URLs.

Minor League Baseball (7.0.0) is the second adapter: MLB's Stats API made to speak ESPN (milb_scoreboard, milb_summary with its pitch-by-pitch plays, milb_standings and the rest), its play text put into ESPN's past tense (MILB_TENSE) so that everything which reads a play's words reads it unchanged. A league that works like another borrows it: MODEL_LEAGUE names the league each new one follows (the WNBA the NBA, women's college basketball men's, the minors MLB, softball college baseball), like() answers "which rules?" where the code asks, and _borrow_tables() fills every per-league table the new league has no entry of its own in.

Where Python has no curses (Windows), _vt_curses_module() stands in for it: the part of curses sportst uses, written out as VT escape codes, with the keyboard and mouse read from the console's input records (Windows) or the terminal's escape codes (anywhere else; SPORTST_CURSES=vt tries it). A date drawn without its leading zero goes through strf(), since Windows spells %-d as %#d.

Olympic sports are generated from OLYMPIC_GAMES: each Games lists its sports, and each sport becomes a LEAGUES entry like owg2026.hockey-m. A new Games is one entry there. ESPN tournaments carry their ESPN path; everything else is read from Wikipedia by title ("Luge at the 2030 Winter Olympics"), with WIKI_SPORT_PAGES for the sports that share a page.


## 23. License and disclaimers

### License

sportst is free and open source under the MIT License:

```
MIT License

Copyright (c) 2026 BravoDeltaThr33

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```

The license covers sportst's own code and text. It does not cover the data, logos, clips or pages sportst shows, which belong to the people who publish them.

### Not affiliated with anyone

sportst is an independent hobby project, made for fun and given away free. It is not affiliated with, endorsed by or sponsored by ESPN, ABC, CBS, NBC, Disney, the NFL, the NCAA, the NBA, the NHL, the AHL, Major League Baseball, the International Olympic Committee, any team, conference or network, or any of the data sources in section 20 (Action Network, Kalshi, HockeyTech, NCAA.com, YouTube, Wikipedia and the rest). Team, league, network and company names, logos and colours are trademarks of their owners and are used only to say which team, league or source something is. The ESPN, ABC, CBS and NBC colour schemes are tributes to the look of classic sports broadcasts, not those networks' own designs.

### The data is theirs

sportst does not host, copy or resell anyone's data. It ships with no scores, stats, odds, logos or clips: each copy asks the public sources itself, from your own computer, as you use it, and keeps only a small cache on that computer (section 2). Each source's own terms of use apply to that use; please respect them, and do not use sportst to republish their data or for anything commercial. Clips play or open from their own sites (ESPN, MLB, the NHL, YouTube) exactly as they are published there; sportst never downloads or redistributes them.

### No guarantees

Scores, stats, schedules, lines and odds come from third parties and can be late, incomplete or wrong. Do not rely on sportst for anything that matters.

### Betting

The value picks, projections and Ask Kim are statistical estimates for entertainment. They are not betting, financial or professional advice, and nobody involved with sportst is responsible for any bet you place or any money you lose. sportst cannot place bets and has no relationship with any sportsbook or market: no affiliate links, no sponsorships, nothing paid. Bet only where sports betting is legal for you and you are of legal age, and only what you can afford to lose. If gambling stops being fun, call or text 1-800-GAMBLER.

### Ask Kim

Kim is a parody character, played for laughs. He does not represent, and is not endorsed by, any real person, government or organisation, and his picks are sportst's model wearing a costume.

### Something of yours?

If you own something sportst shows or names and would like it changed or removed, open an issue on the GitHub repository and it will be looked at promptly.
