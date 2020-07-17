
Panorama XML Snippets
=====================

The configuration snippet descriptions and the associated GitHub
repository link for each xml snippet.

Panorama can be configured using shared elements and device-specific elements. For xml configurations the use of shared
or device-specific configurations is based on the xpath location of the snippets. Set commmands also denote shared or
device-specific configurations. The provided xml snippets have variations in the .meta-cnc.yaml files specifying shared
or device-specific placement in the configuration while the set commands and default loadable configuration are shared only.

**Grouping of XML snippets**

The xml template directories are group according to the user environment:

    + `snippets_panorama`: A full Panorama configuration using shared device-group and template configurations


    + `snippets_panorama_dgtemplate_shared`: used to add shared device-group and baseline template content without Panorama system elements


    + `snippets_panorama_not_shared`: a full Panorama configuration with the device-group and stack containing all configuration elements. Nothing is shared.


    + `snippets_panorama_dgstack_notshared`: used to add additional device-groups and stack, each with full configuration elements. Nothing is shared.



.. Note::
    The template version is found in the template xml file as a tag attribute


.. Note::
    The set commands utilize the same configuration settings


General Device Configuration
----------------------------

----------------------------------------------------------------------

This section provides templated configurations for general device
settings.

Panorama Admin Users
~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/panorama_mgt_config_users.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/panorama_mgt_config_users.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/panorama_mgt_config_users.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/panorama_mgt_config_users.xml>`_ |


Management configuration superuser access

    + Administrative user name

    + Password hash stored in the configuration file

Panorama Password Complexity
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/panorama_mgt_config_pwd.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/panorama_mgt_config_pwd.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/panorama_mgt_config_pwd.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/panorama_mgt_config_pwd.xml>`_ |


Administrative user password complexity profile

    + Attributes including minimum length, characters, and history


Panorama settings
~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/panorama_system.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/panorama_system.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/panorama_system.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/panorama_system.xml>`_ |


System configuration settings for dynamic updates and network services
(eg. DNS, NTP).

    + Update schedule settings

        * Check every 30 minutes for new threat signatures
        * Hourly checks for new AV signatures
        * Check realtime for new Wildfire signatures
        * Recommended time delays and thresholds for checks and installs

    + Use SNMPv3

    + Set default DNS and NTP values

    + Set timezone to UTC

    + Provide a standard login banner warning for unauthorized users

.. Note::
    The Panorama deployment types include ```standard``` or ```cloud``` for AWS, Azure, or GCP environments.
    This is an option in the tools ```build_my_config``` utility to use the proper config option in the template.

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/panorama_setting.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/panorama_setting.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/panorama_setting.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/panorama_setting.xml>`_ |


Panorama management settings

    + Set 'enable reporting on groups' to 'yes'
    + Disable sharing unused objects with devices

    + Set an API key lifetime instead of a permanent/static value

        * default set to 525,600 minutes (1 year)

    + set export of csv log file to maximum of 1,048,576

    + Administrative lockout and access

        * failed attempts and lockout time
        * idle timeout
        * auto acquire commit lock



Security-related Device Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/device_setting.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/device_setting.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/device_setting.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/device_setting.xml>`_ |


General device settings that effect security posture. Found in Device > Setup in the GUI.

    + Wildfire: set optimal file size limits for Wildfire uploads and show verdict responses for grayware, malware and phishing

    + Session rematch: the firewall will go through all the existing sessions and apply the new security policy to any matching traffic

    + Notify User: user should be notified when web-application is blocked; enables the application response page

    + Log Suppression: disabled to ensure unique log entries even if similar session types

    + Prevent TCP and UDP buffer overflow and multi-part HTTP download evasions

        * Disable 'tcp-bypass-exceed-queue'
        * Disable 'udp-bypass-exceed-queue'

    + Enable high DP load logging

    + Prevent App-ID buffer overflow evasion

        * set bypass-exceed-queue to 'no'

    + Prevent TCP and MPTCP evasions

        * set urgent data to 'clear'
        * set drop zero flag to 'yes'
        * set bypass-exceed-oo-queue to 'no'
        * set check-timestamp-option to 'yes'
        * set strip-mptcp-option to yes

    + Set an API key lifetime instead of a permanent/static value

        * default set to 525,600 minutes (1 year)

    + set export of csv log file to maximum of 1,048,576


System Configuration
~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/device_system_shared.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/device_system_shared.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/device_system_shared.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/device_system_shared.xml>`_


