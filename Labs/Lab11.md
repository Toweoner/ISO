# Lab11 - Unidad 1

### Se realizará lo siguiente:



	ps | where {$_.Id -eq <PID>} | select HasExited,ExitCode 

	$process=[System.Diagnostics.Process]::GetProcessById(<PID>)
	$threads=$process.Threads
	$threads | select Id,ThreadState,WaitReason

	
	PS C:\> Get-Process | more
	
	Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
	-------  ------    -----      ----- -----   ------     -- -----------
	    117       9     4488       8920    75     0,87   4488 360webshield
	    174       5     1304       3284    49            1312 atieclxx
	     99       4      804       2476    26             844 atiesrxx
	    118       5    15004      13936    44            4584 audiodg
	     77       6    39484      40956   131     1,78   4720 AwesomiumProcess
	    145       4     5704       7232   431     0,53   4792 bash
	    400      14    25420      13312   173            1688 BCMWLTRY
	     86      10     6944      12348    72     0,28   2384 calc
	    366      19    72144      90796   512   148,48   1984 chrome
	    117       5     1788       5044    62     0,03   3124 chrome
	   1459      35    85544     112856   557   228,09   3160 chrome
	     66       4     1760       4436    52     0,05   3184 chrome
	    264      13    78040      67320   314   108,39   3716 chrome
	    180      11    38024      28260   214     2,81   4212 chrome
	    286      15    51724      49708   426    25,51   4572 chrome
