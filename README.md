dashboardIAC vm is fully provisioned for automate deployment in the Vagrantfile in this lines
  config.vm.provision "shell", inline: <<-SHELL
    yum install httpd wget unzip vim -y
    systemctl start httpd
    systemctl enable httpd
    mkdir -p /tmp/dashboard
    cd /tmp/dashboard
    wget https://www.tooplate.com/zip-templates/2108_dashboard.zip
    unzip -o 2108_dashboard.zip
    cp -r 2108_dashboard/* /var/www/html/
    systemctl restart httpd
    cd /tmp/
    rm -rf /tmp/dashboard
  SHELL