System configuration settings for dynamic updates and network services
(eg. DNS, NTP).

    + Update schedule settings

        * Check every 30 minutes for new threat signatures
        * Hourly checks for new AV signatures
        * Check realtime for new Wildfire signatures
        * Recommended time delays and thresholds for checks and installs

    + Use SNMPv3

    + Set default DNS and NTP values

    + Set timezone to UTC

    + Provide a standard login banner warning for unauthorized users

.. Note::
    The management config types include static or dhcp-client.
    This is specific to each deployment and can be selected as part of the tools to build ```loadable_configs```.
    Since management interface is in the template config, this option must be included for deployment.


Logging
-------

----------------------------------------------------------------------

Logging best practice configurations for logging output and forwarding
profiles. Also Panorama-specific settings for Panorama as a log collector

.. Warning::
    **Configure logging profiles before security rules**
    The template creates a log forwarding profile call default.
    This profile is referenced in the template security rules and should be configured before the security rules.

.. Note::
    **Logging can be deployment dependent**
    The destination in the logging profile is templated to an unroutable syslog server address.
    This can vary based on actual deployment scenarios.


Log forwarding profile
~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/log_settings_profiles.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/log_settings_profiles.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/log_settings_profiles.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/log_settings_profiles.xml>`_ |


Log forward profile referenced in security rules to determine where to
forward log related events.

    + Forward all log activity to Panorama (see the reference syslog
      configuration in shared_log_settings.xml)

    + Email malicious and phishing Wildfire verdicts to the address in the
      email profile (see shared_log_settings.xml)

Device log settings
~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/shared_log_settings.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/shared_log_settings.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/shared_log_settings.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/shared_log_settings.xml>`_ |


Device event logging including sample profiles for email and syslog
forwarding.

    + Reference syslog profile that can be edited for a specific IP
      address and UDP/TCP port

    + Reference email profile that can be edited for specific email domain
      and user information

    + System, configuration, user, HIP, and correlation log forwarding to
      syslog

    + Email critical system events to the email profile


.. Note::
    **When to use email alerts**
    The purpose of select email alert forwarding is ensure not to under alert or over alert yet provide critical messages for key events.
    Under alerting reduces visibility to key events while over alerting creates too much noise in the system.
    The templates are set with a median view to capture key events without too much 'log fatigue' noise


Panorama log settings
~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/panorama_log_settings.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/panorama_log_settings.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/panorama_log_settings.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/panorama_log_settings.xml>`_ |


Panorama event logging including sample profiles for email and syslog forwarding.

    + Reference syslog profile that can be edited for a specific IP address and UDP/TCP port
    + Reference email profile that can be edited for specific email domain and user information
    + System, configuration, user, HIP, and correlation log forwarding to Panorama
    + Traffic and threat related log configuration forwarding to Panorama

Panorama log collector group
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/log_collector_group.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/log_collector_group.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/log_collector_group.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/log_collector_group.xml>`_


After you configure Log Collectors and firewalls, you must assign them to a Collector Group so that the firewalls can send logs to the Log Collectors.

This is a placeholder default log collector group providing proper log forwarding and real-time email alerting configuration.
In many cases deployments under-alert or over-alert real time losing visibility to something drastic because it is never sent to lost in then noise of too many emails.

    + Syslog all logs using the sample syslog profile
    + Email alerts for critical system logs and Wildfire malware/phishing verdicts that require immediate attention



Referenced Objects
------------------

----------------------------------------------------------------------

Address, External Dynamic List (EDL), and tag objects that are
referenced in security rules by name.


Tags
~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/tag.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/tag.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/tag.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/tag.xml>`_ |


Tags used in security rules and related objects.

        + Inbound - inbound (untrust to trust) elements

        + Outbound - outbound (trust to untrust) elements

        + Internal - internal (trust) segmentation elements


Security Profiles and Groups
----------------------------

----------------------------------------------------------------------

The key elements for security posture are security profiles and the
security rules. The templates ensure best practice profiles and
profile groups are available and can be referenced in any security
rules. The template security rules focus on 'top of the list' block
rules to reduce the attack surface.


.. Warning::
    **Profiles and subscriptions**
    All of the template security profiles other than file blocking require
    Threat Prevention, URL Filtering, and Wildfire subscriptions. Ensure
    that the device is properly licensed before applying these
    configurations.



Custom URL Category
~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_custom_url_category.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_custom_url_category.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_custom_url_category.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_custom_url_category.xml>`_ |


Placeholder for custom url categories used in security rules and url
profiles. Using these categories prevents the need to modify the
default template.


        + Block: placeholder to be used in block rules and objects to
          override default template behavior

        + Allow: placeholder to be used in permit rules and objects to
          override default template behavior

        + Custom-No-Decrypt: to be used in the decryption no-decrypt rule to
          specify URLs that should not be decrypted



