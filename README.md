# 🍀 Codding Problems Solutions 🍀
## Solutions for problems from LeetCode and CodeWars
All my solutions could be found at: https://anton-veselskyi.gitbook.io/codding-problems-solutions/

## Set up
1. `git clone https://github.com/uriyyo/coding-challenges`
2. Modify map in `archgenerator/archgenerator/docs/consts.py` to contain languages that you are using(if they are missing)
3. `pip install ./archgenerator`
4. `archgenerator codewars —email ${EMAIL} —password ${PASSWORD}` - to generate codwars.json
5. `archgenerator leetcode --session-id ${SESSION_ID}` - to generate codwars.json (SESSION_ID could be found in  Chrome Dev Tools(F12 or Ctrl+Shift+I) -> Application -> Cookies, it should be long value)
6. `rm -rf ./docs/*` - clean all docs from uriyyo repo
7. `archgenerator docs` - to fill docs folder with your solutions im .md format (all info are taken from codwars.json and leetcode.json)
8. Commit and push your repo
9. Create space at GitBook and link your existing repo via *Integration* tab

## Tool 
**archgenerator** is developed by [@uriyyo](https://github.com/uriyyo) in https://github.com/uriyyo/coding-challenges



