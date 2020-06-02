**To install Anchore CLI command:**
```
sudo yum install -y https://dl.fedoraproject.org/pub/epel/epel-release-latest-7.noarch.rpm
sudo yum-config-manager --enable epel
sudo yum install -y epel-release
sudo yum install -y python-pip
pip install --user --upgrade anchorecli
```

**In order to work anchore-cli command, update .bashrc and .bash_profile with below contents:
```
PATH=$PATH:/root/.local/bin/
export PATH
export ANCHORE_CLI_URL=http://localhost:8228/v1
export ANCHORE_CLI_USER=admin
export ANCHORE_CLI_PASS=foobar
export ANCHORE_CLI_SSL_VERIFY=n
anchore-cli --version
```

**How to vulnerability data to get synced into the engine:**
```
anchore-cli system feeds list
```

**Add and List registries added to anchore engine:**
```
anchore-cli registry add <ecr_registry_name> <access_key> <secret_access_key> --registry-type=awsecr
anchore-cli registry list
```

**Download policy bundle as JSON:**
```
anchore-cli policy get 2c53a13c-1765-11e8-82ef-23527761d060 --detail > policybundle.json
```
**How to add policy and activate:**
```
anchore-cli policy add policybundle.json
anchore-cli policy list
anchore-cli policy activate 2c53a13c-1765-11e8-82ef-23527761d060
```

**Evaluate image vulnerability with and without specific policy:**
```
anchore-cli evaluate check localbuild/continuumio/miniconda3:4.7.12:latest --detail
anchore-cli evaluate check  docker.io/continuumio/miniconda3:4.7.12 --policy anchore_cis_1.13.0_base --detail
```

**Inline_scan tool command:**
```
curl -s https://ci-tools.anchore.io/inline_scan-v0.6.0 | bash -s -- analyze -u admin -p foobar -r http://localhost:8228/v1 -g <image_name>
```
