neil_walrus_basictest_0
=======================

## Description

Check basic Walrus operations, such as get and put

## Procedure

1. Create a bucket
2. Add an object to the bucket
3. Retrieve the object
4. Delete the object
5. Delete the bucket
6. Create a bucket using RightAws::S3::Bucket API in a particular location
7. Add an object to the bucket
8. retrieve the object
9. delete the object
10. delete the bucket
11. Create a bucket using RightAws::S3::Bucket API in a particular location 'us'
12. Add an object to the bucket
13. Create a new object (key?)
14. Copy the second object to the first
15. [FAIL] If copy exists (but there is no check for object consistency here)
16. delete the object1
17. delete the object2
18. delete the bucket
19. Create a bucket using RightAws::S3::Bucket API in a particular location 'us'
20. Add an object to the bucket
21. Get the grantees for the object
22. Print all grantees with Id/Name/Permissions (no check here?)
23. Delete object
24. Delete bucket
25. Create a bucket using RightAws::S3::Bucket API in a particular location 'eu'
26. Add an object to the bucket
27. Rename the object
28. Check for the existence of the object under the new name
29. [FAIL] The object was not found
30. Delete object
31. Delete bucket
32. Create a bucket using RightAws::S3::Bucket API in a particular location 'us'
33. Add object to bucket
34. Create a key object
35. Move the second object to the first
36. [FAIL] Object 2 does exist Object 1 should not
37. Delete object2
38. Delete the bucket
39. Create a bucket using RightAws::S3::Bucket API in a particular location 'eu'
40. Create a key object with data=x and groups and life
41. Put the object (where?)
42. [FAIL] Object does not exists
43. Print object metadata
44. Delete object
45. Delete bucket
46. Create a bucket using RightAws::S3::Bucket API in a particular location 'eu'
47. Create a key object with data=x and groups and life
48. Put the object (where?)
49. [FAIL] Object does not exist
50. Log the meta data
51. Change the metadata
52. Log the meta data
53. Delete object
54. Delete bucket



# Eucalyptus Testunit Framework

Eucalyptus Testunit Framework is designed to run a list of test scripts written by Eucalyptus developers.



## How to Set Up Testunit Environment

On **Ubuntu** Linux Distribution,

### 1. UPDATE THE IMAGE

<code>
apt-get -y update
</code>

### 2. BE SURE THAT THE CLOCK IS IN SYNC

<code>
apt-get -y install ntp
</code>

<code>
date
</code>

### 3. INSTALL DEPENDENCIES
<note>
YOUR TESTUNIT **MIGHT NOT** NEED ALL THE PACKAGES BELOW; CHECK THE TESTUNIT DESCRIPTION.
</note>

<code>
apt-get -y install git-core bzr gcc make ruby libopenssl-ruby curl rubygems swig help2man libssl-dev python-dev libright-aws-ruby nfs-common openjdk-6-jdk zip libdigest-hmac-perl libio-pty-perl libnet-ssh-perl euca2ools
</code>

### 4. CLONE test_share DIRECTORY FOR TESTUNIT
<note>
YOUR TESTUNIT **MIGHT NOT** NEED test_share DIRECTORY. CHECK THE TESTUNIT DESCRIPTION.
</note>

<code>
git clone git://github.com/eucalyptus-qa/test_share.git
</code>

### 4.1. CREATE /home/test-server/test_share DIRECTORY AND LINK IT TO THE CLONED test_share

<code>
mkdir -p /home/test-server
</code>

<code>
ln -s ~/test_share/ /home/test-server/.
</code>

### 5. CLONE TESTUNIT OF YOUR CHOICE

<code>
git clone git://github.com/eucalyptus-qa/**testunit_of_your_choice**
</code>

### 6. CHANGE DIRECTORY

<code>
cd ./**testunit_of_your_choice**
</code>

### 7. CREATE 2b_tested.lst FILE in ./input DIRECTORY

<code>
vim ./input/2b_tested.lst
</code>

### 7.1. TEMPLATE OF 2b_tested.lst, SEPARATED BY TAB

<sample>
192.168.51.85	CENTOS	6.3	64	REPO	[CC00 UI CLC SC00 WS]

192.168.51.86	CENTOS	6.3	64	REPO	[NC00]
</sample>

### 7.2. BE SURE THAT YOUR MACHINE's id_rsa.pub KEY IS INCLUDED THE CLC's authorized_keys LIST

ON **YOUR TEST MACHINE**:

<code>
cat ~/.ssh/id_rsa.pub
</code>

ON **CLC MACHINE**:

<code>
vim ~/.ssh/authorized_keys
</code>

### 8. RUN THE TEST

<code>
./run_test.pl **testunit_of_your_choice.conf**
</code>


## How to Examine the Test Result

### 1. GO TO THE artifacts DIRECTORY

<code>
cd ./artifacts
</code>

### 2. CHECK OUT THE RESULT FILES

<code>
ls -l
</code>


## How to Rerun the Testunit

### 1. CLEAN UP THE ARTIFACTS

<code>
./cleanup_test.pl
</code>

### 2. RERUN THE TEST

<code>
./run_test.pl **testunit_of_your_choice.conf**
</code>


