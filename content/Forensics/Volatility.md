Volatility Usage

Volatility Image Profile

>$ volatility -f <example.raw> imageinfo

Volatility Process List

>$ volatility -f <example.raw> --profile=<profile> pslist

Volatility Process Tree

>$ volatility -f <example.raw> --profile=<profile> pstree

Volatility Process Scan

>$ volatility -f <example.raw> --profile=<profile> psscan

>$ volatility -f <example.raw> --profile=<profile> psscan --output=dot --output-file=<filename.dot> (You Can Open it in Dot Viewer)

Volatility Process Dump

>$ volatility -f <example.raw> --profile=<profile> procdump -p <pid> -D <output/>

Volatility Executed Commands

>$ volatility -f <example.raw> --profile=<profile> cmdscan

Volatility Console Outputs

>$ volatility -f <example.raw> --profile=<profile> consoles

Volatility CMDline

>$ volatility -f <example.raw> --profile=<profile> cmdline

or

>$ volatility -f <example.raw> --profile=<profile> cmdline -p <pid>

Volatility enviroment variables

>$ volatility -f <example.raw> --profile=<profile> envars

Volatility NTLM Password Hashes

>$ volatility -f <example.raw> --profile=<profile> hashdump

Volatility Network Scan

>$ volatility -f <example.raw> --profile=<profile> netscan

Volatility Yara Scan

>$ volatility -f <example.raw> --profile=<profile> yarascan -Y “<yara_rule>”

Volatility DLL Listing

>$ volatility -f <example.raw> --profile=<profile> dlllist -p <pid>

Volatility DLL Dumping

>$ volatility -f <example.raw> --profile=<profile> dlldump -p <pid> -b <base_address> -D <output_directory>

Volatility Dumping Registry

>$ volatility -f <example.raw> --profile=<profile> dumpregistry -D <output_directory>

Volatility Data Extracting

>$ volatility -f <example.raw> --profile=<profile> memdump -p <pid> -D <output>

(change file extension to .data after extracting)

Volatility Psychical Offset of file

>$ volatility -f <example.raw> --profile=<profile> flescan | <filename>

Volatility Handles Listing

>$ volatility -f <example.raw> --profile=<profile> handles -p <pid> -t <type (mutant, process etc.)>

Volatility File Extract from Memory

>$ volatility -f <example.raw> --profile=<profile> dumpfiles -Q <dataoffset> -D <output-directory>

(change file extension after extracting)

Volatility suspicious Memory Allocations

>$ volatility -f <example.raw> --profile=<profile> malfind -p <pid>

Volatility Dumping Memory Written

>$ volatility -f <example.raw> --profile=<profile> vaddump -b <base_address> -D <output_directory>

Volatility Chrome History (Download [https://github.com/superponible/volatility-plugins](https://github.com/superponible/volatility-plugins))

>$ volaility --plugins=plugins/ -f <example.raw> --profile=<profile> chromehistory > <output_file>

or

extract browser history file and open it in SQLite