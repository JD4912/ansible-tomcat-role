# Ansible Role: Tomcat

This Ansible role installs and configures Apache Tomcat on Debian and Red Hat-based systems.

## Requirements

- Ansible 2.9 or higher
- Target system must be either Debian-based (Ubuntu, Debian) or Red Hat-based (RHEL, CentOS, Fedora)
- Root or sudo privileges on the target system

## Role Variables

### Default Variables

```yaml
# Tomcat version to install
tomcat_version: "11.0.0"  # Placeholder for Tomcat 11
tomcat_major_version: "11"

# Installation paths
tomcat_install_dir: "/opt/tomcat"
tomcat_home: "/var/lib/tomcat"

# User and group settings
tomcat_user: "tomcat"
tomcat_group: "tomcat"

# Port configuration
tomcat_port: "8080"

# Java configuration
java_package: "openjdk-17-jdk"  # Default to JDK 17
```

### Available Tomcat Versions

```yaml
tomcat_versions_available:
  "11":
    - "11.0.0"  # Placeholder; update when released
  "10":
    - "10.1.19"
  "9":
    - "9.0.87"
  "8":
    - "8.5.99"
```

### Available Java Versions

```yaml
java_versions_available:
  debian:
    - "openjdk-8-jdk"
    - "openjdk-11-jdk"
    - "openjdk-17-jdk"
    - "openjdk-21-jdk"
  redhat:
    - "java-1.8.0-openjdk-devel"
    - "java-11-openjdk-devel"
    - "java-17-openjdk-devel"
    - "java-21-openjdk-devel"
```

## Dependencies

- Java JDK (OpenJDK 17 by default)
- Systemd (for service management)
- Curl (for downloading Tomcat)

## Example Playbook

```yaml
---
- name: Install Tomcat on Ubuntu and Red Hat
  hosts: all
  become: yes
  vars:
    tomcat_version: "10.1.19"  # Specify your desired Tomcat version
    tomcat_major_version: "10"
    java_package: "openjdk-17-jdk"  # Specify your desired Java version
  roles:
    - tomcat
```

## Features

- Installs and configures Apache Tomcat
- Sets up Tomcat user and group
- Configures systemd service
- Manages Java dependencies
- Configures proper permissions
- Sets up JAVA_HOME environment
- Downloads and extracts Tomcat tarball
- Ensures service is enabled and started

## Installation Process

1. Installs required Java version
2. Creates Tomcat user and group
3. Sets up installation directory
4. Downloads and extracts Tomcat
5. Configures systemd service
6. Sets proper permissions
7. Starts and enables Tomcat service

## Verification

After installation, you can verify Tomcat is running by:

1. Checking the service status:
   ```bash
   systemctl status tomcat
   ```

2. Accessing the default page:
   ```
   http://your-server:8080
   ```

## License

BSD

## Author Information

Your Name/Organization
