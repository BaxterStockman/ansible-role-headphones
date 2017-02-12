# Ansible Role - Headphones

A role for managing a
[Headphones](https://github.com/Headphones/HeadphonesServer) installation.

## Requirements

This role is appropriate for systems using
[systemd](https://www.freedesktop.org/wiki/Software/systemd/) as a service
manager.  The role will abort if it detects that `ansible_service_mgr` is
a defined value other than `"systemd"`.

_This role does not install Headphones itself or any of its dependencies_.
You must install Headphones prior to applying the role.

## Role Variables

- `headphones_systemd_supplementary_groups` - a list of groups keyed to the
  Headphones unit's `SupplementaryGroups`.  Default is `['downloads']`.
- `headphones_settings` - a hash of settings to merge into Headphones's
  configuration file.  By default the hash is empty.
- `headphones_data_dir` - Corresponds to the `--datadir` command line option to
  `Headphones.py`.  This is where Headphones stores its database, cache, and
  logs, among other assets.  Defults to `/var/data/headphones`.
- `headphones_config_file` - The path to Headphones' configuration file.
  Corresponds to the `--config` command line option to `Headphones.py`.
  Defaults to `{{ headphones_data_dir }}/config.ini`.

## Dependencies

None.

## Example Playbook

```yaml
- hosts: headphones
  roles:
    - role: BaxterStockman.headphones
      headphones_settings:
        core:
          port: 8111
        manage:
          library: /my/media/library
```

## License

MIT

## Author Information

Matt Schreiber <mschreiber@gmail.com>
