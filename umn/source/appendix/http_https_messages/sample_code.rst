:original_name: smn_ug_a9004.html

.. _smn_ug_a9004:

Sample Code
===========

Java
----

Verify **signing_cert_url**, **signature** that obtained in :ref:`HTTP or HTTPS Message Format <smn_ug_a9002>`, and **message** (contained in the message signature) to check the message validity, as shown in the following:

.. code-block::

   private static void isMessageValid(String signing_cert_url,
               String signature, Map<String, String> message) {
           InputStream in = null;
           try {
               URL url = new URL(signing_cert_url);
               in = url.openStream();
               CertificateFactory cf = CertificateFactory.getInstance("X.509");
               X509Certificate cert = (X509Certificate) cf.generateCertificate(in);
               Signature sig = Signature.getInstance(cert.getSigAlgName());
               sig.initVerify(cert.getPublicKey());
               sig.update(buildSignMessage(message).getBytes("UTF-8"));
               byte[] sigByte = Base64.getDecoder().decode(signature);
               if (sig.verify(sigByte)) {
                   System.out.println("Verify success");
               } else {
                   System.out.println("Verify failed");
               }
           } catch (Exception e) {
               throw new SecurityException("Verify method failed.", e);
           } finally {
               if (in != null) {
                   try {
                       in.close();
                   } catch (IOException e) {
                       e.printStackTrace();
                   }
               }
           }
       }

.. note::

   If your Java version is earlier than 8, use the third-party package **commons-codec.jar** to perform Base64 decoding, and replace **byte[] sigByte = Base64.getDecoder().decode(signature);** with **byte[] sigByte = Base64.decodeBase64(signature);** in the preceding code.

The following is an example of the code to create the message verification signature:

.. code-block::

   private static String buildSignMessage(Map<String,String> msg) {
       String type = msg.get("type");
       String message = null;
       if ("Notification".equals(type)){
           message = buildNotificationMessage(msg);
       } else if ("SubscriptionConfirmation".equals(type) ||
       "UnsubscribeConfirmation".equals(type)){
           message = buildSubscriptionMessage(msg);
       }
       return message;
   }

   private static String buildSubscriptionMessage(Map<String, String> msg) {
       String stringMessage = "message\n";
       stringMessage += msg.get("message") + "\n";
       stringMessage += "message_id\n";
       stringMessage += msg.get("message_id") + "\n";
       stringMessage += "subscribe_url\n";
       stringMessage += msg.get("subscribe_url") + "\n";
       stringMessage += "timestamp\n";
       stringMessage += msg.get("timestamp") + "\n";
       stringMessage += "topic_urn\n";
       stringMessage += msg.get("topic_urn") + "\n";
       stringMessage += "type\n";
       stringMessage += msg.get("type") + "\n";
       return stringMessage;
   }

   private static String buildNotificationMessage(Map<String, String> msg)
       {
           String stringMessage = "message\n";
           stringMessage += msg.get("message").toString() + "\n";
           stringMessage += "message_id\n";
           stringMessage += msg.get("message_id").toString() + "\n";
           if (msg.get("subject") != null){
                stringMessage += "subject\n";
                stringMessage += msg.get("subject").toString() + "\n";
           }
           stringMessage += "timestamp\n";
           stringMessage += msg.get("timestamp").toString() + "\n";
           stringMessage += "topic_urn\n";
           stringMessage += msg.get("topic_urn").toString() + "\n";
           stringMessage += "type\n";
           stringMessage += msg.get("type").toString() + "\n";
           return stringMessage;
       }

Node.js
-------

::

   const fs = require('fs');
   const crypto = require('crypto');
   const jsrsag = require('jsrsasign');

   /**
   * Message signature verification
   * @param pemFile: path for storing the signature file (path for storing the certificate downloaded to your local computer)
   * @param signature: signature to be verified
   * @param message: content of the message to be verified
   * @returns {boolean} true: The signature passes the verification. false: The signature fails the verification.
    */
   function verifyMessage(pemFile, signature, message) {
       const pubPem = fs.readFileSync(pemFile);
       const verify = crypto.createVerify(signatureAlgorithm(pubPem));
       verify.update(buildSignMessage(message));
       const verifyResult = verify.verify(pubPem, signature, 'base64');
       if (verifyResult) {
           console.log("verify success");
           return true;
       } else {
           console.log('verify failed, result: ' + verifyResult);
           return false;
       }
   }

   /**
   * Obtain the signature algorithm from the certificate.
    */
   function signatureAlgorithm(pubPem) {
       const certObject = new jsrsag.X509();
       certObject.readCertPEM(pubPem.toString());
       let algorithm = certObject.getSignatureAlgorithmField();
       if (algorithm.split('with').length > 1) {
           algorithm = algorithm.split('with')[1] + '-' + algorithm.split('with')[0];
       }
       return algorithm;
   }

   function buildSignMessage(msg) {
       const type = msg.type;
       let message = '';
       if (type === 'Notification') {
           message = buildNotificationMessage(msg);
       } else if (type === 'SubscriptionConfirmation') {
           message = buildSubscriptionMessage(msg);
       }
       return message;
   }

   function buildNotificationMessage(msg) {
       let signMessage = 'message\n' + msg.message + '\n';
       signMessage += 'message_id\n' + msg.message_id + '\n';
       if (msg.subject) {
           signMessage += 'subject\n' + msg.subject + '\n';
       }
       signMessage += 'timestamp\n' + msg.timestamp + '\n';
       signMessage += 'topic_urn\n' + msg.topic_urn + '\n';
       signMessage += 'type\n' + msg.type + '\n';
       return signMessage;
   }

   function buildSubscriptionMessage(msg) {
       let signMessage = 'message\n' + msg.message + '\n';
       signMessage += 'message_id\n' + msg.message_id + '\n';
       signMessage += 'subscribe_url\n' + msg.subscribe_url + '\n';
       signMessage += 'timestamp\n' + msg.timestamp + '\n';
       signMessage += 'topic_urn\n' + msg.topic_urn + '\n';
       signMessage += 'type\n' + msg.type + '\n';
       return signMessage;
   }

