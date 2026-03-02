# 🎮 Game Glitch Investigator: The Impossible Guesser

## 🚨 The Situation

You asked an AI to build a simple "Number Guessing Game" using Streamlit.
It wrote the code, ran away, and now the game is unplayable. 

- You can't win.
- The hints lie to you.
- The secret number seems to have commitment issues.

## 🛠️ Setup

1. Install dependencies: `pip install -r requirements.txt`
2. Run the broken app: `python -m streamlit run app.py`

## 🕵️‍♂️ Your Mission

1. **Play the game.** Open the "Developer Debug Info" tab in the app to see the secret number. Try to win.
2. **Find the State Bug.** Why does the secret number change every time you click "Submit"? Ask ChatGPT: *"How do I keep a variable from resetting in Streamlit when I click a button?"*
3. **Fix the Logic.** The hints ("Higher/Lower") are wrong. Fix them.
4. **Refactor & Test.** - Move the logic into `logic_utils.py`.
   - Run `pytest` in your terminal.
   - Keep fixing until all tests pass!

## 📝 Document Your Experience

- [✅] Describe the game's purpose:
   The game purpose is a guessing number game. You're given a selection of 'Difficultly' and each level is provided with range of numbers and number of attempts. The user has to input a number until it matches with the secret number. The user is provided with hints and able to restart the game.
  
- [✅] Detail which bugs you found:
   1. "New game" button would not restart the game status and history or score won't clear. The game would be on lock till all the attempts are ran out.
   2. The "check_game" function had an inverted condition. Also, the typeError handler had a error in their condition.
   3. The "update_score" function has inconsistent scoring outcomes.
   4. st.sidebar had incorrect range display and wrong logic behind secret regenerating when 'Difficultly' selection changes.
      
- [✅] Explain what fixes you applied:
  1. The fixes I applied for "new game" button is changing the state attempts and adding state status/state history
  2. For "check_game" function, I change the condition body where it returns the accurate response for if-condition. I also convert secret into a string (similar to guess), fixing the error on string comparison
  3. I fixed the condition body where it could decrease points based on the number of attempts and could be awarded if given "too high" or "too low"
  4. I change the mismatch between the displayed range and actual range. I also change the if condition body for secret in session state  

## 📸 Demo

<img width="1324" height="690" alt="Screenshot 2026-03-01 at 7 47 54 PM" src="https://github.com/user-attachments/assets/bb14fe13-ae9a-49ec-9734-f007948cceb5" />


