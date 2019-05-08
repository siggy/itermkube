## Kubernetes Context in iTerm2's Status Bar

This guide demonstrates displaying the current Kubernetes context in iTerm2's
Status Bar.

Note: This requires iTerm2 3.3+.

![iTerm Kube](assets/images/itermkube.png "iTerm Kube")

### Install iTerm2 Shell Integration

`iTerm2` > `Install Shell Integration`

This will add a line to your `.bash_profile`:

```bash
test -e "${HOME}/.iterm2_shell_integration.bash" && source "${HOME}/.iterm2_shell_integration.bash"
```

### Add the `kubecontext` user variable

Before `.iterm2_shell_integration.bash` is loaded, add this function:

```bash
function iterm2_print_user_vars() {
  iterm2_set_user_var kubecontext $(kubectl config current-context)
}
```

### Add `kubecontext` Status Bar component

1. `iTerm2` > `Preferences` > `Profiles` > `Session` > `Configure Status Bar`
2. Drag a new `Interpolated String` component to `Active Components`.
3. Select the new component and click `Configure Component`.
4. Set `String Value` to `\(user.kubecontext)`
