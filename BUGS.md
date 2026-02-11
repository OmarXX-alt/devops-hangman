# Bug Tracker

## Known Bugs

### Word Bank Bugs
### 1. Word Bank Edit Bug
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: Editing a word from the word bank deletes it instead of updating it
- **Steps to Reproduce**:
  1. Open word bank
  2. Attempt to edit an existing word
  3. Word gets deleted instead of being updated
- **Expected Behavior**: Word should be updated with new value
- **Actual Behavior**: Word is removed from the word bank
- **Priority**: High
- **Assigned To**: 
- **Notes**: 





### Player Setup Bugs

#### 1. Player Name Can Start Empty
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: Players can start the game without entering names. Empty input fields default to "Player 1" and "Player 2" instead of requiring valid input.
- **Steps to Reproduce**:
  1. Leave player name fields empty
  2. Click "Start Game"
  3. Game starts with default names
- **Expected Behavior**: Game should not start if player names are empty. Error message should be displayed (per REQ-PS-01)
- **Actual Behavior**: Game starts with default names "Player 1" and "Player 2"
- **Priority**: High
- **Requirements Violated**: REQ-PS-01 (Player names MUST NOT be empty)
- **Assigned To**: 
- **Notes**: Code at line 139-140 in script.js uses fallback values instead of validating

#### 2. Players Can Start with Similar Names
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: Two players can have the same or identical names, making it impossible to distinguish between them during gameplay.
- **Steps to Reproduce**:
  1. Enter "John" for Player 1
  2. Enter "John" for Player 2
  3. Click "Start Game"
  4. Game starts with both players having the same name
- **Expected Behavior**: Game should validate that Player 1 and Player 2 have different names. Error message should be displayed (per REQ-PS-01)
- **Actual Behavior**: Game allows identical player names
- **Priority**: High
- **Requirements Violated**: REQ-PS-01 (Player 1 and Player 2 MUST have different names)
- **Assigned To**: 
- **Notes**: No validation check exists in startGame() function

#### 3. Missing Start Game Button Validation
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: The "Start Game" button does not validate player names before starting the game
- **Expected Behavior**: The "Start Game" button MUST validate player names (per REQ-PS-02)
- **Actual Behavior**: No validation occurs; game starts regardless of input
- **Priority**: High
- **Requirements Violated**: REQ-PS-02 (The "Start Game" button MUST validate player names)
- **Assigned To**: 
- **Notes**: Validation logic needs to be added to startGame() function at line 135

---

### Game Flow Bugs

#### 1. Player Turn Does Not Change After Win
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: When a player wins a round, the turn does not switch to the other player. The same player continues playing in the next round.
- **Steps to Reproduce**:
  1. Start a game with two players
  2. Complete a round where Player 1 wins
  3. Click "Next Round"
  4. Observe that Player 1 plays again instead of Player 2
- **Expected Behavior**: Players MUST switch turns after a win (per REQ-WL-01). The next player MUST be the one who didn't play the previous round (per REQ-WL-04)
- **Actual Behavior**: The same player continues playing after winning
- **Priority**: High
- **Requirements Violated**: REQ-WL-01 (Players MUST switch turns after a win), REQ-WL-04 (The next player MUST be the one who didn't play the previous round)
- **Assigned To**: 
- **Notes**: gameWon() function does not switch currentPlayer; only gameLost() function at line 319 switches turns

#### 2. Lives Not Resetting Between Rounds
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: Lives counter calculation is incorrect and does not properly reset to 6 at the start of each round
- **Steps to Reproduce**:
  1. Start a new round
  2. Check the lives display
  3. Make wrong guesses
  4. Start next round
  5. Observe lives counter behavior
- **Expected Behavior**: Lives MUST reset to 6 at the start of each round (per REQ-GF-01). Lives MUST start at 6 (per REQ-GM-04)
- **Actual Behavior**: Lives calculation in updateLives() function (line 222) is incorrect: `livesLeft = maxWrong - wrongGuesses + 1` results in 7 lives initially instead of 6
- **Priority**: High
- **Requirements Violated**: REQ-GF-01 (Lives MUST reset to 6), REQ-GM-04 (Lives MUST start at 6)
- **Assigned To**: 
- **Notes**: Formula should be `livesLeft = maxWrong - wrongGuesses` (6 - 0 = 6, not 6 - 0 + 1 = 7)

---

### Gameplay Mechanics Bugs

#### 1. No Visual Indication for Already-Used Letters
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: When a player clicks a letter that has already been guessed, there is no visual feedback or indication to inform them that the letter was already used
- **Steps to Reproduce**:
  1. Start a game
  2. Click a letter (e.g., "A")
  3. Try clicking the same letter again
  4. Button does nothing but provides no visual indication it was already used
- **Expected Behavior**: Each letter MUST only be clickable once per round (per REQ-GM-01). Clicking a letter MUST disable that button (per REQ-GM-01)
- **Actual Behavior**: Button is not disabled after clicking, providing no visual feedback that it has already been used
- **Priority**: Medium
- **Requirements Violated**: REQ-GM-01 (Clicking a letter MUST disable that button)
- **Assigned To**: 
- **Notes**: guessLetter() function checks if letter was used (line 176) but doesn't disable the button; need to add button.disabled = true after clicking

#### 2. Incorrect Hangman Parts Display Order
- **Status**: Open
- **Date Found**: February 11, 2026
- **Description**: Hangman parts appear in the wrong order. Currently displays: head → left arm → right arm → body → left leg → right leg
- **Steps to Reproduce**:
  1. Start a game
  2. Make wrong guesses
  3. Observe the order of hangman parts appearing
- **Expected Behavior**: Parts MUST appear in this order: head, body, left arm, right arm, left leg, right leg (per REQ-GM-05)
- **Actual Behavior**: Parts appear in order: head, left arm, right arm, body, left leg, right leg
- **Priority**: High
- **Requirements Violated**: REQ-GM-05 (Parts MUST appear in this order: head, body, left arm, right arm, left leg, right leg)
- **Assigned To**: 
- **Notes**: updateHangman() function at line 229 uses wrongOrder array with incorrect sequence; should use the parts array instead which has the correct order

---
