
To get IAM info
```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Allow",
        "Action": [
            "iam:Get*",
            "iam:List*",
            "iam:Generate*"
        ],
        "Resource": "*"
    }
}
```
EC2 with policy
```
{
   "Version": "2012-10-17",
   "Statement": [
    {
        "Effect": "Allow",
        "Action": [
                    "ec2:AuthorizeSecurityGroupEgress",
                    "ec2:AuthorizeSecurityGroupIngress",
                    "ec2:AttachVolume",
                    "ec2:CancelSpotInstanceRequests",
                    "ec2:CreateSecurityGroup",
                    "ec2:CreateTags",
                    "ec2:CreateVolume",
                    "ec2:DeleteSecurityGroup",
                    "ec2:DeleteTags",
                    "ec2:DeleteVolume",
                    "ec2:Describe*",
                    "ec2:DescribeVolumes",
                    "ec2:DetachVolume",
                    "ec2:ImportKeyPair",
                    "ec2:DescribeKeyPairs",
                    "ec2:ModifyInstanceAttribute",
                    "ec2:RequestSpotInstances",
                    "ec2:RevokeSecurityGroupIngress",
                    "ec2:RunInstances",
                    "ec2:StartInstances",
                    "ec2:StopInstances",
                    "ec2:TerminateInstances",
                    "ec2:RequestSpotFleet",
                    "ec2:DescribeSpotFleetInstances",
                    "ec2:DescribeSpotFleetRequests",
                    "ec2:DescribeSpotFleetRequestHistory",
                    "ec2:CancelSpotFleetRequests",
                    "iam:PassRole",
                    "iam:ListRoles",
                    "iam:GetRole",
                    "iam:ListInstanceProfiles",
                    "iam:SimulatePrincipalPolicy"
                    ],
        "Resource": ["*"]
    }
```
  
WithMultiple Conditions
  ```
  {
"Version": "2012-10-17",
"Statement": [
 {
     "Sid": "NonResourceBasedPermissions",
     "Effect": "Allow",
     "Action": [
             "ec2:AssociateAddress",
             "ec2:DisassociateAddress",
             "ec2:ImportKeyPair",
             "ec2:RequestSpotInstances",
             "ec2:RequestSpotFleet",
             "ec2:ModifySpotFleetRequest",
             "ec2:CancelSpotFleetRequests",
             "ec2:CancelSpotInstanceRequests",
             "ec2:CreateSpotDatafeedSubscription",
             "ec2:DeleteSpotDatafeedSubscription",
             "ec2:Describe*",
             "ec2:CreateKeyPair",
             "ec2:CreateSecurityGroup",
             "ec2:CreateTags",
             "ec2:CreateFleet",
             "ec2:DeleteLaunchTemplate",
             "ec2:DeleteLaunchTemplateVersions",
             "ec2:CreateLaunchTemplateVersion",
             "ec2:CreateLaunchTemplate",
             "ec2:DescribeLaunchTemplates",
             "ec2:DescribeLaunchTemplateVersions",
             "sts:DecodeAuthorizationMessage",
             "iam:SimulatePrincipalPolicy"
             ],
     "Resource": ["*"]
     },
 {
     "Sid": "AllowInstanceActions",
     "Effect": "Allow",
     "Action": [
            "ec2:StartInstances",
            "ec2:StopInstances",
            "ec2:ModifyInstanceAttribute",
            "ec2:TerminateInstances",
            "ec2:AttachVolume",
            "ec2:DetachVolume",
            "ec2:CreateTags",
            "ec2:DeleteTags"
            ],
     "Resource": "arn:aws:ec2:<AWS Region>:<AWS Account ID>:instance/*",
     "Condition": {
         "StringLike": {
                "ec2:InstanceProfile": "arn:aws:iam::<AWS Account ID>:instance-profile/<AWS Role Name>"
                }
         }
     }
    ```
    
    Create IAM user with specific tags
```    
    {
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "TagUsersWithOnlyTheseTags",
            "Effect": "Allow",
            "Action": [
                "iam:CreateUser",
                "iam:TagUser",
                "iam:ListUsers"
            ],
            "Resource": "*",
            "Condition": {
                "StringEqualsIfExists": {
                    "aws:RequestTag/Department": [
                        "Development",
                        "QualityAssurance"
                    ],
                    "aws:RequestTag/JobFunction": "Employee"
                },
                "ForAllValues:StringEquals": {
                    "aws:TagKeys": [
                        "Department",
                        "JobFunction"
                    ]
                }
            }
        }
    ]
}
```
