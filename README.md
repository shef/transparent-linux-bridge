transparent-linux-bridge
========================

This is a patched bridge module for linux kernel linux-2.6.18-348.18.1.el5.

This module have disabled check for link-local multicast frames such as LACP
or any other multicast frames in the range 01:80:C2:00:0x.

I have used it for special test case.


br_input.c:

/* the check is disabled for LACP over bridge testing purposes

        if (unlikely(is_link_local(dest))) {
                skb->pkt_type = PACKET_HOST;
                return NF_HOOK(PF_BRIDGE, NF_BR_LOCAL_IN, skb, skb->dev,
                               NULL, br_handle_local_finish) != 0;
        }
*/
