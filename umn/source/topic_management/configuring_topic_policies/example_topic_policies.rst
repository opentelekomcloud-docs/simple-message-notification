:original_name: smn_ug_44003.html

.. _smn_ug_44003:

Example Topic Policies
======================

Example 1
---------

.. code-block::

   {
       "Version": "2016-09-07",
       "Id": "__default_policy_ID",
       "Statement": [
           {
               "Sid": "__user_pub_0",
               "Effect": "Allow",
               "Principal": {
                   "CSP": [
                       "urn:csp:iam::123456789:root",
                       "urn:csp:iam::987654321:root"
                   ]
               },
               "Action": [
                   "SMN:Publish",
                   "SMN:QueryTopicDetail"
               ],
               "Resource": "urn:smn:region:cffe4fc4c9a54219b60dbaf7b586e132:Mytopic",
               "Condition": {
                   "DateLessThan":{
                        "csp:CurrentTime":"2017-11-07T15:35:00Z"
                   }
               }
           }
       ]
   }

The example is explained as follows:

The policy whose ID is **\__default_policy_ID** contains one statement. The statement ID is **\__user_pub_0**. The statement allows users whose domain IDs are **123456789** and **987654321** to query details of and publish messages to the topic whose URN is **urn:smn:region:cffe4fc4c9a54219b60dbaf7b586e132:Mytopic**. This topic policy is valid until **2017-11-07T15:35:00Z**.

Example 2
---------

.. code-block::

   {
       "Version": "2016-09-07",
       "Id": "__default_policy_ID",
       "Statement": [
           {
               "Sid": "__user_pub_0",
               "Effect": "Allow",
               "Principal": {
                   "CSP": [
                       "urn:csp:iam::123456789:root",
                       "urn:csp:iam::987654321:root"
                   ]
               },
               "Action": [
                   "SMN:Subscribe"
               ],
               "Resource": "urn:smn:region:6558ed0a1485466897e962f38fdfdb88:helloworld",
               "Condition": {
                   "DateLessThan":{
                        "csp:CurrentTime":"2017-11-07T15:35:00Z"
                   }
                   "StringLike": {
                        "smn:Endpoint":["*@gmail.com","*@hotmail.com"]
                   }
               }
           }
       ]
   }

The example is explained as follows:

The policy whose ID is **\__default_policy_ID** contains one statement. The statement ID is **\__user_pub_0**. The statement allows users whose domain IDs are **123456789** and **987654321** to subscribe Gmail and Hotmail email addresses to the topic whose URN is **urn:smn:region:6558ed0a1485466897e962f38fdfdb88:helloworld**. This topic policy is valid until **2017-11-07T15:35:00Z**.

Example 3
---------

.. code-block::

   {
       "Version": "2016-09-07",
       "Id": "__default_policy_ID",
       "Statement": [
           {
               "Sid": "__user_pub_0",
               "Effect": "Allow",
               "Principal": {
                   "CSP": [
                       "urn:csp:iam::123456789:root",
                       "urn:csp:iam::987654321:root"
                   ]
               },
               "Action": [
                   "SMN:Publish",
                   "SMN:QueryTopicDetail"
               ],
               "Resource": "urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic"
           },
           {
               "Sid": "__user_pub_1",
               "Effect": "Deny",
               "Principal": {
                   "CSP": [
                       "urn:csp:iam::987654321:root"
                   ]
               },
               "Action": [
                   "SMN:Publish",
                   "SMN:QueryTopicDetail"
               ],
               "Resource": "urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic"
           },
           {
               "Sid": "__service_pub_0",
               "Effect": "Allow",
               "Principal": {
                   "Service": [
                       "obs"
                   ]
               },
               "Action": [
                   "SMN:Publish",
                   "SMN:QueryTopicDetail"
               ],
               "Resource": "urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic"
           }
       ]
   }

The example is explained as follows:

The policy whose ID is **\__default_policy_ID** contains three statements whose IDs are **\__user_pub_0**, **\__user_pub_1**, and **\__service_pub_0**.

-  Statement **\__user_pub_0** allows users whose domain IDs are **123456789** and **987654321** to query details of and publish messages to the topic whose URN is **urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic**.
-  Statement **\__user_pub_1** does not allow the user whose domain ID is **987654321** to query details of and publish messages to the topic whose URN is **urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic**.
-  Statement **\__service_pub_0** allows the OBS service to query details of and publish messages to the topic whose URN is **urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic**.

The three statements altogether determine the effect of the topic policy. The evaluation process is as follows:

-  If the user whose domain ID is **987654321** tries to publish a message to topic **urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic**, statement **\__user_pub_0** allows the operation request, but statement **\__user_pub_1** denies it. Therefore, the request is denied.
-  If the user whose domain ID is **888888888** tries to publish a message to topic **urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic**, no statement denies the request, but there is also no statement that explicitly allows it. Therefore, the request is denied.
-  If the user whose domain ID is **123456789** tries to publish a message to topic **urn:smn:regionId:e23bf08ebb924730b452426c60849564:ECM_BKS_Topic**, statement **\__user_pub_0** allows the operation request, and no statement denies it. Therefore, the request is allowed.
