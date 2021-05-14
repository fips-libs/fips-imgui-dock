fips-imgui-dock
===============

Fipsified Dear ImGui docking branch (https://github.com/ocornut/imgui)

fips build system: https://github.com/floooh/fips

## How to integrate:

Add the dependency to your fips.yml file:

```yaml
imports:
    fips-imgui-dock:
        git: https://github.com/fips-libs/fips-imgui-dock
```

Use imgui-dock as dependency in your targets:

```cmake
fips_begin_*(...)
    ...
    fips_deps(imgui-dock)
fips_end_*(...)
```
