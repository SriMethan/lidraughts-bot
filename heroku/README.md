## How to setup bot on heroku:
- Place your engine(s) in the `engine.dir` directory
- Copy `config.yml.default` to `config.yml`
- Create an account for your bot on [Lidraughts.org](https://lidraughts.org/signup)
- NOTE: If you have previously played games on an existing account, you will not be able to use it as a bot account
- Once your account has been created and you are logged in, [create a personal OAuth2 token](https://lidraughts.org/account/oauth/token/create?scopes[]=bot:play&description=lidraughts-bot) with the "Play as a bot" selected and add a description
- A `token` e.g. `Xb0ddNrLabc0lGK2` will be displayed. Store this in `config.yml` as the `token` field. You can also set the token in the heroku config vars `$LIDRAUGHTS_BOT_TOKEN`.
- NOTE: You won't see this token again on Lidraughts.
- Move all the files from `./heroku` to `.` (replace the files in `.` with the files from `./heroku` in case of a conflict)
- In `config.yml`, enter the binary name as the `engine.name` field (the engine should be for Linux)
- In `startbot.sh`, delete `chmod +x ./engines/engine_name` if you are using a homemade engine else replace `engine_name` with the binary name at line `chmod +x ./engines/engine_name`
- Edit the variants: `supported_variants` and time controls: `supported_tc` from the config.yml as necessary
- Create a [new heroku app](https://dashboard.heroku.com/new-app).
- Follow the steps on Deploy using Heroku Git
- Once it has been deployed, go to Resources tab on heroku and enable worker (bash startbot.sh) dynos. (If you don't see any dynos in the Resources tab, then you must wait for about 5 minutes and then refresh your heroku page.)
