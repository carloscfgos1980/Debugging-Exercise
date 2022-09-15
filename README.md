Degugging

\*The path cannot contain (&)

1.1 - I switched loseResult : winResult; so when it wins it will show the correct game over. It was not the good solution but it works.

1.2 The Real solution:
There was a bug when (GameOver) was called.
wordGuessed function was mispelled that is why it returns false even when the result was true.(App.js: line 31)

---

2. - AppContainer.js error in line 50.
     Error spelling the const newGuessedLetters

---

3. - Error in App.js
     3.1 - Change let for const(line 16)
     3.2 - place !before !guessedLetters.includes(letter)

---

4. - Error (bug) AppContainer. EventListener (guessLetterHandler) (line 44 -58)
     4.1 Create a const for the length of the inputField value not equal no null (0). Ex:
     const inputGiven = this.state.currentChosenLetter.length > 0;(line 45)
     4.2 - Create a const for new letters so dissable the change of picking the same letter again. EX:
     const newLetter = !this.state.guessedLetters.includes(
     this.state.currentChosenLetter
     (line 46 - 48)
     4.3 - Create a condiction to use above constante. Ex:
     if (inputGiven && newLetter) {
     const newGuessedLetters = [...this.state.guessedLetters];
     newGuessedLetters.push(this.state.currentChosenLetter);
     this.setState({
     guessedLetters: newGuessedLetters
     });
     }
     (line 49-55)

4.4 - Create a default value in case that no value has been entered. Ex
this.setState({ currentChosenLetter: "" });(line 56)

---

5. Error (Bug) in AppCpntainer.js
   5.1 - Change (>) for (>=) so it wont
   continue guessing until -1 guesses. Ex(line 30:
   getWrongLetters(game.chosenWord, game.guessedLetters).length >= game.maxGuesses

---

6.Error (Bug) in AppCpntainer.js
6.1 - Add a const for the new letters. Ex (line 46-48):
const newLetter = !this.state.guessedLetters.includes(
this.state.currentChosenLetter
);
6.2 - Include the condiction (newLetter). Ex(line 49):
if (inputGiven && newLetter) {
