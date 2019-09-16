node{
  stage(exec the pipeline){
sh ```
#export DISPLAY=localhost:0.0
#curl -qL -o packer.zip https://releases.hashicorp.com/packer/0.12.3/packer_0.12.3_linux_amd64.zip && unzip packer.zip
echo "Installing jq..."
#curl -qL -o jq https://stedolan.github.io/jq/download/linux64/jq && chmod +x ./jq
ls -l
echo "test"
if $image_type==vmware
then
  /bin/packer build -var-file=vars.json packer.json
  echo "zip output files vmware"
  sudo zip -r Predictive-Health-Gateway-0.5.1-rc.4-vmware-iso.zip /var/lib/jenkins/workspace/packer-test/Predictive-Health-Gateway-0.5.1-rc.4-vmware-iso
  sudo chmod 777 /var/lib/jenkins/workspace/packer-test
else
 /bin/packer build -var-file=vars.json vbox.json
 echo "zip output files vbox"
sudo zip -r phg-phg-0.5.1-rc.4-Vbox.zip /var/lib/jenkins/workspace/packer-test/phg-phg-0.5.1-rc.4-Vbox
fi
echo "test1"
sudo chmod 777 /var/lib/jenkins/workspace/packer-test
#withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', credentialsId: 'aws-cred']]) {
#aws s3 cp /var/lib/jenkins/workspace/packer-test/phg-phg-0.5.1-rc.4-Vbox.zip s3://artifacts-vmware-phg/vmware-image
aws s3 ls ```

}
