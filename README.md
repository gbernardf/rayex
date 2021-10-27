# Rayex

Rayex provides Elixir NIF bindings to [Raylib](https://www.raylib.com/)

> WIP: many of the functions on raylib are yet not implemented, check the [contributing section](#contributing) to help \
> NOTE: We are developing for the raylib 4.0-dev (that is why the CI is not passing right now, but you can use `make test` to test)

![](examples/3d_picking.gif)

## Installation

The package can be installed by adding `rayex` to your list of dependencies in `mix.exs`:

```elixir
def deps do
  [
    {:rayex, "~> 0.0.1"}
  ]
end
```

The docs can be found at [https://hexdocs.pm/rayex](https://hexdocs.pm/rayex).

## How to run

You need the following deps installed on your system:
* elixir
* raylib (**master branch**)
* pkg-config

Note: If you are using Nix or NixOS you can run __nix-shell__ to get an ready to go env to work on!

Now you can run:
```bash
mix deps.get
iex -S mix
```

Testing Rayex
```elixir
# open new window
Rayex.init_window 200, 200, 'window name'

# draw a line
Rayex.begin_drawing
Rayex.draw_line 10, 10, 50, 51, %{r: 255, g: 161, b: 0, a: 255}
Rayex.end_drawing
```

Also you can run our examples!!

## Contributing

There are a few things that you need to know about the code:
* This project aims to run each one of [those functions](https://www.raylib.com/cheatsheet/cheatsheet.html) with elixir
* To do so, we are using [Unifex](https://hexdocs.pm/unifex/readme.html) to create NIFs
* On `c_src/rayex/rayex.spec.exs` you can find the definitions that will be generated by Unifex
* On `c_src/rayex/rayex.c` you can find how they are implemented
* On `c_src/rayex/rayex.h` and `lib/unifex/code_generator/base_types/...` you can find custom types
* On `lib/rayex/unifex/raylib.ex` is where the generated functions will be stored and used for each module under `lib/rayex`, the public API

Any contributions are appreciated

## License

   Copyright 2021 Shiryel

   Licensed under the Apache License, Version 2.0 (the "License");
   you may not use this file except in compliance with the License.
   You may obtain a copy of the License at

       http://www.apache.org/licenses/LICENSE-2.0

   Unless required by applicable law or agreed to in writing, software
   distributed under the License is distributed on an "AS IS" BASIS,
   WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
   See the License for the specific language governing permissions and
   limitations under the License.
