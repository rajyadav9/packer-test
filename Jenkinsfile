node{
  stage('exec the pipeline'){
sh """
ls -l
echo "test"
git clone https://github.com/rajyadav9/packer-test.git
if $image_type==vmware
then
  ls -lrt
  echo "I did ls"
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
bucket=$bucket-name
bucket= phg ${bucket} Vbox.zip
aws s3 cp /var/lib/jenkins/workspace/packer-test/$bucket s3://artifacts-vmware-phg/phg/$bucket/
aws s3 ls """
  }
}
