# Python-SIP
Primative library to facilitate automated calls and messaging.

## How to use the library.

First you need to start a session by supplying basic SIP account details  
sip_session = sip.SIPSession(local_ip, username, domain, password)

Then you define some event handlers  
sip_session.call_accepted += self.call_accepted  
sip_session.call_rejected += self.call_rejected  
sip_session.call_ended += self.call_ended  
sip_session.call_error += self.call_error  
sip_session.message_sent += self.message_sent

The event handler will return information about the session as well as the SIP message for you to exact data from  
def call_accepted(self, session, data):

make a call, you will need to supply your own SDP data  
call_id = sip_session.send_sip_invite(to_address, call_sdp)

You can also send messages  
call_id = sip_session.send_sip_message(to_address, message_body)

Please note that after the call is accepted you will need to write your own code to handle the RTP stream
