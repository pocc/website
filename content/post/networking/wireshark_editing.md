---
title: "Wireshark Editing"
date: 2019-03-12T12:44:45Z
author: Ross Jacobs
desc: "Remember to use a spellchecker when you edit your pcaps"
tags:
  - networking
  - wireshark
image: https://allabouttesting.org/wp-content/uploads/2018/06/tshark-count.jpg

draft: true
---

_Remember to use a spellchecker when you edit your pcaps_

## <a name="editcap"></a>filtering packets

Editcap allows you to remove packets by several parameters
* `-r` 
* `-A <start time>`
* `-B <stop time>`
* [packet#-packet#] [packet#]
### Using tshark to filter by capture/display filter

In order to create a oneliner and pass the filtered file to editcap, you can
create a temporary file:

```bash
tempfile=$(mktemp)
tshark -r dhcp.pcap -Y "dhcp.type == 1" -w $tempfile 
editcap $tempfile dhcp2.pcap -a 1:"Cool story bro!"
```

This isn't as elegant as reading from stdin, but editcap does not currently have
this capability

tshark can be used to reduce packet size 

## <a name=reordercap></a>reordercap
Sometimes packets are out of order. Reordercap fixes that.

### Truncate packet size

### Change packet comment
Use -a

### Change number of commets

## <a name=mergecap></a>mergecap
Merge two or more packet captures together

## <a name=text2pcap></a>text2pcap
Convert a hexstring into a packet capture
