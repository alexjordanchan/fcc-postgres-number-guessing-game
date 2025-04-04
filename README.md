# freeCodeCamp: Build a Number Guessing Game

## Instructions
To complete this project, you need to write a script that generates a random number between 1 and 1000 for users to guess. Create a `number_guess`database to hold the information suggested in the user stories. 

- Connect to the interactive psql shell with `psql --username=freecodecamp --dbname=postgres` to create the database. In your script, you can create a `PSQL` variable for querying the database like this: `PSQL="psql --username=freecodecamp --dbname=<database_name> -t --no-align -c"`.
- Your script should only ask for input from the user to get the username and to take guesses. Your script should output exactly what is described in the user storied below, and nothing extra.
- The tests will add users to your database when the script has that ability, feel free to delete those. Some script related user stories may not pass until the script is completely working. Don't forget to commit your work frequently.

## Part 1: Create the Database
```
# Connect to the interactive psql shell
psql --username=freecodecamp --dbname=postgres
```
```
# Create Database 'number_guess'
CREATE DATABASE number_guess

# Connect to Databse
\c number_guess

# Create table 'user'
CREATE TABLE users();

# Create table 'user' - Add Columns
ALTER TABLE users ADD COLUMN user_id SERIAL PRIMARY KEY;
ALTER TABLE users ADD COLUMN username VARCHAR(22) NOT NULL UNIQUE; 

# Create table 'games'
CREATE TABLE games();

# Create table 'games' - Add Columns
ALTER TABLE games ADD COLUMN game_id SERIAL PRIMARY KEY;
ALTER TABLE games ADD COLUMN user_id INT NOT NULL;
ALTER TABLE games ADD COLUMN guesses INT NOT NULL DEFAULT(0);
ALTER TABLE games ADD FOREIGN KEY(user_id) REFERENCES users(user_id);
```

## Part 2: Write the BASH script
- Create a `number_guessing_game` folder in the `project` folder for your program
```
# Split terminal, then create a folder
mkdir number_guessing_game
```
- Create `number_guess.sh` in your `number_guessing_game` folder and give it executable permissions
```
# Create a file under folder 'number_guessing_game'
touch number_guess.sh

# Give it executable permissions
chmod +x number_guess.sh
```

- Turn the `number_guessing_game` folder into a git repository
- The message for the first commit should be `Initial commit`
```
# Turn it into a git repo
git init

# Make git repo comit (1st) - to main branch
git add .
git commit -m "Initial commit"
```

- Your script should have a shebang at the top of the file that uses `#!/bin/bash`
- Your script should randomly generate a number that users have to guess
- When you run your script, you should prompt the user for a username with `Enter your username:`, and take a username as input. Your database should allow usernames that are 22 characters
- If that username has been used before, it should print `Welcome back, <username>! You have played <games_played> games, and your best game took <best_game> guesses.`, with `<username>` being a users name from the database, `<games_played>` being the total number of games that user has played, and `<best_game>` being the fewest number of guesses it took that user to win the game
- If the username has not been used before, you should print `Welcome, <username>! It looks like this is your first time here.`
- The next line printed should be `Guess the secret number between 1 and 1000:` and input from the user should be read

- Until they guess the secret number, it should print `It's lower than that, guess again:` if the previous input was higher than the secret number, and `It's higher than that, guess again:` if the previous input was lower than the secret number. Asking for input each time until they input the secret number.
- If anything other than an integer is input as a guess, it should print `That is not an integer, guess again:`
- When the secret number is guessed, your script should print `You guessed it in <number_of_guesses> tries. The secret number was <secret_number>. Nice job!` and finish running

## Part 3: Commit to GitHub Repository
- Your git repository should have at least five commits
- The rest of the commit messages should start with `fix:`, `feat:`, `refactor:`, `chore:`, or `test:`
```
# Make git repo comit (2nd) - to main branch
git add .
git commit -m "feat: ASK_USERNAME"

# Make git repo comit (3rd) - to main branch
git add .
git commit -m "feat: lopp structure"

# Make git repo comit (4th) - to main branch
git add .
git commit -m "refactor: GUESSING_MACHINE"

# Make git repo comit (5th) - to main branch
git add .
git commit -m "fix: plural spelling"
```

- You should finish your project while on the `main` branch, your working tree should be clean, and you should not have any uncommitted changes
