# ansible-role-apt-repository

This Ansible role configures additional apt repositories, including the package
signing keys.

## Variables

The following table lists the available variables and their default values:

| Variable                      | Default | Description                     |
| ----------------------------- | ------- | ------------------------------- |
| `apt_repository_components`   | `main`  | The list of components.         |
| `apt_repository_key_checksum` | `""`    | The checksum of the key file.   |
| `apt_repository_key_url`      | `""`    | The URL for the key file        |
| `apt_repository_name`         |         | The name of the repository.     |
| `apt_repository_suite`        |         | The suite or distribution name. |
| `apt_repository_type`         | `deb`   | The type of the repository.     |
| `apt_repository_url`          |         | The URL for the repository.     |

**Note:** If the `apt_repository_suite` variable is not defined, its value is
dynamically derived from `ansible_distribution_release`.

## Usage

Please note that, at least for now, the role is not available from Ansible
Galaxy. To retrieve the role, run the following command in your `roles`
directory:

```shell
git clone https://github.com/jakan0/ansible-role-apt-repository.git jakan0.apt_repository
```

Once the role has been retrieved, a simple playbook that utilizes this role
would look something like this:

```yaml
- hosts: debian
  roles:
    - role: jakan0.apt_repository
      vars:
        apt_repository_name: example
        apt_repository_key_url: https://packages.example.com/gpg
        apt_repository_key_checksum: sha256:e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855
        apt_repository_url: https://packages.example.com
```

## License

MIT
