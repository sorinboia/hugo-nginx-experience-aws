+++
title = "Accessing the Nginx Controller"
menuTitle = "Nginx Controller Access"
date = 2020-07-08T14:37:59+03:00
weight = 10
+++

1. The Nginx Controller has already been deployed with the terraform declaration, we need to find the public IP address.

```

export controller_ip=$(tf state show "aws_instance.controller" | grep "public_ip" | grep -v "associate_public_ip_address" | cut -d'"' -f2)
curl -k -c cookie.txt -X POST --url "https://$controller_ip/api/v1/platform/login" --header 'Content-Type: application/json' --data '{"credentials": {"type": "BASIC","username": "nginx@f5.com","password": "Admin2020"}}'
export controller_apikey=$(curl -k -sb cookie.txt -c cookie.txt https://$controller_ip/api/v1/platform/global | jq .currentStatus.agentSettings.apiKey | tr -d '"')

tf state show "aws_instance.controller" | grep "public_ip" | grep -v "associate_public_ip_address" | cut -d'"' -f2
```

2. Change the directory back to the original repo folder:
```
cd ..
```

3. Browse (using `HTTPS`) to the IP address of the Controller and verify you have access:

```
Username (email): nginx@f5.com
Password: Admin2020
```