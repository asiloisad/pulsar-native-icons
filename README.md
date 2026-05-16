# native-icons

Show native OS file icons in Pulsar. Uses the icon that Windows Explorer, macOS Finder, or the Linux desktop theme would show for the same file type.

## Features

- **Native OS icons**: Uses system file icons instead of bundled icon fonts.
- **Support mode**: Adds native icons only for greenlisted files, alongside another icon package.
- **Service mode**: Registers icon services and can be used as the primary icon package.
- **CSS-compatible filters**: Greenlist and blacklist support simple filename patterns in support mode.
- **Custom file types**: Honours Pulsar's `core.customFileTypes` mappings.
- **Embedded-icon binaries**: `.exe`, `.lnk`, `.ico`, `.dll`, `.url`, `.scr`, `.msi` can use their real per-file icon.

## Installation

To install `native-icons` search for [native-icons](https://web.pulsar-edit.dev/packages/native-icons) in the Install pane of the Pulsar settings or run `ppm install native-icons`. Alternatively, you can run `ppm install asiloisad/pulsar-native-icons` to install a package directly from the GitHub repository.

## Modes

Use `support` mode when another icon package is already active. It does not register services or mutate DOM elements. It injects one CSS rule per greenlisted pattern using the `.icon[data-name...]::before` convention used by tree-view, tabs, fuzzy finder, find-and-replace, archive-view, and many community packages. Files outside the greenlist are untouched.

Use `service` mode when `native-icons` is your primary icon package. It registers services, tags supported file elements, and returns icon classes to consumers. Greenlist and blacklist are ignored in this mode. Files receive their native file icon, and directories use Pulsar's default folder icon.

## Provided Service `file-icons.element-icons`

Provided only in `service` mode.

Lets other packages iconize their own DOM elements. Returns a `Disposable`.

## Provided Service `atom.file-icons`

Provided only in `service` mode.

Provides `iconClassForPath(path)` for synchronous icon class lookup.

## Contributing

Got ideas to make this package better, found a bug, or want to help add new features? Just drop your thoughts on GitHub. Any feedback is welcome!
