# set up Pulumi State & state locking 

### create s3 bucket for state 
`aws s3api create-bucket --bucket pulumi-state-bucket --region us-east-1`

### create dynamodb for state locking 
`aws dynamodb create-table \
  --table-name PulumiStateLocking \
  --attribute-definitions AttributeName=LockID,AttributeType=S \
  --key-schema AttributeName=LockID,KeyType=HASH \
  --provisioned-throughput ReadCapacityUnits=5,WriteCapacityUnits=5`



# Configure pulumi to use s3 backend 


`pulumi new aws-typescript`

