<h1 align="center">
	<img src="icon.svg" alt="Firefox Breeze theme" width="100" height="100"/><br>
 Firefox Breeze theme
</h1>

<p align="center"><strong>A Breeze theme for Firefox</strong></p>

<p align="center">This theme follows lastest Breeze Adwaita style.</p>

![Screenshot of the theme](screenshot.png)

## Description

This is a bunch of CSS code to make Firefox look closer to KDE's native apps.

This theme is supposed to work with current supported Firefox releases:

- Firefox 68
- Firefox 60 ESR
- Firefox 68 ESR
- Firefox 69 Beta
- Firefox 70 Nightly

***Firefox 60 ESR issues:***

*(Dark theme variant is broken in Firefox < 67).*

*https://developer.mozilla.org/en-US/docs/Web/CSS/@media/prefers-color-scheme#Browser_compatibility*

## Installation

### Installation script
```sh
git clone https://github.com/brombinmirko/firefox-breeze-theme/ && cd firefox-breeze-theme
./scripts/install.sh
```

#### Script options
- -f `<firefox_folder>` *optional*
	- Set custom Firefox folder path, for example `~/.mozilla/icecat/`.
	- Default: `~/.mozilla/firefox/`

- -p `<profile_folder>` *optional*
	- Set custom profile folder name, for example `e0j6yb0p.default-nightly`
	- Default: `*.default` (standard default profile)

- -g *optional*
	- Auto enable GNOMISH extra features `hide-single-tab.css` & `matching-autocomplete-width.css`


### Manual installation
1. Go to `about:support` in Firefox.

2. Application Basics > Profile Directory > Open Directory.

3. Open directory in a terminal.

4. Create a `chrome` directory if it doesn't exist.

	```sh
	mkdir -p chrome
	cd chrome
	```

5. Clone this repo to a subdirectory:

	```sh
	git clone https://github.com/brombinmirko/firefox-breeze-theme.git
	```

6. Create single-line user CSS files if non-existent or empty (at least one line is needed for `sed`):

	```sh
	[[ -s userChrome.css ]] || echo >> userChrome.css
	```

7. Import this theme at the beginning of the CSS files (all `@import`s must come before any existing `@namespace` declarations):

	```sh
	sed -i '1s/^/@import "firefox-breeze-theme\/userChrome.css";\n/' userChrome.css
	```

8. Symlink preferences file:

	```sh
	ln -s chrome/firefox-breeze-theme/configuration/user.js ../user.js
	```

9. Restart Firefox.

10. Open Firefox customization panel and move the new tab button to headerbar.

11. Be happy with your new gnomish Firefox.

## Updating
Both manual and script installation methods should create a git clone in `your-profile-folder-path/chrome/firefox-breeze-theme`, so the easiet way to update the theme is to open this folder in terminal and perform a git pull.

```sh
git pull origin master
```

> Note: Running installation script to update after cloning again the repo can work, but also can introduce duplication in CSS sheets.

## Uninstalling/removing the theme
- Go to your profile folder (Go to `about:support` in Firefox > Application Basics > Profile Directory > Open Directory).
- Remove `chrome` folder.

## Enabling optional features
Open `chrome/firefox-breeze-theme/userChrome.css` with a text editor and follow instructions to enable extra features. Keep in mind this file might change in future versions and your configuration will be lost. You can copy the @imports you want to enable to a new file named `customChrome.css` directly in your `chrome/firefox-breeze-theme` directory if you want it to survive updates. Remember all @imports must be at the top of the file, before other statements.

Alternatively you can run installation script with `-g` flag to auto install GNOMISH features.

```sh
./scripts/install.sh -g
```

*Those features are not included by default, because can introduce bugs or Firefox functionalities lost.*

- **hide-single-tab.css** *GNOMISH*

	Hide the tab bar when only one tab is open.

	You should move the new tab button somewhere else for this to work, because by default it is on the tab bar too.

- **matching-autocomplete-width.css** *GNOMISH*

	Limit the URL bar's autocompletion popup's width to the URL bar's width.

- **active-tab-contrast.css**

	Active tab better contrast.

- **system-icons.css**

	Use system theme icons instead of Adwaita icons included by theme.

- **drag-window-headerbar-buttons.css**

	Allow drag window from headerbar buttons *GNOMISH* **[BUGGED]**

	It can activate button action, with unpleasant behavior.

- **symbolic-tab-icons.css**

	Make all tab icons look kinda like symbolic icons.


Feel free to use any parts of my code to develop your own themes, I don't force
any specific license on your code.

## Special thanks
Based on **[Sai Kurogetsu/rafaelmardojai](https://github.com/rafaelmardojai/firefox-breeze-theme)** original work.
