===============================
Community Windows Release Notes
===============================

.. contents:: Topics


v0.2.0
======

Release Summary
---------------

This is the first proper release of the ``community.windows`` collection on 2020-07-18.
The changelog describes all changes made to the modules and plugins included in this collection since Ansible 2.9.0.


Minor Changes
-------------

- win_disk_facts - Set output array order to be by disk number property - https://github.com/ansible/ansible/issues/63998
- win_domain_computer - ``sam_account_name`` with missing ``$`` will have it added automatically (https://github.com/ansible-collections/community.windows/pull/93)
- win_domain_computer - add support for offline domain join (https://github.com/ansible-collections/community.windows/pull/93)
- win_domain_group_membership - Add multi-domain forest support - https://github.com/ansible/ansible/issues/59829
- win_domain_user - Added the ``identity`` module option to explicitly set the identity of the user when searching for it - https://github.com/ansible/ansible/issues/45298
- win_firewall- Change req check from wmf version to cmdlets presence - https://github.com/ansible/ansible/issues/63003
- win_firewall_rule - add parameter to support ICMP Types and Codes (https://github.com/ansible/ansible/issues/46809)
- win_iis_webapplication - add new options ``connect_as``, ``username``, ``password``.
- win_iis_webapplication - now uses the current application pool of the website instead of the DefaultAppPool if none was specified.
- win_nssm - Implement additional parameters - (https://github.com/ansible/ansible/issues/62620)
- win_pester - Only execute ``*.tests.ps1`` in ``path`` to match the default behaviour in Pester - https://github.com/ansible/ansible/issues/55736

Removed Features (previously deprecated)
----------------------------------------

- win_disk_image - removed the deprecated return value ``mount_path`` in favour of ``mount_paths``.

Bugfixes
--------

- **security issue** win_unzip - normalize paths in archive to ensure extracted files do not escape from the target directory (CVE-2020-1737)
- psexec - Fix issue where the Kerberos package was not detected as being available.
- psexec - Fix issue where the ``interactive`` option was not being passed down to the library.
- win_credential - Fix issue that errors when trying to add a ``name`` with wildcards.
- win_domain_computer - Fix idempotence checks when ``sAMAccountName`` is different from ``name``
- win_domain_computer - Honour the explicit domain server and credentials when moving or removing a computer object - https://github.com/ansible/ansible/pull/63093
- win_domain_user - Better handle cases when getting a new user's groups fail - https://github.com/ansible/ansible/issues/54331
- win_format - Idem not working if file exist but same fs (https://github.com/ansible/ansible/issues/58302)
- win_format - fixed issue where module would not change allocation unit size (https://github.com/ansible/ansible/issues/56961)
- win_iis_webapppool - Do not try and set attributes in check mode when the pool did not exist
- win_iis_website - Actually restart the site when ``state=restarted`` - https://github.com/ansible/ansible/issues/63828
- win_partition - Fix invalid variable name causing a failure on checks - https://github.com/ansible/ansible/issues/62401
- win_partition - don't resize partitions if size difference is < 1 MiB
- win_timezone - Allow for _dstoff timezones
- win_unzip - Fix support for paths with square brackets not being detected properly
