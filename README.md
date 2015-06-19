# PrintQmigrator

General Description
 Some years ago, at the old Windows NT4 time, Microsoft provided ChangePrint.exe in the Windows NT4 resource kit. This tool could be used in the login script and was based on a text file which contained all "Old/New print queues definitions".

However, ChangePrint does not run anymore on Windows XP. And the resource kit provide no solution to this problem. The official answer of Microsoft is: Windows XP support VB scripting, you only need to write some code.

That’s exactly what I done, trying to translatethe ChangePrint in VBScript. I tested my script when I migrated a big print server, and my tool does perfectly the job! I called it PrintQmigrator.

Usage
 You can call PrintQmigrator from a login script (in \\DC\Netlogon or in a standard GPO). You can also put the text file containing all Old/New print queues definitions in the same location or on a file share. You can also have many text files as you want!

Synthax information
PrintQmigrator.vbs <TextFileFullPath.txt>

Exemple:

PrintQmigrator.vbs \\FileServer\Share\Printers.txt

Or you can simply double click on the file PrintQmigrator.vbe and it will ask you for a text file where the print queues are defined.

Here is the structure of the text file, where you have to enter the data about your migration:

The PrintQmigrator text file is a basic CSV file, where the separator MUST be a semi-colon (;).

Below, you will find a good sample of a text file, that shows you can migrate the print queue on another server keeping the print queues' names or not. You can also keep the server but just rename the queues:

\\OldServer\OldPrintQueue;\\NewServer\NewPrintQueue
\\OldServer\OldPrintQueue1;\\OldServer\NewPrintQueue1
\\OldServer2\OldPrintQueue2;\\NewServer2\NewPrintqueue2

PrintQmigrator will only read the lines beginning with \\. So you can easily comment the file!

If you only need to disconnect a print queue and NOT to replace with another, just let the "new print queue" empty, i.e :

\\oldserver\oldprintqueu;

