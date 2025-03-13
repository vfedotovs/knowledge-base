

How to join multiple lines in the single line 
=============================================
 cat  localcli_storage-core-device-list.txt | grep -E "  Display Name|^   Size|Model|Vendor" | sed -e 'N;N;N;s/\n//g'| grep -vi nvme
   Display Name: SYNOLOGY iSCSI Disk (naa.60014051b5c0ed0da77dd49b0d856ed4)   Size: 307200   Vendor: SYNOLOGY   Model: Storage
   Display Name: LIO-ORG iSCSI Disk (naa.60014055f8b2795a91c490c97bcac81b)   Size: 102400   Vendor: LIO-ORG    Model: disk02
   Display Name: LIO-ORG iSCSI Disk (naa.60014057a7407bf702f4f9e9d92a9ede)   Size: 102400   Vendor: LIO-ORG    Model: disk01


SED OR exmaple 
================
 cat  prettyPrint.sh_hostlist.txt | grep -E "hostId|hostName" 
      <hostId>host-14</hostId>
      <hostName>192.168.1.50</hostName>
      <hostId>host-12</hostId>
      <hostName>192.168.1.49</hostName>


 cat  prettyPrint.sh_hostlist.txt | grep -E "hostId|hostName" | sed -E 's/<\/?(hostId|hostName)>//g'
      host-14
      192.168.1.50
      host-12
      192.168.1.49

Incorrect Character Set Usage ([...])

[hostId\|hostName\] treats h, o, s, t, I, d, |, h, o, s, t, N, a, m, e as individual characters instead of whole words.
Incorrect Escape Sequences for | in macOS sed

The | (pipe) needs proper grouping with \( and \), but macOS sed does not support \| inside \(\) like GNU sed does.
Corrected sed Command for macOS (BSD sed)

Explanation:

-E enables extended regular expressions (needed for | to work in macOS sed).
<\/? matches both opening <tag> and closing </tag>.
(hostId|hostName) matches either hostId or hostName.
> ensures only the complete tags are removed.


SED OR exxample that matches word instead of characters in []
==========================
 cat  prettyPrint.sh_hostlist.txt | grep -E "hostId|hostName" | sed -E 's/(hostId|hostName|>|<)//g'
      host-14/
      192.168.1.50/
      host-12/
      192.168.1.49/


Most polular boudaries
=======================
() boundaries 
(^...) line start
(...$) line end 
[A-Z]  characters
[0-9]  digits
\b only word
\B only match word inside  larger word



Example: Reordering Three Columns
==================================
Input (data.txt):

John Doe 25
Alice Smith 30
Bob Brown 40

Swap First and Last Name:
sed -E 's/^([^ ]+) ([^ ]+) ([0-9]+)$/\2, \1 - Age: \3/' data.txt

Output:
Doe, John - Age: 25
Smith, Alice - Age: 30
Brown, Bob - Age: 40


In sed, certain characters have special meanings and should be escaped with a backslash (\) to be interpreted literally. 
===============

Here's a list of commonly used characters that require escaping:

Period (.): Matches any single character. To match a literal period, use \..

Asterisk (*): Denotes zero or more occurrences of the preceding element. To represent a literal asterisk, use \*.

Caret (^): Indicates the start of a line. To match a literal caret, use \^.

Dollar Sign ($): Signifies the end of a line. For a literal dollar sign, use \$.

Square Brackets ([ and ]): Define a character class. To match literal square brackets, escape them as \[ \].

Backslash (\): Serves as an escape character. To match a literal backslash, use \\.

Ampersand (&): In the replacement part of the s (substitute) command, & refers to the entire matched portion. To include a literal ampersand in the replacement text, escape it as \&.

Forward Slash (/): Commonly used as a delimiter in sed commands. To use a literal forward slash within the pattern or replacement, escape it as \/. Alternatively, you can choose a different delimiter to avoid escaping.

Parentheses (( and )): Used for grouping in extended regular expressions. To match literal parentheses, escape them as \( and \).

Plus (+) and Question Mark (?): In some versions of sed, these characters have special meanings in extended regular expressions and may need to be escaped to be treated literally.

It's important to note that the necessity of escaping certain characters can vary depending on the sed implementation and the regular expression mode (basic vs. extended) being used. For instance, in POSIX basic regular expressions, characters like |, +, and ? do not have special meanings unless escaped, whereas in extended regular expressions, they do.

