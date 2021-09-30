gleam
===

We use Ubuntu 20.04 LTS.

Since we explore using Gleam as our main programming language, we shall treat it as one of our projects.

Gleam, in turn, is developed against Erlang and Rust.

Erlang is Gleam's target, Rust is the language used to write Gleam's compiler.

Thus, we concede our principle to use only system-provided packages for these three.

## Rust

We use `rustup` to manage Rust installations.

```
curl https://sh.rustup.rs | less # Always inspect scripts you're about to run!
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Then, `rustup  --default-toolchain nightly --profile minimal -y`.

I'm currently using `2021-09-26`. We should set up a CI system that checks if gleam builds and its tests run.

## Erlang

Given that we are using cutting edge stack, we also prefer to use cutting-edge Erlang. For this we are using a `.deb` file by Erlang Solutions. Currently, we're using R24.0.5.

```
wget https://packages.erlang-solutions.com/erlang/debian/pool/esl-erlang_24.0.5-1~ubuntu~focal_amd64.deb -O /tmp/erl.deb
sudo apt install libncurses5 libwxbase3.0-dev libwxgtk3.0-gtk3-dev libsctp1
sudo dpkg -i /tmp/erl.deb
rm /tmp/erl.deb
```

## Gleam

Clone the project and run `make install`, it will install the compiler locally.

To work with your own projects you'll need `rebar3`, which you can get
from S3:

```
mkdir -p ~/.local/bin
wget https://s3.amazonaws.com/rebar3/rebar3 -O ~/.local/bin/rebar3 && chmod +x ~/.local/bin/rebar3
```

(add `~/.local/bin` to your PATH environment variable in your `~/.bashrc` if you haven't yet).
