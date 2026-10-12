# Quan Yuan's Academic Homepage

Personal homepage built with [AcadHomepage](https://github.com/RayeRen/acad-homepage.github.io), a Jekyll template. The original template is MIT-licensed; see [LICENSE](LICENSE).

Edit `_config.yml` for profile information, `_pages/about.md` for the main content, and `_data/navigation.yml` for navigation. The portrait and research image are `avatar.jpg` and `SRTP_fig.png`.

## Local preview on Windows

Install Ruby+Devkit and Bundler, then run these commands in the project directory in PowerShell:

```powershell
bundle install
bundle exec jekyll serve --host 127.0.0.1 --port 4000 --livereload --force_polling
```

If PowerShell cannot find `ruby` or `bundle`, add the Ruby installation's `bin` directory to the current terminal's PATH first. For the Ruby installation at `C:\Ruby33-x64`:

```powershell
$env:Path = 'C:\Ruby33-x64\bin;' + $env:Path
ruby --version
bundle --version
```

This PATH change applies to the current PowerShell session. To make it persistent, add `C:\Ruby33-x64\bin` to your Windows user `Path` environment variable and restart the terminal application.

Open <http://127.0.0.1:4000/> and leave the terminal running. Press `Ctrl+C` to stop the server. Opening `_pages/about.md` or the source files as plain HTML will not render the site.

If an existing `Gemfile.lock` still selects GitHub Pages 215 / Jekyll 3.9.0, update the Pages dependency before starting the server:

```powershell
bundle update github-pages
bundle exec jekyll --version
```

The Gemfile requires GitHub Pages 232 or newer. Version 232 uses Jekyll 3.10.0, which fixes the Ruby 3.3 logger error (`undefined method [] for nil` in `logger.rb`). Updating only Nokogiri does not update this older Jekyll version. Commit the updated `Gemfile.lock` along with `Gemfile` after a successful update.

Warnings that `csv`, `base64`, or `bigdecimal` will no longer be default gems in Ruby 3.4 are separate from that logger error; they do not stop a Ruby 3.3 preview.

GitHub Pages can build the Jekyll source directly. For a project site under `username.github.io/repository-name`, set `baseurl` in `_config.yml` to `/repository-name`.

The current `_config.yml` is prepared for the personal site `Deeper-OZ1/Deeper-OZ1.github.io`, with `url: "https://deeper-oz1.github.io"` and an empty `baseurl`. If you publish to another repository, update `repository`, `url`, and `baseurl` accordingly. These settings do not create or upload a GitHub repository.

The SEO template uses Jekyll's `absolute_url` filter, so local preview does not need a Git `origin` remote to generate page URLs. If Jekyll reports `No repo name found`, check that you are using the current configuration and template. Restart the preview server after editing `_config.yml`.
