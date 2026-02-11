# Bug Tracker

## Known Bugs

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


## 2. Empty Word Validation Bug
- **Status**: Open  
- **Date Found**: February 11, 2026  
- **Description**: The system allows empty words to be added to the word bank.  
- **Steps to Reproduce**:
  1. Open word bank  
  2. Leave the input field empty  
  3. Click add/save  
- **Expected Behavior**: The system should reject empty input and display a validation message.  
- **Actual Behavior**: An empty word is added to the word bank.  
- **Priority**: High  
- **Assigned To**:  
- **Notes**: May cause gameplay errors  


## 3. Duplicate Word Allowed Bug
- **Status**: Open  
- **Date Found**: February 11, 2026  
- **Description**: The system allows duplicate words to be added to the word bank.  
- **Steps to Reproduce**:
  1. Add a word (e.g., HELLO)  
  2. Add the same word again  
- **Expected Behavior**: The system should prevent duplicate entries and display an error message.  
- **Actual Behavior**: The same word is added multiple times to the word bank.  
- **Priority**: Medium  
- **Assigned To**:  
- **Notes**: Causes redundant entries and reduces data integrity.  


## 4. Numbers and Special Characters Validation Bug
- **Status**: Open  
- **Date Found**: February 11, 2026  
- **Description**: The system allows words containing numbers and special characters, violating the requirement that words must contain only uppercase letters (A–Z).  
- **Steps to Reproduce**:
  1. Open word bank  
  2. Enter a word such as HELLO123  
  3. Enter a word such as TEST!  
  4. Click add/save  
- **Expected Behavior**: The system should reject words containing numbers or special characters.  
- **Actual Behavior**: Words containing invalid characters are accepted.  
- **Priority**: High  
- **Assigned To**:  
- **Notes**: Violates input validation rule defined in REQUIREMENTS.md.

## 5. Word Bank Delete Function Not Working
- **Status**: Open  
- **Date Found**: February 11, 2026  
- **Description**: The system does not allow users to delete words from the word bank, violating the requirement that users must be able to remove words.  
- **Steps to Reproduce**:
  1. Open word bank  
  2. Attempt to delete an existing word  
  3. Observe system response  
- **Expected Behavior**: The selected word should be removed from the word bank.  
- **Actual Behavior**: The word remains in the word bank and is not deleted.  
- **Priority**: High  
- **Assigned To**:  
- **Notes**: Violates word bank management requirement and affects user control over stored words.  


---
