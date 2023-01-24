# tmux-choose-pane

Open a picker to choose pane. Meanwhile, show current command and work directory for each pane.

![preview.jpg](https://media.githubusercontent.com/media/adoyle-h/_imgs/master/github/tmux-choose-pane/preview.jpg)

## Installation

You can use `git` or `curl` to install it.

### Using git

```sh
git clone https://github.com/adoyle-h/tmux-choose-pane.git .

# Add tmux-choose-pane to PATH
sudo ln -s "$PWD/tmux-choose-pane/tmux-choose-pane" /usr/local/bin/
```

### Using curl

```sh
curl -LO 'https://raw.githubusercontent.com/adoyle-h/tmux-choose-pane/master/tmux-choose-pane'
chmod +x ./tmux-choose-pane
sudo mv ./tmux-choose-pane /usr/local/bin/
```

## Usage

### .tmux.conf

Before calling `tmux-choose-pane`, you should set `pane-border-format` option in your `.tmux.conf` file.

For example,

```
## Pane
set -g pane-base-index 1
set -g pane-border-status off
set -g pane-border-style 'bg=black fg=#4C4C4E italics'
set -g pane-active-border-style 'bg=black fg=#428FFF italics bold'
set -g pane-border-format '≺ #{pane_current_command} #{?pane_title,#{pane_title},#{pane_current_path}} ≻'

# The default pane title is hostname, change it to empty
set-hook -g after-new-window 'selectp -T ""'
set-hook -g after-new-session 'selectp -T ""'
set-hook -g after-split-window 'selectp -T ""'

# Press '-' to choose pane
bind - run-shell tmux-choose-pane
```

You can change these tmux options and key-bindings for your needs.

### tmux-choose-pane

Just call `tmux-choose-pane` to trigger the picker.

And `tmux-choose-pane -h` to print usage.

```
Usage: [<ENV_OPTS>] tmux-choose-pane

ENV_OPTS:
  border_bg=#19191A            The background color of pane-border-style
  border_fg=#A2A2A2            The background color of pane-border-style
  active_border_bg=#081A33     The background color of pane-active-border-style
  active_border_fg=#428FFF     The front color of pane-active-border-style
  pane_border_status=top       Turn pane border status lines off or set their position. Values: off | top | bottom
  display_time=10000           Display duration in milliseconds
```

## Suggestion, Bug Reporting, Contributing

Please read [./docs/CONTRIBUTING.md](./docs/CONTRIBUTING.md) before opening new Issue/Discussion/PR and posting any comments.

## Copyright and License

Copyright 2023 ADoyle (adoyle.h@gmail.com) Some Rights Reserved.
The project is licensed under the **Apache License Version 2.0**.

Read the [LICENSE][] file for the specific language governing permissions and limitations under the License.

Read the [NOTICE][] file distributed with this work for additional information regarding copyright ownership.

## Other Projects

- [Other shell projects created by me](https://github.com/adoyle-h?tab=repositories&q=&type=source&language=shell&sort=stargazers)

<!-- Links -->

[LICENSE]: ./LICENSE
[NOTICE]: ./NOTICE
[tags]: https://github.com/adoyle-h/tmux-choose-pane/tags
[issue]: https://github.com/adoyle-h/tmux-choose-pane/issues
[discussion]: https://github.com/adoyle-h/tmux-choose-pane/discussions
[PR]: https://github.com/adoyle-h/tmux-choose-pane/pulls
