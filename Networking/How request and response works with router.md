***

## Establish an connection with router:  

*First we connect to an router.Which assigns us an private ip.*

## Use Case:

*Think of I want to send an message hello server on test.com.So when we send and request to server on test.com firstly that request is sent to our router which takes our private ip and the replaces it with its public ip and port and stores the data in the `NAT Table` ,and then router sents request to test.com.

*After this test.com sends response to the IP from which the request came which was our router public IP.Then routers uses NAT and Nat uses NAT table which finds for which device this response was and then sends response to that private ip.

## But what in case a person sent and response to our IP??

*First of all NAT will check did there was info related to this response which was coming is in the NAT table if it is so router will send response to the IP for which it was stored in the NAT table but if there is nothing related to that response in the NAT table so it will deny and block that request.*
`Router can only allow incoming traffic when there is an existing request OR a configured rule.`



