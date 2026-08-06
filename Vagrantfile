# -*- mode: ruby -*-
# vi: set ft=ruby :

# ==============================================================================
# AutoCloud Enterprise
# Automated Private Cloud Infrastructure
#
# Author      : Wael Balhoudi
# Repository  : https://github.com/WaelBalhoudi/AutoCloud-Enterprise
#
# Description:
# This Vagrantfile provisions the infrastructure used throughout the
# AutoCloud Enterprise project. Virtual machines are configured with
# Vagrant and VirtualBox, while Ansible performs all software
# configuration and infrastructure automation.
#
# Phase:
# Phase 3 – Infrastructure Provisioning
# ==============================================================================

# ------------------------------------------------------------------------------
# Global Configuration
# ------------------------------------------------------------------------------

PROJECT_NAME = "AutoCloud"

BOX    = "bento/ubuntu-24.04"
DOMAIN = "autocloud.local"

MEMORY = 3072
CPUS   = 2

# ------------------------------------------------------------------------------
# Enterprise Infrastructure Definition
# Hostname => Static Private IP
# ------------------------------------------------------------------------------

MACHINES = {
  "cloud01"   => "10.10.10.10",
  "idm01"     => "10.10.10.20",
  "monitor01" => "10.10.10.30"
}

# ==============================================================================
# Vagrant Configuration
# ==============================================================================

Vagrant.configure("2") do |config|

  config.vm.box = BOX

  # --------------------------------------------------------------------------
  # Deployment Messages
  # --------------------------------------------------------------------------

  config.trigger.before :up do |trigger|
    trigger.info = <<~MSG

    ============================================================
               AutoCloud Enterprise Deployment
    ============================================================

    Provider : VirtualBox
    Machines : cloud01, idm01, monitor01

    Provisioning enterprise infrastructure...

    ============================================================

    MSG
  end

  config.trigger.after :up do |trigger|
    trigger.info = <<~MSG

    ============================================================
                 Infrastructure Ready
    ============================================================

    Verify connectivity:

      ansible all -i ansible/inventory/hosts.yml -m ping

    Deploy the infrastructure:

      ansible-playbook -i ansible/inventory/hosts.yml ansible/site.yml

    ============================================================

    MSG
  end

  # --------------------------------------------------------------------------
  # SSH Configuration
  # --------------------------------------------------------------------------

  config.ssh.insert_key = false
  config.ssh.keep_alive = true

  # --------------------------------------------------------------------------
  # VirtualBox Provider Defaults
  # --------------------------------------------------------------------------

  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.linked_clone = true
  end

  # --------------------------------------------------------------------------
  # Virtual Machine Definitions
  # --------------------------------------------------------------------------

  MACHINES.each do |hostname, ip|

    config.vm.define hostname do |node|

      node.vm.hostname = hostname

      node.vm.network "private_network",
        ip: ip

      node.vm.provider "virtualbox" do |vb|
        vb.name   = "#{PROJECT_NAME}-#{hostname}"
        vb.memory = MEMORY
        vb.cpus   = CPUS
      end

      node.vm.post_up_message = <<~MSG

      ------------------------------------------------------------
      #{hostname} is ready.

      Hostname : #{hostname}
      Address  : #{ip}

      Connect using:

        vagrant ssh #{hostname}

      ------------------------------------------------------------

      MSG

    end

  end

  # --------------------------------------------------------------------------
  # Future Expansion
  # --------------------------------------------------------------------------
  #
  # client01 (Windows)
  #
  # The Windows client will be introduced in a later phase to
  # simulate an enterprise employee workstation.
  #
  # Planned use cases:
  #
  # - Active Directory / LDAP authentication
  # - Nextcloud access
  # - NFS file sharing
  # - Permission validation
  # - Enterprise workflow testing
  #
  # --------------------------------------------------------------------------

end