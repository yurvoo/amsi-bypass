we get the exact address of the jump instruction by searching for the first byte of each instruction this technique is effective even in the face of updates or modifications to the target data set.

for example :

| 48:85D2 | test rdx, rdx |

| 74 3F | je amsi.7FFAE957C694 |

| 48 : 85C9 | test rcx, rcx |

| 74 3A | je amsi.7FFAE957C694 |

| 48 : 8379 08 00 | cmp qword ptr ds : [rcx + 8] , 0 |

| 74 33 | je amsi.7FFAE957C694 |

the search pattern will be like this : { 0x48,'?','?', 0x74,'?',0x48,'?' ,'?' ,0x74,'?' ,0x48,'?' ,'?' ,'?' ,'?',0x74,0x33}
![image](https://github.com/user-attachments/assets/edd4cb1e-18dd-4c9f-aab4-d0829791c182)
PATCH
![image](https://github.com/user-attachments/assets/c98d70f7-14e9-4e57-88c2-9419e290b083)