.. note::

   The sample code has passed the test on Nodejs v14.17.5.

Go
--

.. code-block::

   package demo

   import (
       "bytes"
       "crypto"
       "crypto/rsa"
       "crypto/x509"
       "encoding/base64"
       "encoding/json"
       "encoding/pem"
       "fmt"
       "io/ioutil"
   )

   type Message struct {
       Signature        string  `json:"signature"`
       Subject          *string `json:"subject"`
       TopicUrn         string  `json:"topic_urn"`
       MessageId        string  `json:"message_id"`
       SignatureVersion string  `json:"signature_version"`
       Type             string  `json:"type"`
       Message          string  `json:"message"`
       SubscribeUrl     string  `json:"subscribe_url"`
       UnsubscribeUrl   string  `json:"unsubscribe_url"`
       SigningCertUrl   string  `json:"signing_cert_url"`
       Timestamp        string  `json:"timestamp"`
   }

   func VerifyMessage(pemFile string, message string) bool {
       msg := Message{}
       err := json.Unmarshal([]byte(message), &msg)
       if err != nil {
           fmt.Println("Convert json to struct failed")
           return false
       }
       pemContent, err := ioutil.ReadFile(pemFile)
       if err != nil {
           fmt.Println("Read pem file failed")
           return false
       }
       certDerblock, _ := pem.Decode(pemContent)
       if certDerblock == nil {
           fmt.Println("Decode pem file failed")
           return false
       }
       cert, err := x509.ParseCertificate(certDerblock.Bytes)
       if err != nil {
           fmt.Println("Parse cert failed")
           return false
       }

       msgString := buildMessage(&msg)
       msgHash := crypto.SHA256.New()
       msgHash.Write([]byte(msgString))
       msgHashSum := msgHash.Sum(nil)

       decodeSign, _ := base64.StdEncoding.DecodeString(msg.Signature)

       publicKey := cert.PublicKey.(*rsa.PublicKey)
       err = rsa.VerifyPKCS1v15(publicKey, crypto.SHA256, msgHashSum, decodeSign)
       if err != nil {
           fmt.Println("Verify failed")
           return false
       } else {
           fmt.Println("Verify success")
           return true
       }
   }

   func buildMessage(msg *Message) string {
       if msg.Type == "Notification" {
           return buildNotificationMessage(msg)
       } else if msg.Type == "SubscriptionConfirmation" || msg.Type == "UnsubscribeConfirmation" {
           return buildSubscriptionMessage(msg)
       }
       return ""
   }

   func buildNotificationMessage(msg *Message) string {
       buf := bytes.Buffer{}
       buf.WriteString("message\n" + msg.Message + "\n")
       buf.WriteString("message_id\n" + msg.MessageId + "\n")
          //The Subject field does not exist in msg, and this issue needs to be addressed.
       if msg.Subject != nil {
           buf.WriteString("subject\n" + *msg.Subject + "\n")
       }
       buf.WriteString("timestamp\n" + msg.Timestamp + "\n")
       buf.WriteString("topic_urn\n" + msg.TopicUrn + "\n")
       buf.WriteString("type\n" + msg.Type + "\n")
       return buf.String()
   }

   func buildSubscriptionMessage(msg *Message) string {
       buf := bytes.Buffer{}
       buf.WriteString("message\n" + msg.Message + "\n")
       buf.WriteString("message_id\n" + msg.MessageId + "\n")
       buf.WriteString("subscribe_url\n" + msg.SubscribeUrl + "\n")
       buf.WriteString("timestamp\n" + msg.Timestamp + "\n")
       buf.WriteString("topic_urn\n" + msg.TopicUrn + "\n")
       buf.WriteString("type\n" + msg.Type + "\n")
       return buf.String()
   }

.. note::

   The sample code has passed the test on Go 11.5
