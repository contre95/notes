# Cloud "Oneliners"

A bunch of cloud oneliners I usually find my self needing.

## Amazon Web Services (AWS)

### AWS Export variables

Oneliner to export variables inside a container or somewhere you need to test any sdk and you don't have de awscli installed

```bash
env | grep AWS | awk '{print "export " $1}'
```

### Check how many GB you have on EC2 Snapshots

This one is not mine actually, I stole it from a guy at work.

```bash
aws ec2 describe-snapshots --query 'Snapshots[].VolumeSize' --output text |
	tr [:space:] '\n' |
	awk '{sum += $1} END {print sum, "GB"}'
```

### Create SSM activations with Tags

```bash
aws ssm create-activation \
  --default-instance-name "managed-instance-name" \
  --registration-limit 1 \
  --tags '[{"Key":"KEYNAME","Value": "Value"}]' \
  --iam-role service-role/AmazonEC2RunCommandRoleForManagedInstances
```

### AWS Delete all SSM activations

There's no current way to select a bunch of activation and swipe them all at once (You must have `jq` installed)

```bash
aws ssm describe-activations | \
  jq '.ActivationList | map(.ActivationId) | .[]' | \
  awk '{print "aws ssm delete-activation --activation-id " $1}'
```

### AWS Whoami

```bash
aws sts get-caller-identity
```

### AWS Assume Role from CLI

```bash
aws sts assume-role \
  --role-arn arn:aws:iam::123456789:role/TestAssumeRole \
  --role-session-name pirulo-session
```

### AWS Assume Role from CLI and set credentials

Run the following command's output to sh.

```bash
aws sts assume-role --role-arn "<ROLE_ARN>" --role-session-name PiruloeSssion > \
  keys.json.tmp && \
  cat keys.json.tmp | \
  jq '.Credentials.SecretAccessKey' | \
  awk '{print "export AWS_SECRET_ACCESS_KEY=" $1}' && \
  cat keys.json.tmp | jq '.Credentials.AccessKeyId' | \
  awk '{print "export AWS_ACCESS_KEY_ID=" $1}' && \
  cat keys.json.tmp | \
  jq '.Credentials.SessionToken' | \
  awk '{print "export AWS_SESSION_TOKEN=" $1}' ; \
  echo "export AWS_SECURITY_TOKEN=" ; \
  rm -f keys.json.tmp
```

--- 
## Google Cloud Platform (GCP)

### Gcloud Whoami

```bash
gcloud config list account --format "value(core.account)"
```

### Gcloud parse output with `jq`

```bash
gcloud compute instances list --project=project-name --format=json --filter="creationTimestamp>2020-09-03" | \
  jq '.[] | ."instance_id" = .id | {zone,instance_id,account_id:"project-name",cloud_provider:"GCP"}'
```

--- 
## Azure

### Azure VM get ID (Inside the VM)

``` bash
curl -H Metadata:true "http://169.254.169.254/metadata/instance/compute/vmId?api-version=2017-08-01&format=text"
```
