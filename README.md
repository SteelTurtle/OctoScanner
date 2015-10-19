# OctoScanner
A PowerShell module that implements a multi-thread, remote system scanner 
OCTOSCANNER version 2.0.2 - last code revision: 14/10/2015. Requires at least PowerShell v.3 to work.
  
  Author: Daniele Mancuso (steelturtle@msn.com)
  Using public domain code for the (excellent!) MultiThreading engine section written by Ryan Witschger @(http://www.Get-Blog.com), and
  for the CSV Exporter (Convert-OutputForCSV) by Boe Prox
  This PowerShell Module is freely distributable and available to anyone.
  ...Just spend some good words on the author if you like it!  
  
# How does it work?
The main component of the PowerShell module is the cmdlet "Start-SystemScannerMT", which can query a single computer or a list of (remote) computers for a specific subset of system information and performance counters. 
"Start-SystemScannerMT" works using multi-threading to poll multiple performance counters at the same time on the remote machine.
If launched as an argument of the "Start-MultiThreadEngine" cmdlet it can also scan more machines at the same time.
Start-SystemScannerMT also accept input from the pipeline.
Please note that, to launch the "Start-SystemScannerMT" cmdlet on any machine, you need first to be sure that the PowerShell execution policy (on the target machine(s)) has been set to "Unrestricted".
The module has been filled with comments and examples about how to use the comdlets; theoretically this should make OctoScanner easy to use, modify and improve by anybody with a decent knowledge of PowerShell.

# But wait, there is more...
Actually, with the OctoScanner Module, you can pipe the Start-SystemScannerMT and the Start-MultiThreadEngine cmdlets with several other helper functions contained in the module. You can, for example, get the list of machines to remotely scan directly from a MS SQL Server AND/OR save the result of your scan to a MS SQL database.


# A couple of words on OctoScanner limitations (and why do OctoScanner exist).
Although I have had a lot of fun in developing the OctoScanner module, I wouldn't even try to suggest you use it for mass-scanning of the Windows clients in your network. Consider this example: with a 64-bit Windows 8.1 machine equipped with 16 GBytes of RAM, due to the highly inefficient way a scripting language like PowerShell deals with multi-threading, I was able to scan about 300 remote client machines in batteries of 20 machines per scanning-session, each session collecting data for 10 minutes. During the scanning sequences, the OctoScanner module sucked the entire quantity of RAM available and the  quad-core CPU of the host machine worked at 100% of his power. 
Moral of the story is: be sure to have a (powerful) dedicated machine to run the scanner.
You know the problem: shell scripting should never be used for tasks triggering the simultaneous use of such a number of computing resources. That is a job for a proper software created and compiled with a real programming language.
Not to mention that a software of this kind should be conceived with its specific Server and Client components, right? :)
Right.

Well, unless some of your project managers have already sold to a customer a scanning solution for remote Windows clients that does not require them to buy a SCOM (System Center Operation Manager) server, because some smartass has guaranteed his/her bosses that "you can do wonders with PowerShell, oh yes"!!
So somebody walks to your desk and asks you if somehow you can repair in 7 days the damages caused by this collective madness; the rest of the story is what you can find here... 
That was a word of advice on the context in which OctoScanner was born; now take the PSM and decide what to do with it! 

The author.
