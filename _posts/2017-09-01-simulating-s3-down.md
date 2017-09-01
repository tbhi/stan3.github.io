---
layout: post
---
We can simulate AWS S3 being down by using iptables to drop traffic to the
addresses it is hosted on, at least from an EC2 VPC host.

    aws ec2 describe-prefix-lists

shows

    {
      "PrefixLists": [
        {
          "PrefixListName": "com.amazonaws.us-east-1.s3",
          "Cidrs": [
            "54.231.0.0/17"
          ],
          "PrefixListId": "pl-63a5400a"
        }
      ]
    }    

where we can pick out the network range and feed it to iptables

    iptables -A OUTPUT -d 54.231.0.0/17 -j DROP
