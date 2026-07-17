# Packwiz Guide (via unsup)

A step-by-step guide to creating and distributing a modpack using [packwiz](https://packwiz.infra.link/) with [unsup](https://git.sleeping.town/exa/unsup) auto-updating, via [Prism Launcher](https://prismlauncher.org/).

Please note this guide assumes you have a basic understanding of GitHub, Git, and modding in general. If you are new to any of these topics, please read up on them before proceeding.

---

## Step 1: Fork the template repository

Fork this template repository to your GitHub account.

## Step 2: Clone the forked repository

Clone the forked repository to your local machine:

```bash
git clone https://github.com/your-username/your-repo.git
cd your-repo
```

## Step 3: Configure `unsup.ini`

Open the `unsup.ini` file in the main folder and change the `source` line to point to your forked repository. It should look like this:

```ini
source=https://raw.githubusercontent.com/username/repo_name/refs/heads/main/modpack_name/pack.toml
```

Where:
- `username` — your GitHub username
- `repo_name` — the name of your forked repository
- `modpack_name` — the name of the folder in your repository that contains the `pack.toml` file

Save the file after making this change.

## Step 4: Download Packwiz GUI

Download **Packwiz GUI** from the [releases page](https://github.com/AmberIsFrozen/PW-GUI/releases).

> **Note:** This guide is based on using the JAR file. You can try the EXE if you prefer, but Windows has not been tested.

## Step 5: Create a new modpack

Run the JAR file:

```bash
java -jar PW-GUI-1.2.0-all.jar
```

Then in the GUI:
1. Click **Download Packwiz**, then **Create new modpack**.
2. Either import from CurseForge or make a fresh pack.
3. For the **file location**, select the folder where you cloned your forked repository.

## Step 6: Add mods

Add any mods, etc. to the `pack.toml` file in the Packwiz folder. You can do this by either:

- Editing the file directly, or
- Using the GUI to add mods

## Step 7: Increment the version

Once all changes for that version of the modpack are complete:

1. Click **Modpack config**.
2. Go to **Version**.
3. Increment the version number.

## Step 8: Commit and push

Once you have made your changes, commit and push them to your repository on GitHub:

```bash
git add .
git commit -m "Update modpack"
git push
```

## Step 9: Test in Prism Launcher

1. Open **Prism Launcher** and click **Add Instance**.
2. Create a version that matches your Minecraft and modloader versions exactly.
3. Right-click the instance and select **Folder**.
4. Inside the `minecraft/.minecraft` folder, drag in the `unsup.ini` file.
5. Back in Prism Launcher, right-click the instance again and select **Edit Instance**.
6. Under **Version**, select **Import Components**, then select the `com.unascribed.unsup.json` file. This will import the modpack into Prism Launcher.
7. **Export the instance** ***BEOFRE*** you run it (as a **Prism .zip** — a MultiMC zip or others will break unsup) to ensure a small file size.
8. Run it as a test to make sure everything works.

## Step 10: Share your modpack

If everything works, you can now share your modpack with others.

### Using Prism Launcher
They simply need to:

1. Drag the zip into Prism Launcher.
2. Launch it.

### Using Other Launchers
Here Unsup needs to be installed, a launch argument added, and the .ini file added manually to the .minecraft folder.

1. Download the newest **stable** unsup.jar from the [offical releases](https://git.sleeping.town/exa/unsup/releases).
2. Locate the JVM Arguments and add `-javaagent:unsup-x.x.x.jar` in the beggining (should look like `unsup-1.2.7.jar`.)
3. Download the unsup.ini from your repository.
4. Verify both unsup-x.x.x.jar and unsup.ini files are in the correct .minecraft directory.
5. Launch as normal.

> **Recommendation:** Add the zip and unsup.ini to **GitHub Releases** for your repository so that others can easily download it. 

---

## Adding more mods later

To add more mods, simply repeat **Steps 6–8**. Users will automatically be prompted to update the modpack when they launch it.
