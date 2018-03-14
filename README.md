grpc_plugin
=====

A rebar plugin
inspired by [Reber3 gpb plugin](https://github.com/lrascao/rebar3_gpb_plugin).
automatically compiling .proto files using [grpc_lib](https://github.com/Bluehouse-Technology/grpc_lib).

Build
-----

    $ rebar3 compile

Use
---

Add the plugin to your rebar config:

```erlang
{plugins, [
           { grpc_plugin, ".*", {git, "https://github.com/ajiyoshi-vg/grpc_lib.git", {branch, master}}}
          ]}.

{grpc_opts,[
            {i, "priv"}
            , {module_name_prefix, "pb_"}
            , {o_erl, "src"}
            , {strings_as_binaries, true}
            , type_specs
            , {generate, client} % or {generate, server}
           ]}.

{provider_hooks, [
                  {pre, [
                         {compile, grpc_plugin}
                        ]}
                 ]}.
```

Then just compile.


```bash
    $ rebar3 compile
```
