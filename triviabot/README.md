# Trivia Bot

A Keybase chat bot that provides access to the [OpenTDB](https://opentdb.com) trivia database so it can be enjoyed in Keybase chat.

## Running

In order to run the Trivia bot, there needs to be a running MySQL database in order to store the leaderboard and API tokens to OpenTDB.

1. On that SQL instance, create a database for the bot, and run `db.sql` to set up the tables.
2. Build the bot using Go 1.13+, like such (in this directory):
   ```
   go install .
   ```
3. To start the Trivia bot, run a command like this:
   ```
   $GOPATH/bin/triviabot --dsn 'root@/triviabot'
   ```
4. Run `triviabot --help` for more options.

### Helpful Tips

- If you accidentally run the bot under your own username and wish to clear the `!` commands, run the following:
  ```
  keybase chat clear-commands
  ```
- Restricted bots are restricted from knowing channel names. If you would like
  a bot to announce or report errors to a specific channel you can use a
  `ConversationID` which can be found by running:
  ```
  keybase chat conv-info teamname --channel channel
  ```
- By default, bots are unable to read their own messages. For development, it may be useful to disable this safeguard.
  You can do this using `--read-self` flag when running the bot.

### Docker

There are a few complications running a Keybase chat bot, and it is likely easiest to deploy using Docker. See https://hub.docker.com/r/keybaseio/client for our preferred client image to get started.