File Blocking
~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_file_blocking.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_file_blocking.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_file_blocking.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_file_blocking.xml>`_ |


Security profile for actions specific to file blocking (FB).


.. Note::
    **File blocking and file types**
    The Block file type recommendation is based on common malicious file
    types with minimal impact in a Day 1 deployment. Although PE is
    considered the highest risk file type it is also used for legitimate
    purposes so blocking PE files will be deployment specific and not
    included in the template.

        + Day 1 Block file types: 7z, bat, chm, class, cpl, dll, hlp, hta,
          jar, ocx, pif, scr, torrent, vbe, wsf

        + The profiles will alert on all other file types for logging purposes


Profiles:

        + Outbound-FB: For outbound (trust to untrust) security rules

        + Inbound-FB: For inbound (untrust to trust) security rules

        + Internal-FB: For internal network segmentation rules

        + Alert-Only-FB: No file blocking, only alerts for logging purposes

        + Exception-FB: For exception requirements in security rules to avoid
          modifying the default template profiles


Anti-Spyware
~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_spyware.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_spyware.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_spyware.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_spyware.xml>`_ |


Security profile for actions specific to anti-spyware (AS).

.. Note::
    **Sinkhole addresses**
    The profiles use IPv4 and IPv6 addresses for DNS sinkholes. IPv4 is
    currently provided by Palo Alto Networks. IPv6 is a bogon address. In 9.0
    the IPv4 address is replaced by an FQDN

[9.x] Support for DNS Cloud subscription service

    + In addition to the current malicious domain push to the device, also include domain lookups using the cloud service

[10.x] Support for DNS Cloud subscription domain categories and actions

    + set malicious categories to sinkhole


Profiles:

        + Outbound-AS : For outbound (trust to untrust) security rules

            * Block severity = Critical, High, Medium
            * Default severity = Low, Informational
            * DNS Sinkhole for IPv4 and IPv6
            * Single packet capture for Critical, High, Medium severity

        + Inbound-AS : For inbound (untrust to trust) security rules

            * Block severity = Critical, High, Medium
            * Default severity = Low, Informational
            * DNS Sinkhole for IPv4 and IPv6
            * Single packet capture for Critical, High, Medium severity

        + Internal-AS : For internal network segmentation rules

            * Block severity = Critical, High
            * Default severity = Medium, Low, Informational
            * DNS Sinkhole for IPv4 and IPv6
            * Single packet capture for Critical, High, Medium severity

        + Alert-Only-AS : No blocking, only alerts for logging purposes

            * Alert all severities and malicious domain events
            * No packet capture

        + Exception-AS : For exception requirements in security rules to avoid
          modifying the default template profiles


URL Filtering
~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_url_filtering.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_url_filtering.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_url_filtering.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_url_filtering.xml>`_ |


Security profile for actions specific to URL filtering (URL).

.. Note::
    Only ``BLOCK`` categories will be listed for each profile below.
    All other URL categories will be set to ``ALERT`` in the templates for logging
    purposes. The complete list of categories can be found in the url filtering template.

[10.x] Support for local machine learning based on web content

    + block malicious content using dynamic classification


Profiles:

        + Outbound-URL : For outbound (trust to untrust) security rules

            * URL Categories
            * Site Access: Block command-and-control, malware, phishing,
              Black List (custom URL category)
            * User Credential Submission: Block all categories
            * Alert category = includes White List (custom URL category)
            * URL Filtering Settings: HTTP Header Logging (user agent, referer, X
              -Forwarded-For)
            * dynamic classification to block malicious web conent

        + Alert-Only-URL : No blocking, only alerts for logging purposes

            * Alert all categories including custom categories Black List and
              White List

        + Exception-URL : For exception requirements in security rules to
          avoid modifying the default template profiles

            * URL Categories
            * Site Access: Block command-and-control, malware, phishing,
              Black List (custom URL category)
            * User Credential Submission: Block all categories
            * Alert category = includes White List (custom URL category)
            * URL Filtering Settings: HTTP Header Logging (user agent, referer, X
              -Forwarded-For)
            * dynamic classification to block malicious web conent

.. Note::
    9.0 includes new URL categories for risk and newly created domains. In future best practices, these categories
    may be used to provide additional security protections when combined with existing URL categories. For now, these
    categories are only set to `alert`.

Anti-Virus
~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_virus.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_virus.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_virus.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_virus.xml>`_ |


Security profile for actions specific to AntiVirus (AV) and Wildfire signatures. All decoders using 'reset-both'
as actions except for the Alert-Only profile.

