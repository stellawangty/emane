# emane
AWS with EMANE

Reference: https://github.com/adjacentlink/emane/wiki

## Vagrant(local)
Reference: https://emane-docker.readthedocs.io/en/latest/introduction.html
![pic0](pic/image.png)
![pic1](pic/image-1.png)

~~~
nodes:
  companyA:
    - name: '11'
      is_border: True
      neighbors: ['12', '13', '21', '22']
    - name: '12'
      is_border: True
      neighbors: ['11', '13', '22']
    - name: '13'
      is_border: False
      neighbors: ['11', '12']
  companyB:
    - name: '21'
      is_border: True
      neighbors: ['11', '22']
    - name: '22'
      is_border: True
      neighbors: ['11', '12', '21']
~~~
![pic2](pic/image-2.png)

## AWS CLI
1. Create AK SK: open https://console.aws.amazon.com/iam/home?nc2=h_m_sc#/security_credentials
![pic3](pic/image-3.png)
2. Configure AWS CLI:
    Reference: https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2-linux.html
~~~
aws configure
~~~

![pic4](pic/image-4.png)

Reference: https://docs.aws.amazon.com/eks/latest/userguide/install-aws-iam-authenticator.html
~~~
curl -o aws-iam-authenticator https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/aws-iam-authenticator
~~~

## AWS EKS
Reference: https://docs.aws.amazon.com/eks/latest/userguide/getting-started-eksctl.html
~~~
curl -o kubectl https://amazon-eks.s3.us-west-2.amazonaws.com/1.19.6/2021-01-05/bin/linux/amd64/kubectl
curl --silent --location "https://github.com/weaveworks/eksctl/releases/latest/download/eksctl_$(uname -s)_amd64.tar.gz" | tar xz -C /tmp

eksctl create cluster \
--name emane-demo \
--region us-east-2 \
--fargate
~~~
![pic5](pic/image-5.png)
![pic6](pic/image-6.png)
Created: 
![pic7](pic/image-7.png)
![pic8](pic/image-8.png)
![pic9](pic/image-9.png)

## EMANE
![pic10](pic/image-10.png)
![pic11](pic/image-11.png)
![pic12](pic/image-12.png)
![pic13](pic/image-13.png)

## EC2
Initialization: 18.04
emane-demo.pem file:
~~~
-----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEArOwo1woi+aDelNchj2C562OR0VM38LrfSh6cYJ+9ElgDPkbU
3vcU+/mh4eH+ANB14oDHe12+MyhnSVZmaCPgiuCKPFu4vystH2kJnAeDQuRSqv+z
eLxJ/fB8PamEARDosrCzSt5oK7tgN97+XbWXffexQ/3Kj6RjIhF4U5gV0w1lLSfV
WAuDLRel6/fViG32v8U2Em80s5MTlVxBHEAkZbFRTru9qS9FYfBm72R4/xHX5IvK
KBIqu7DSrMcMzS378lgSq0bslv82IH/m4cK7D1wNmTM9nwSO+cTibfwzocEVQAO8
vhenLqg6RO+IMClWU3FaLGT5ZoG1toK3BAmIGQIDAQABAoIBADeSCSnaCxVXuk/w
tstB1V2s+N5hNPf6xekm3zA6BWPQvvIThzNECg1T0s8pdhxC4a9xnSmrHYWJNXAf
APf0l6Npt2LgQwXEVVLjyX/H9knX4C0t0To6oDioQPT79fz1tyI9oNCtmqJ7K9eo
pOvugImtwNzNwXvZ4zW+kYGjvVe+TYF7+Vtb368bMQY4BVdNxiwlv1/tUaY2TOCT
GkyQR/ZiYd2AgzJ0LpOpCsZHpM+CEaUEbSUUYr1CQiIxMoZ+5YyLgLI9xAGNUAqV
Cdw05oz3P5xvzhLKPQTRorXo77u67P+/dfytTLA9A/d8E4sjdFCvFNhZF0w7WeuV
UjdYCAUCgYEA5gnZXRf4WaAx/TAyEedI0rayL9BCiRMpmCUrqBUawehAhxSLjxVC
MKjHjBy+qvyxW90HINelthms0Q3H+SyKw1Gx9xwubSAE/0hPiylYkFEGDdBXriKq
iDReXSwA4TlHINIjwhlL1GGOmbI5PeeSBeyrmpWKESd13KmljnvNZb8CgYEAwHAl
SjoOJEZ4uRCmyTeHBUJvfp94GS/U3B85ePqSDsTu31q5Ftnyicqnz2rZf+LcKVYy
n8peuPMBbLb8lppotKdMDynvTRDI92hu7X6L/2ySEB/+NWu+cU95qJLzm5L5mXnd
0ZT3d9ygOAty5s2UrtuK1ohzttHGjKTGuOpS+CcCgYEAxRxTYG2VpFab/vM5NBYW
VFevv0CYgpQk4/WVvuS2lMjJ4fU80FHK8Z7tvaUzy5fS8YAnB4FAwRSm/Eruuxfr
nwl1kORY87CoF4aCgh/ff2mt4lBPkSqrLSKSaQu3hUVrKThm436Bd25QnmoUmnK+
sMznDgJs194UJAxJjBmRGkkCgYEAleECehxbVU95yRG6BS/1PlhvBBzp6hwB2muL
VLk7trsVHOrJC442Q7GOH5Ml0V/8f0l+Zku0mLHTYzvl4NpkQIeoSosrsUcobuFs
vBZ6rTZ/UIXKdQr0qcXviCbkC0BenHV5GTm/wCAavWvVUwO9EK83JD3kefhKftH7
YJxIgLMCgYEArPstuYqpF0VLuU5XAcoN+3tbfgMdMX/qkjovnWnpP2SIG/c0jvAz
6XC45OMEGIf0ILiPNbB+L7eIW52adtwVckBriPNvar+p85xP4nAymj4YeZ6b4iLS
jX2uQujRPF0pFmRSicqxjNJ0azfO5KIKOzW97oFOZz+sXGxx3mEcxaw=
-----END RSA PRIVATE KEY-----    
~~~

~~~
ssh -i emane-demo.pem ubuntu@18.224.62.99
~~~
Switch to root:
~~~
su root
~~~
Execute: 
~~~
apt update
apt install docker.io
pip3 install -r requirements.txt

# set up emane environment
wget https://adjacentlink.com/downloads/emane/emane-1.2.5-release-1.ubuntu-18_04.amd64.tar.gz
tar zxvf emane-1.2.5-release-1.ubuntu-18_04.amd64.tar.gz
cd emane-1.2.5-release-1/debs/ubuntu-18_04/amd64
dpkg -i *.deb
apt-get -y install -f
~~~
![pic14](pic/image-14.png)

Start EMANE:
![pic15](pic/image-15.png)

Execute emanesh:
![pic16](pic/image-16.png)

Show topology:
![pic17](pic/image-17.png)

Move to local:
~~~
scp -i emane-demo.pem ubuntu@18.224.62.99:/home/emane-docker/a.png .
~~~
![pic18](pic/image-18.png)






    
    


