# SciOly-ID-Discord-Bots
A template for creating Discord Bots to study for Science Olympiad ID events.

# Usage
To setup your own bot, follow these steps:

1. Create a GitHub repository using this template. Click the green `"Use this template"` button above or click [here](https://github.com/tctree333/SciOly-ID-Discord-Bots/generate). Name your new repository something interesting that describes it's purpose.

The following steps contain code editing. While you can edit and create files directly online, it's much easier to use a proper text editor. I recommend using [VSCode](https://code.visualstudio.com/), since there's plenty of extensions that can make your life easier, though there are plenty of other alternatives. You would also have to learn Git to interact with your repository, but there are plenty of tutorials online.

However, for this particular purpose, editing files online will be sufficient.

2. Open up the `bot` folder and open `config.py`. This is where you will setup your bot's settings. For examples of configs, see the [examples section](#examples).
   * `BOT_DESCRIPTION` - This is a description of the Discord bot.
   * `BOT_SIGNATURE` - This is what is displayed at the top of an embed. This is also a short description of the bot.
   * `PREFIXES` - This is what is used to call your bot. The first item of the list will be used when giving example commands. Having different cased versions of your prefix may be helpful to mobile users, along with having a prefix with only letters and periods.
   * `ID_TYPE` - This is a singular noun that describes what you are IDing.
   * `NAME` - It doesn't really matter what this is, basically an id for your bot.
   * `GITHUB_IMAGE_REPO_URL` - This is a link to the GitHub repo hosting your images, which we will create later. Be sure to update this as soon as possible.
   * `INVITE` - This is a Discord link that lets people invite your bot to a server. We will get this later.
   * `SUPPORT_SERVER` - This is the link to the Discord server that will act as a support server.
   * `AUTHORS` - Put your name/username here. Credit people for their part in the bot's creation.
   * `SOURCE_LINK` - This is the link to the GitHub repo hosing your code, the one you're editing right now.
   * `ID_GROUPS` - Set this to `True` if you want to categorize the items. Possible categories include taxons for birds/fossils, muscle groups for anatomy, or categories of space objects for astronomy.
   * `CATEGORY_NAME` - This is what you are splitting your categories by.
   * `CATEGORY_ALIASES` - This is a dict of different aliases your categories may go by for ease of use. You do not need to put all your categories here, only if it has an alias.

3. Now we need to add the lists. Go to `bot/data/lists/` and create a new file called whatever you're IDing. For example, a fossils bot would have a list called `fossils.txt`. If you have categories, create a file for each category. Fill in these files with the lists, one per line.
4. If some items in the list can go by a different name, you can input them in `bot/data/aliases.txt`. Delete everything there and input your aliases one per line, with the name in the other list as the first item.
5. Now, input the links to the wikipedia pages for each item in `bot/data/wikipedia.txt`. You can manually enter them in, making sure the name matches the items in the other list. You can also run `generate_wikipedia.py` in the `scripts` folder a few times to generate the list for you. You will still have to manually go through to ensure the correct link was found. 
6. Register a bot account on the [Discord Developers Portal](https://discordapp.com/developers/applications/). To do so, create a new application. Name your application, then navigate to the `Bot` section, and add a bot. Change your application name if necessary. Update `setup.sh` with your bot token (`Bot` section), client secret (`General Information` section), and Discord user id. You can also generate your bot invite link. Go to the `OAuth2` section and check `bot` in the `Scopes` section. In the `Bot Permissions` secion, check `Send Messages`, `Embed Links`, and `Attach Files`. Copy the URL generated and update `config.py`.
7. Great! Now we will need to add images. Create a new GitHub repository to host your images [here](https://github.com/new).

These next steps will be the most difficult to do online, though it is possible.

8. You will need to upload at least one picture of each item on the list, but more is definitely reccomended. These will be the pictures you see when using the bot, so more variety and more pictures is better. Get some friends to help out. The repository structure should be `category_name/item_name/image_name`. Images should be smaller than 8MB and in a `.png`, `.jpg`, or `.jpeg` format. You can see examples in the [example section](#examples).

Once you have all of this set up, it's now time to run your bot.

9. Clone the code repo locally (if you haven't already) with `git clone CODE_REPO_URL`. Change into that directory with `cd REPO_NAME`.
10. Install a local Redis server by running `chmod +x install-redis.sh && ./install-redis.sh`. Start your Redis server with `redis-server`. [Source](https://redis.io/topics/quickstart)
11. Install any necessary packages with `pip install -r requirements.txt`. You may also want to setup a python virtual environment to avoid package conflicts before installing packages.
12. You are now ready to run the application! Setup the environment with `source setup.sh`. Start the bot with `python3 -m bot`.

**Congrats! You just created your own ID Discord bot.** Add your bot to the Discord server of your choice using the invite link generated in step 6.

If there are any issues or you have any questions, let us know in the Bird-ID [Discord support server.](https://discord.gg/xDqYddK)

# Examples

* **Reach for the Stars ID Bot** - [https://github.com/tctree333/Reach-For-The-Stars-Bot]
* **Reach for the Stars ID Bot Images** - [https://github.com/tctree333/Reach-For-The-Stars-Images]
* **Bird-ID** - [https://github.com/tctree333/Bird-ID] (doesn't use this template, more advanced)

# Hosting

There are many options for hosting a bot, you can run it on your own computer, run it on a Raspberry Pi, or find cloud hosting options. This repo is setup to use Heroku like Bird-ID, but there are drawbacks as Heroku is fairly underpowered and will restart your bot once a day. If you are planning to use Heroku, you will want to use their cloud Redis databases. See Bird-ID for the code.