[10.x] Support for WF-based local machine learning to block malicious content for exe and powershell files.


Profiles:


        + Outbound-AV: For outbound (trust to untrust) security rules

        + Inbound-AV: For inbound (untrust to trust) security rules

        + Internal-AV: For internal network segmentation rules

        + Alert-Only-AV: No blocking, only alerts for logging purposes

        + Exception-AV: For exception requirements in security rules to avoid
          modifying the default template profiles


.. Note::
    **Email response codes with SMTP not IMAP or POP3**
    Reset-both is used for SMTP, IMAP, and POP3. SMTP '541' response
    messages are returned to notify that the session was blocked. IMAP and
    POP3 do not have the same response model. In live deployments, instead
    of DoS concerns with retries, the endpoints typically stop resending
    after a small number of sends with timeouts.

.. Note::
    9.0 includes support for http/2. If you are upgrading from a previous version
    ensure that this decoder matches the actions for standard http.


Vulnerability Protection
~~~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_vulnerability.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_vulnerability.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_vulnerability.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_vulnerability.xml>`_ |



Profiles:

        + Outbound-VP : For outbound (trust to untrust) security rules

            * Block severity = Critical, High, Medium
            * Alert severity = Low, Informational
            * Single packet capture for Critical, High, Medium severity

        + Inbound-VP : For inbound (untrust to trust) security rules

            * Block severity = Critical, High, Medium
            * Alert severity = Low, Informational
            * Single packet capture for Critical, High, Medium severity

        + Internal-VP : For internal network segmentation rules

            * Block severity = Critical, High
            * Alert severity = Medium, Low, Informational
            * Single packet capture for Critical, High, Medium severity

        + Alert-Only-VP : No blocking, only alerts for logging purposes

            * Alert all severities
            * No packet capture

        + Exception-VP: For exception requirements in security rules to avoid
          modifying the default template profiles

.. Note::
    A separate branch is being used as a placeholder for Brute-Force-Exceptions_. This provides a way
    to include Support recommended exceptions by ThreatID value. These can be loaded using console SET
    commands or using API-based tools

.. _Brute-Force-Exceptions: https://github.com/PaloAltoNetworks/iron-skillet/tree/bruteForceExceptions


Wildfire Analysis
~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_wildfire_analysis.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_wildfire_analysis.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_wildfire_analysis.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_wildfire_analysis.xml>`_ |


Security profile for actions specific to Wildfire upload and analysis
(WF).

.. Note::
    ``Public Cloud`` is the default
    All template profiles are configured to upload all file types in any
    direction to the public cloud for analysis.


Profiles:

        + Outbound-WF: For outbound (trust to untrust) security rules

        + Inbound-WF: For inbound (untrust to trust) security rules

        + Internal-WF: For internal network segmentation rules

        + Alert-Only-WF: No blocking, only alerts for logging purposes

        + Exception-WF: For exception requirements in security rules to avoid
          modifying the default template profiles


Security Profile Groups
~~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profile_group.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profile_group.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profile_group.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profile_group.xml>`_ |


Security profile groups based on use case


        + Inbound: For rules associated to inbound (untrust to trust) sessions

        + Outbound: For rules associated to outbound (trust to untrust)
          sessions

        + Internal: For rules associated to trust-domain network segmentation

        + Alert Only: Provides visibility and logging without a blocking
          posture


Security Rules
--------------

----------------------------------------------------------------------


Recommended Block Rules
~~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/pre_rulebase_security.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/pre_rulebase_security.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/pre_rulebase_security.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/pre_rulebase_security.xml>`_ |


Recommended block rules for optimal security posture with associated
default log-forwarding profile


        + Outbound Block Rule: Block destination IP address match based on the
          Palo Alto Networks predefined externals dynamic lists

        + Inbound Block Rule: Block source IP address match based on the Palo
          Alto Networks predefined externals dynamic lists

.. Note::
    **Security rules in the template are block only**
    The template only uses block rules. Allow rules are zone, direction
    and use case dependent. Additional templating work will provide
    recommended use case case security rules.


Default Security Rules
~~~~~~~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/post_rulebase_default_security_rules.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/post_rulebase_default_security_rules.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/post_rulebase_default_security_rules.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/post_rulebase_default_security_rules.xml>`_ |


Configuration for the default interzone and intrazone default rules


        + Intrazone

            * Enable logging at session-end using the default logging profile
            * Use the Internal security profile-group

        + Interzone

            * Explicit drop of traffic between zones
            * Enable logging at session-end using the default logging profile


Decryption
----------

----------------------------------------------------------------------


Profiles
~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/profiles_decryption.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/profiles_decryption.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/profiles_decryption.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/profiles_decryption.xml>`_ |


