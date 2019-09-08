# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'etc'
require 'pathname'

Vagrant.configure("2") do |config|
    # define synced folders
    config.vm.synced_folder ".", "/home/vagrant/fightfor-kong"

    config.vm.define "ffkong" do |ffkong|
        # define virtualization provider
        ffkong.vm.provider "virtualbox"
        # define box
        ffkong.vm.box = "bento/ubuntu-16.04"

        config.vm.provider "virtualbox" do |v|
            # define RAM in MBs
            v.memory = 1024
            # define number of vCPUs
            v.cpus = 1
        end
    end

    # forward SSH agent
    config.ssh.forward_agent = true
    config.ssh.insert_key = false

    config.vm.network :forwarded_port, guest: 22, host: 2407, id: "ssh", auto_correct: false
    config.vm.network :forwarded_port, guest: 80, host: 8000, id: "kong_http"
    config.vm.network :forwarded_port, guest: 443, host: 8443, id: "kong_https"
    config.vm.network :forwarded_port, guest: 8001, host: 8001, id: "kong_admin_http"
    config.vm.network :forwarded_port, guest: 8444, host: 8444, id: "kong_admin_https"
    config.vm.network :forwarded_port, guest: 8080, host: 8080, id: "kong_dashboard"

    # provision with Ansible
    config.vm.provision :ansible do |ansible|
        ansible.playbook = "app-fightfor-kong.yml"
        ansible.host_key_checking = false
        ansible.vault_password_file = ".ansible-vault-password"
        if ENV['ANSIBLE_TAGS'] != ""
            ansible.tags = ENV['ANSIBLE_TAGS']
        end

        ansible.extra_vars = {
            is_vagrant: true,
        }
    end
end
