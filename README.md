# Connect

[![IRC][IRC Badge]][IRC]

###### [Usage](#usage) | [Configuration](#configuration) | [Contributing](CONTRIBUTING)

> [Kakoune] extension to connect to client / session.

[![YouTube](https://img.youtube.com/vi/v_Ffno9wiJ4/0.jpg)](https://youtu.be/v_Ffno9wiJ4)

## Dependencies

- [Shell]

## Installation

``` sh
ln --symbolic $PWD/bin/kak-connect ~/.local/bin/
```

## Running

- When `$KAKOUNE_{SESSION,CLIENT}` are set: Open in the specified client
- When `$KAKOUNE_SESSION` is set: Connect to the specified session
- Else: Fall back to `kak`

## Usage

Add a `:terminal` command:

``` kak
define-command terminal -params .. %{
  shell \
    -export session \
    -export client \
    %sh(echo $TERMINAL) -e %arg(@) \
    %sh(test $# = 0 &&
      echo $SHELL
    )
}
```

Launch a terminal then execute in it:

``` sh
kak-connect <file>
```

The file will be opened in the client from where `:terminal` was executed.

You can configure your applications to use `kak-connect` instead of `kak`.

## Configuration

Configure your shell.

``` sh
EDITOR=kak-connect
```

``` sh
alias kak=kak-connect
```

[Kakoune]: http://kakoune.org
[IRC]: https://webchat.freenode.net?channels=kakoune
[IRC Badge]: https://img.shields.io/badge/IRC-%23kakoune-blue.svg
[Shell]: https://github.com/alexherbo2/shell.kak
