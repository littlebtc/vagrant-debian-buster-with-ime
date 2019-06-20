$script = <<-SCRIPT
export DEBIAN_FRONTEND=noninteractive
apt-get update && apt-get upgrade -y && \
apt-get install -y --no-install-recommends \
  gdm3 gnome-shell gnome-session firefox-esr chromium\
  ibus ibus-gtk3 ibus-chewing im-config fonts-noto-cjk
SCRIPT

$script_user = <<-SCRIPT
im-config -n ibus 
dbus-launch gsettings set org.gnome.desktop.input-sources sources "[('xkb', 'us'), ('ibus', 'chewing')]"
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "debian/buster64"
  config.vm.provider "virtualbox" do |v|
    v.memory = "2048"
    v.gui = true
  end
  config.vm.provision "shell", inline: $script
  config.vm.provision "shell", inline: $script_user, privileged: false
end