Recommended_Decryption_Profile. Referenced by the default decryption
rule.

        + SSL Forward Proxy

            * Server Cert Verification : Block sessions with expired certs, Block
              sessions with untrusted issuers, Block sessions with unknown cert
              status
            * Unsupported Mode Checks : Block sessions with unsupported versions,
              Blocks sessions with unsupported cipher suites

        + SSL No Proxy

            * Server Cert Verification : Block sessions with expired certs, Block
              sessions with untrusted issuers

        + SSH Proxy

            * Unsupported Mode Checks : Block sessions with unsupported versions,
              Block sessions with unsupported algorithms

        + SSL Protocol Settings:

            * Minimum Version: TLSv1.2; Max version TLSv1.3; Any TLSv1.1 errors can help find outdated
              TLS endpoints
            * Key Exchange Algorithms: RSA not recommended and unchecked
            * Encryption Algorithms: 3DES and RC4 not recommended and unavailable
              when TLSv1.2 is the min version
            * Authentication Algorithms:MD5 not recommended and unavailable when
              TLSv1.2 is the min version


Decryption Rules
~~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/pre_rulebase_decryption.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/pre_rulebase_decryption.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/pre_rulebase_decryption.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/pre_rulebase_decryption.xml>`_ |


Recommended SSL decryption pre-rules for no-decryption.

       + NO decrypt rule for select URL categories; Initially disabled in the Day 1 template until SSL decryption to be enabled


Zone Protection
---------------

----------------------------------------------------------------------


Profile
~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/zone_protection_profile.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/zone_protection_profile.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/zone_protection_profile.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/zone_protection_profile.xml>`_ |


Recommended_Zone_Protection profile for standard, non-volumetric best
practices. This profile should be attached to all interfaces within
the network.


.. Note::
    **Recon Protection**
    Default values enabled in alert-only mode; active blocking posture requires network tuning

Packet Based Attack Protection

        + IP Drop: Spoofed IP Address, Malformed

        + TCP Drop: Remove TCP timestamp, No TCP Fast Open, Multipath TCP
          (MPTCP) Options = Global


Reports
-------

----------------------------------------------------------------------


Reports
~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/reports_simple.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/reports_simple.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/reports_simple.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/reports_simple.xml>`_ |



Series of reports to look for traffic anomalies, where to apply or
remove rules, etc. Reports are grouped by topic per the report group
section below.


.. Note::
    **Zones and Subnets in report queries**
    The repo contains a separate folder for custom reports that use a
    placeholder zone called 'internet' for match conditions in reports.
    This value MUST be changed to match the actual public zone used in a
    live network. Additional zones and/or subnets to be used or excluded
    in the reports would be added in the query values.


.. Note::
    To generate reports that include PA-7000 Series log data not forwarding to Panorama,
    use Remote Device Data as the Data Source. This is only viewable from the ```All`` device group
    option and not a specific device group.


Report Groups
~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/report_group_simple.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/report_group_simple.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/report_group_simple.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/report_group_simple.xml>`_ |


Report groups allow you to create sets of reports that the system can
compile and send as a single aggregate PDF report with an optional
title page and all the constituent reports included.

Template report groups include:

Simple (included in Day One template)


        + Possible Compromise: malicious sites and verdicts, sinkhole sessions


Custom

        + User Group Activity (eg. Employee, Student, Teacher): user-id
          centric reports grouped by user type

        + Inbound/Outbound/Internal Rule Tuning: Used rules, app ports,
          unknown apps, geo information

        + Inbound/Outbound/Internal Threat Tuning: Allowed threats traversing
          the device

        + File Blocking Tuning: View of upload/download files and types with
          associated rule

        + URL Tuning: Views by categories, especially questionable and unknown
          categories

        + Inbound/Outbound/Internal Threats Blocked: Threat reports specific
          to blocking posture; complement to threat tuning

        + Non-Working Traffic: View of dropped, incomplete, or insufficient
          data sessions


Email Scheduler
~~~~~~~~~~~~~~~

`View xml snippet:` |
`8.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v8.1/templates/panorama/snippets/email_scheduler_simple.xml>`_ |
`9.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.0/templates/panorama/snippets/email_scheduler_simple.xml>`_ |
`9.1 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v9.1/templates/panorama/snippets/email_scheduler_simple.xml>`_ |
`10.0 <https://github.com/PaloAltoNetworks/iron-skillet/blob/panos_v10.0/templates/panorama/snippets/email_scheduler_simple.xml>`_ |


Schedule and email recipients for each report group. The template uses
a sample email profile configured in shared_log_settings.
