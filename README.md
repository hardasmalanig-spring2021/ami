# Amazon Machine Images(AMI)

An Amazon Machine Image (AMI) provides the information required to launch an instance
This application will help launch Amazon EC2 instance by building AMI using using AWS CLI and Hashicorp Packer 


## Prerequistes 
- [Amazon CLI](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)
- [Set up AWS Profile](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-profiles.htm)
- [Install Hashicorp Packer](https://learn.hashicorp.com/tutorials/packer/getting-started-install)


## Linux setup to install Packer

    1. install packer using following steps on fedora
       - sudo dnf install -y dnf-plugins-core
       - sudo dnf config-manager --add-repo https://rpm.releases.hashicorp.com/fedora/hashicorp.repo
       - sudo dnf -y install packer

    2. verify installation
       - Hasicorp packer

## Build AMI

    1. create a packer template file like "ami.json" in the current repository .

    2. "ami.json" takes aws_acces_key_id and aws_secret_key , aws region, aws account id from the github secrets as environment variables

    3. Run the following commands to validate and build the image
        - packer validate ami.json
        - packer build ami.json

    If the above steps results in success then an aws machine image will be created in aws account for which you have provided the access to this packer script

    The packer Image built with the above script "ami.json" will have nodejs already installed