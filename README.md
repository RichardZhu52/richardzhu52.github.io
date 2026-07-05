# Academic Pages

**Academic Pages is a GitHub Pages template for personal and professional portfolio-oriented websites.**

![Academic Pages template example](images/themes/homepage-light.png "Academic Pages template example")

# Getting Started

1. Register a GitHub account if you don't have one and confirm your e-mail (required!)

2. Click the **Use this template** button in the top right.

3. On the **New repository** page, enter your public repository name as **[your GitHub username].github.io**, which will also become your website URL.

4. Edit the site-wide configuration in `_config.yml` and double check that:

   * `url` matches your GitHub Pages URL.
   * `repository` matches your GitHub repository.

5. Add your site content. Upload files (PDFs, ZIP files, etc.) to the `files/` directory. They will be available at:

   ```
   https://[your GitHub username].github.io/files/example.pdf
   ```

6. Check the GitHub Pages deployment status under your repository **Settings → Pages**.

7. (Optional) Use the notebooks or Python scripts in `markdown_generator/` to generate publication and talk pages from a TSV file.

See more information at https://academicpages.github.io/.

## Additional Tutorials

* https://jayrobwilliams.com/posts/2020/06/academic-website/

---

# Running Locally

Previewing your website locally before pushing changes to GitHub is highly recommended.

## Option 1 (Recommended): Native Installation

### First-time setup

Clone your repository:

```bash
git clone https://github.com/<your-username>/<your-username>.github.io.git
cd <your-username>.github.io
```

### Linux / Windows Subsystem for Linux

Install the required packages:

```bash
sudo apt update
sudo apt install ruby-dev ruby-bundler nodejs
```

If packages cannot be located:

```bash
sudo apt update && sudo apt upgrade -y
```

and then retry the installation.

---

### macOS (Recommended)

> **Note:** On some Macs, `brew install ruby` may fail due to Homebrew Portable Ruby download issues. The following installation method avoids those issues by installing Ruby directly using `rbenv`.

#### 1. Install rbenv

```bash
git clone https://github.com/rbenv/rbenv.git ~/.rbenv

echo 'export PATH="$HOME/.rbenv/bin:$PATH"' >> ~/.zshrc
echo 'eval "$(rbenv init - zsh)"' >> ~/.zshrc

exec zsh
```

#### 2. Install ruby-build

```bash
git clone https://github.com/rbenv/ruby-build.git ~/.rbenv/plugins/ruby-build
```

#### 3. Install Ruby

```bash
rbenv install 3.3.5
rbenv global 3.3.5
```

Verify the installation:

```bash
ruby -v
which ruby
```

You should see something similar to:

```text
ruby 3.3.5 ...
```

and

```text
/Users/<username>/.rbenv/shims/ruby
```

#### 4. Install Node.js

Install Node however you normally manage packages on your machine (Homebrew, nvm, etc.). For example:

```bash
brew install node
```

#### 5. Install Bundler

```bash
gem install bundler
```

---

### Install project dependencies

From the repository root:

```bash
bundle install
```

The first installation may take several minutes because Ruby gems containing native extensions must be compiled.

If successful, you'll see a new `vendor/` directory.

---

### Launch the local website

Always launch Jekyll through Bundler:

```bash
bundle exec jekyll serve -l -H localhost
```

Then open:

```
http://localhost:4000
```

The site will automatically rebuild whenever Markdown or HTML files change.

---

## Daily Usage

Once everything has been installed successfully, you **do not need to repeat any installation steps.**

Whenever you want to work on your website:

```bash
cd <your-username>.github.io
bundle exec jekyll serve -l -H localhost
```

Open:

```
http://localhost:4000
```

That's it.

If you pull changes that modify the `Gemfile`, simply rerun:

```bash
bundle install
```

before launching Jekyll again.

---

## Troubleshooting

### `Could not find bundler (...) required by Gemfile.lock`

If your local Bundler version differs from the one recorded in `Gemfile.lock`, you can safely regenerate the lockfile:

```bash
rm Gemfile.lock
bundle install
```

---

### `linked to incompatible libruby`

If you see an error similar to:

```
linked to incompatible libruby
```

your gems were compiled against a different Ruby installation.

Remove the locally installed gems:

```bash
rm -rf vendor .bundle
```

Then reinstall:

```bash
bundle install
```

---

### `jekyll: command not found`

Run Jekyll using:

```bash
bundle exec jekyll serve -l -H localhost
```

instead of

```bash
jekyll serve
```

`bundle exec` ensures Jekyll uses the exact gem versions installed for this project.

---

### Permission errors during `bundle install`

Install gems locally:

```bash
bundle config set --local path vendor/bundle
bundle install
```

---

### Linux build dependencies

Some Linux distributions also require:

```bash
sudo apt install build-essential gcc make
```

---

# Using Docker

If you prefer not to install Ruby locally, or want an isolated environment, you can run the website using Docker.

## Prerequisites

* Docker Desktop installed
* Docker Engine running

Verify Docker is available:

```bash
docker --version
docker compose version
docker info
```

If `docker info` reports that it cannot connect to the Docker daemon, start Docker Desktop and wait until it finishes launching.

---

## Build and run

From the repository root:

```bash
chmod -R 777 .
docker compose up
```

Once the container finishes building, open:

```
http://localhost:4000
```

---

# Using the DevContainer in VS Code

If you use Visual Studio Code, this repository includes a Dev Container configuration.

Normally VS Code will detect it automatically and prompt you to reopen the repository inside the container.

If not, manually run:

**F1 → Dev Containers: Reopen in Container**

VS Code will restart inside the development container and automatically host the website at:

```
http://localhost:4000
```

Changes to your files will automatically trigger a rebuild.

---

# Maintenance

Bug reports and feature requests should be submitted via GitHub Issues:

https://github.com/academicpages/academicpages.github.io/issues/new/choose

Questions about customizing the template are welcome in GitHub Discussions:

https://github.com/academicpages/academicpages.github.io/discussions

This repository was forked (then detached) by Stuart Geiger from the Minimal Mistakes Jekyll Theme by Michael Rose (MIT License). It is currently maintained by Robert Zupko, and additional maintainers are welcome.

---

## Bugfixes and Enhancements

If you have bug fixes or enhancements, submit them as a pull request by **forking** the repository rather than using the template directly.

You can later synchronize your fork with the upstream repository to receive updates.

Because Academic Pages is distributed as a template, updating an already-customized repository may produce merge conflicts. Rebasing or cherry-picking upstream commits usually works well, but if you are uncomfortable with Git, another option is to save your Markdown and configuration files, recreate the repository from the latest template, and copy your content back in.

---

<div align="center">

![pages-build-deployment](https://github.com/academicpages/academicpages.io/actions/workflows/pages/pages-build-deployment/badge.svg)

[![GitHub contributors](https://img.shields.io/github/contributors/academicpages/academicpages.github.io.svg)](https://github.com/academicpages/academicpages.github.io/graphs/contributors)

[![GitHub release](https://img.shields.io/github/v/release/academicpages/academicpages.github.io)](https://github.com/academicpages/academicpages.github.io/releases/latest)

[![GitHub license](https://img.shields.io/github/license/academicpages/academicpages.github.io?color=blue)](https://github.com/academicpages/academicpages.github.io/blob/master/LICENSE)

[![GitHub stars](https://img.shields.io/github/stars/academicpages/academicpages.github.io)](https://github.com/academicpages/academicpages.github.io)

[![GitHub forks](https://img.shields.io/github/forks/academicpages/academicpages.github.io)](https://github.com/academicpages/academicpages.github.io/fork)

</div>
