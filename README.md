[comment]: # "Auto-generated SOAR connector documentation"
# Threat Grid

Publisher: Splunk  
Connector Version: 2\.2\.9  
Product Vendor: Threat Grid  
Product Name: Threat Grid  
Product Version Supported (regex): "\.\*"  
Minimum Product Version: 4\.10\.0\.40961  

This app supports executing investigative actions to analyze executables and URLs on the Threat Grid sandbox

### Configuration Variables
The below configuration variables are required for this Connector to operate.  These variables are specified when configuring a Threat Grid asset in SOAR.

VARIABLE | REQUIRED | TYPE | DESCRIPTION
-------- | -------- | ---- | -----------
**base\_uri** |  required  | string | Base URL to Threat Grid service
**verify\_server\_cert** |  optional  | boolean | Verify server certificate
**api\_key** |  required  | password | API Key
**timeout** |  required  | numeric | Timeout \(seconds\)

### Supported Actions  
[test connectivity](#action-test-connectivity) - Validate the asset configuration for connectivity\. This action logs into the device to check the connection and credentials  
[detonate file](#action-detonate-file) - Run the file in the Threat Grid sandbox and retrieve the analysis results  
[get report](#action-get-report) - Query for results of an already completed task in Threat Grid  
[detonate url](#action-detonate-url) - Load a URL in the Threat Grid sandbox and retrieve the analysis results  
[list playbooks](#action-list-playbooks) - List the playbooks available in the connected ThreatGrid environment  
[list submissions](#action-list-submissions) - List the submissions present on ThreatGrid based on the query provided  

## action: 'test connectivity'
Validate the asset configuration for connectivity\. This action logs into the device to check the connection and credentials

Type: **test**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
No Output  

## action: 'detonate file'
Run the file in the Threat Grid sandbox and retrieve the analysis results

Type: **generic**  
Read only: **False**

This action requires the input file to be present in the vault and therefore takes the vault id as the input parameter\.

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**vault\_id** |  required  | Vault ID of file to detonate | string |  `vault id`  `pe file`  `pdf`  `sha1` 
**file\_name** |  optional  | Filename to use | string |  `file name` 
**vm** |  optional  | VM image to run on | string | 
**force\_analysis** |  optional  | Force re\-run of sample | boolean | 
**private** |  optional  | Mark file and results private | boolean | 
**playbook** |  optional  | ThreatGrid Playbook to run on the submitted file | string |  `threatgrid playbook name` 
**sample\_password** |  optional  | Password used to open the submitted file | string |  `password` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.file\_name | string |  `file name` 
action\_result\.parameter\.sample\_password | string |  `password` 
action\_result\.parameter\.force\_analysis | boolean | 
action\_result\.parameter\.playbook | string |  `threatgrid playbook name` 
action\_result\.parameter\.private | boolean | 
action\_result\.parameter\.vault\_id | string |  `vault id`  `pe file`  `pdf`  `sha1` 
action\_result\.parameter\.vm | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.asn | numeric | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.country | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.country\_name | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.org | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.reverse\_dns | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.ts | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.first\_seen | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.last\_seen | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.query\_hash\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.scanner\_count | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.scanner\_match | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.status | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.threat\_level | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.threat\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.trust\_factor | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.created\-time | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.entropy | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.Sections\.InternetShortcut\.Properties\.URL | string |  `url` 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.exports | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.company\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.copyright | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.file\_description | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.file\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.internal\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.original\_file\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.product\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.product\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.header\_relocations | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_code\_segment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_instruction\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_stack\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_stack\_segment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.pages | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.size\_in\_paragraphs | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.import\_hash | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.number\_of\_symbols | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.actual\_checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.claimed\_checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.entrypoint\_address | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.file\_alignment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.linker\_major\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.linker\_minor\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.loader\_flag | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.number\_of\_rva\_and\_sizes | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.reserved\_field | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.section\_alignment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.subsystem | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.signed | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.timestamp | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.imports\.\*\.dll | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.imports\.\*\.entries | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.internal\_checksum\_match | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.codepage | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.language | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.locale | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.offset | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.path | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.resource\_sha256 | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.sublanguage | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.address | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.characteristics | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.data\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.entropy | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.entropy\_type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.section | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.section\_hash | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.virtual\_size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.InternetShortcut\.properties\.URL | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.signatures | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.tag\_attrs | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.tags | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.urls | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.magic\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.magic\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.md5 | string |  `md5` 
action\_result\.data\.\*\.report\.artifacts\.\*\.mime\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.origin | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.path | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.contains | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.extracted\_from | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.network | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.process | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.sha1 | string |  `sha1` 
action\_result\.data\.\*\.report\.artifacts\.\*\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.report\.artifacts\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.type | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.changed | boolean | 
action\_result\.data\.\*\.report\.disk\.mbr\.contents\.curr | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.contents\.orig | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.changed | boolean | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.start | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.type | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.start | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.type | numeric | 
action\_result\.data\.\*\.report\.domains\.\*\.content\_categories | string | 
action\_result\.data\.\*\.report\.domains\.\*\.security\_categories | string | 
action\_result\.data\.\*\.report\.domains\.\*\.status | string | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.key | string | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.offset | numeric | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.pattern | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_created | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_deleted | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_modified | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.kpid | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.allocation\_type | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.entry\.\*\.base\_address | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.entry\.\*\.size | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.process | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.process\_handle | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.protect | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.zero\_bits | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.monitored | boolean | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.new | boolean | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.parent | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.pid | numeric |  `pid` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.ppid | numeric |  `pid` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.process\_name | string |  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.access | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.options | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_deleted | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.data | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.data\_type | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.value\_name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.command\_line | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.current\_directory | string |  `file path` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.desktop\_info | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.dll\_path | string |  `file path` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.image\_pathname | string |  `file path`  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.runtime\_data | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.shell\_info | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.tid | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.upid | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.uthread | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.window\_title | string |  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.client\_id | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.create\_suspended | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.process | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.process\_handle | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.return | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.thread | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.time | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.category | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.confidence | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Answer\_Data | string |  `ip` 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Answer\_Type | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Artifact\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Code | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Description | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Filetype | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Method | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Network\_Stream | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Path | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Process\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Process\_Name | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Query\_Data | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Query\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Rule | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.SHA256 | string |  `sha256` 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Script\_Type | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Status | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.TTL | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Trans\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.URL | string |  `url` 
action\_result\.data\.\*\.report\.iocs\.\*\.description | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.heuristic\_coefficient | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.hits | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.ioc | string |  `url` 
action\_result\.data\.\*\.report\.iocs\.\*\.mitre\-tactics | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.severity | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.tags | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.title | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.truncated | boolean | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.report\_created | numeric | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.sandbox\_id | string | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.sandbox\_version | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.filename | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.magic | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.sha256 | string |  `hash`  `md5`  `sha256` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.type | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.analysis\_end | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.analysis\_start | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.controlsubject | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.current\_os | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.display\_name | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.run\_time | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.sample\_executed | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.sandcastle | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.vm | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.vm\_id | string |  `md5` 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_missed | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_orig | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_orig\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_resp | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_resp\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.conn\_state | string | 
action\_result\.data\.\*\.report\.network\.\*\.dst | string |  `ip` 
action\_result\.data\.\*\.report\.network\.\*\.dst\_port | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.duration | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.history | string | 
action\_result\.data\.\*\.report\.network\.\*\.packets | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.packets\_orig | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.packets\_resp | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.service | string | 
action\_result\.data\.\*\.report\.network\.\*\.session | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.src | string |  `ip` 
action\_result\.data\.\*\.report\.network\.\*\.src\_port | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.transport | string | 
action\_result\.data\.\*\.report\.network\.\*\.ts\_begin | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.ts\_end | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.uid | string | 
action\_result\.data\.\*\.report\.status\.analysis\_started\_at | numeric | 
action\_result\.data\.\*\.report\.status\.analysis\_submitted\_at | numeric | 
action\_result\.data\.\*\.report\.status\.done\_url | string |  `url` 
action\_result\.data\.\*\.report\.status\.id | string |  `md5` 
action\_result\.data\.\*\.report\.status\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.status\.origin | string | 
action\_result\.data\.\*\.report\.status\.original\_filename | string | 
action\_result\.data\.\*\.report\.status\.playbook | string | 
action\_result\.data\.\*\.report\.status\.queue | string | 
action\_result\.data\.\*\.report\.status\.ran | boolean | 
action\_result\.data\.\*\.report\.status\.running\_on | string | 
action\_result\.data\.\*\.report\.status\.sample\_started\_at | numeric | 
action\_result\.data\.\*\.report\.status\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.status\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.status\.state | string | 
action\_result\.data\.\*\.report\.status\.status | string | 
action\_result\.data\.\*\.report\.status\.ven | string | 
action\_result\.data\.\*\.report\.status\.vm | string | 
action\_result\.data\.\*\.report\.status\.vm\_runtime | numeric | 
action\_result\.data\.\*\.report\.threat\.bucket | string | 
action\_result\.data\.\*\.report\.threat\.heuristic\_raw\_score | numeric | 
action\_result\.data\.\*\.report\.threat\.heuristic\_score | numeric | 
action\_result\.data\.\*\.report\.threat\.threat\_score | numeric | 
action\_result\.data\.\*\.report\.version | numeric | 
action\_result\.data\.\*\.report\.versions\.file\.html | string | 
action\_result\.data\.\*\.report\.versions\.file\.ini | string | 
action\_result\.data\.\*\.report\.versions\.file\.js | string | 
action\_result\.data\.\*\.report\.versions\.file\.lnk | string | 
action\_result\.data\.\*\.report\.versions\.file\.pdf | string | 
action\_result\.data\.\*\.report\.versions\.file\.pe | string | 
action\_result\.data\.\*\.report\.versions\.file\.rtf | string | 
action\_result\.data\.\*\.report\.versions\.file\.txt | string | 
action\_result\.data\.\*\.report\.versions\.file\.version | string | 
action\_result\.data\.\*\.report\.versions\.heuristic\_model | string | 
action\_result\.data\.\*\.report\.versions\.network\.version | string | 
action\_result\.data\.\*\.report\.versions\.reversing\_labs | string | 
action\_result\.data\.\*\.report\.versions\.version | string | 
action\_result\.data\.\*\.report\.versions\.virustotal | string | 
action\_result\.data\.\*\.report\.versions\.yara | string | 
action\_result\.data\.\*\.status\.completed\_at | string | 
action\_result\.data\.\*\.status\.filename | string | 
action\_result\.data\.\*\.status\.id | string |  `threatgrid task id`  `md5` 
action\_result\.data\.\*\.status\.login | string | 
action\_result\.data\.\*\.status\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.status\.os | string | 
action\_result\.data\.\*\.status\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.status\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.status\.started\_at | string | 
action\_result\.data\.\*\.status\.state | string | 
action\_result\.data\.\*\.status\.status | string | 
action\_result\.data\.\*\.status\.submission\_id | numeric | 
action\_result\.data\.\*\.status\.submitted\_at | string | 
action\_result\.data\.\*\.status\.vm | string | 
action\_result\.data\.\*\.threat\.bis | string | 
action\_result\.data\.\*\.threat\.count | numeric | 
action\_result\.data\.\*\.threat\.max\-confidence | numeric | 
action\_result\.data\.\*\.threat\.max\-severity | numeric | 
action\_result\.data\.\*\.threat\.sample | string |  `md5` 
action\_result\.data\.\*\.threat\.score | numeric | 
action\_result\.summary\.id | string |  `threatgrid task id`  `md5` 
action\_result\.summary\.results\_url | string |  `url` 
action\_result\.summary\.target | string |  `file name` 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'get report'
Query for results of an already completed task in Threat Grid

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**id** |  required  | Task ID to get the results of | string |  `threatgrid task id` 
**download\_report** |  optional  | Download HTML report to the phantom vault | boolean | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.download\_report | boolean | 
action\_result\.parameter\.id | string |  `threatgrid task id` 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.asn | numeric | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.country | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.country\_name | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.org | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.reverse\_dns | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.ts | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.first\_seen | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.last\_seen | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.query\_hash\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.scanner\_count | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.scanner\_match | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.status | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.threat\_level | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.threat\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.trust\_factor | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.created\-time | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.entropy | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.Sections\.InternetShortcut\.Properties\.URL | string |  `url` 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.exports | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.company\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.copyright | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.file\_description | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.file\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.internal\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.original\_file\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.product\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.product\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.header\_relocations | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_code\_segment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_instruction\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_stack\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_stack\_segment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.pages | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.size\_in\_paragraphs | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.import\_hash | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.number\_of\_symbols | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.actual\_checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.claimed\_checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.entrypoint\_address | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.file\_alignment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.linker\_major\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.linker\_minor\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.loader\_flag | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.number\_of\_rva\_and\_sizes | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.reserved\_field | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.section\_alignment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.subsystem | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.signed | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.timestamp | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.imports\.\*\.dll | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.imports\.\*\.entries | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.internal\_checksum\_match | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.codepage | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.language | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.locale | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.offset | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.path | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.resource\_sha256 | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.sublanguage | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.address | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.characteristics | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.data\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.entropy | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.entropy\_type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.section | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.section\_hash | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.virtual\_size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.InternetShortcut\.properties\.URL | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.signatures | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.tag\_attrs | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.tags | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.urls | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.magic\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.md5 | string |  `md5` 
action\_result\.data\.\*\.report\.artifacts\.\*\.mime\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.origin | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.path | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.contains | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.extracted\_from | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.network | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.process | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.sha1 | string |  `sha1` 
action\_result\.data\.\*\.report\.artifacts\.\*\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.report\.artifacts\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.type | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.changed | boolean | 
action\_result\.data\.\*\.report\.disk\.mbr\.contents\.curr | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.contents\.orig | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.changed | boolean | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.start | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.type | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.start | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.type | numeric | 
action\_result\.data\.\*\.report\.domains\.\*\.content\_categories | string | 
action\_result\.data\.\*\.report\.domains\.\*\.security\_categories | string | 
action\_result\.data\.\*\.report\.domains\.\*\.status | string | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.key | string | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.offset | numeric | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.pattern | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_created | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_deleted | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_modified | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.kpid | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.allocation\_type | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.entry\.\*\.base\_address | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.entry\.\*\.size | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.process | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.process\_handle | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.protect | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.zero\_bits | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.monitored | boolean | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.new | boolean | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.parent | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.pid | numeric |  `pid` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.ppid | numeric |  `pid` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.process\_name | string |  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.access | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.options | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_deleted | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.data | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.data\_type | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.value\_name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.command\_line | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.current\_directory | string |  `file path` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.desktop\_info | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.dll\_path | string |  `file path` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.image\_pathname | string |  `file path`  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.runtime\_data | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.shell\_info | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.tid | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.upid | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.uthread | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.window\_title | string |  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.client\_id | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.create\_suspended | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.process | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.process\_handle | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.return | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.thread | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.time | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.category | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.confidence | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Answer\_Data | string |  `ip` 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Answer\_Type | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Artifact\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Code | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Description | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Filetype | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Gid | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.IP | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Message | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Method | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Network\_Stream | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Path | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Process\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Process\_Name | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Query\_Data | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Query\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Rev | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Rule | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.SHA256 | string |  `sha256` 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Script\_Type | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Sid | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Status | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.TTL | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Trans\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.URL | string |  `url` 
action\_result\.data\.\*\.report\.iocs\.\*\.description | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.heuristic\_coefficient | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.hits | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.ioc | string |  `url` 
action\_result\.data\.\*\.report\.iocs\.\*\.mitre\-tactics | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.severity | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.tags | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.title | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.truncated | boolean | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.report\_created | numeric | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.sandbox\_id | string | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.sandbox\_version | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.filename | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.magic | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.sha256 | string |  `hash`  `md5`  `sha256` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.type | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.analysis\_end | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.analysis\_start | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.controlsubject | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.current\_os | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.display\_name | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.run\_time | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.sample\_executed | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.sandcastle | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.vm | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.vm\_id | string |  `md5` 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_missed | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_orig | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_orig\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_resp | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_resp\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.conn\_state | string | 
action\_result\.data\.\*\.report\.network\.\*\.dst | string |  `ip` 
action\_result\.data\.\*\.report\.network\.\*\.dst\_port | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.duration | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.history | string | 
action\_result\.data\.\*\.report\.network\.\*\.packets | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.packets\_orig | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.packets\_resp | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.service | string | 
action\_result\.data\.\*\.report\.network\.\*\.session | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.src | string |  `ip` 
action\_result\.data\.\*\.report\.network\.\*\.src\_port | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.transport | string | 
action\_result\.data\.\*\.report\.network\.\*\.ts\_begin | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.ts\_end | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.uid | string | 
action\_result\.data\.\*\.report\.status\.analysis\_started\_at | numeric | 
action\_result\.data\.\*\.report\.status\.analysis\_submitted\_at | numeric | 
action\_result\.data\.\*\.report\.status\.done\_url | string |  `url` 
action\_result\.data\.\*\.report\.status\.id | string |  `md5` 
action\_result\.data\.\*\.report\.status\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.status\.options | string | 
action\_result\.data\.\*\.report\.status\.origin | string | 
action\_result\.data\.\*\.report\.status\.original\_filename | string | 
action\_result\.data\.\*\.report\.status\.playbook | string | 
action\_result\.data\.\*\.report\.status\.queue | string | 
action\_result\.data\.\*\.report\.status\.ran | boolean | 
action\_result\.data\.\*\.report\.status\.running\_on | string | 
action\_result\.data\.\*\.report\.status\.sample\_started\_at | numeric | 
action\_result\.data\.\*\.report\.status\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.status\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.status\.state | string | 
action\_result\.data\.\*\.report\.status\.status | string | 
action\_result\.data\.\*\.report\.status\.tags | string | 
action\_result\.data\.\*\.report\.status\.ven | string | 
action\_result\.data\.\*\.report\.status\.vm | string | 
action\_result\.data\.\*\.report\.status\.vm\_runtime | numeric | 
action\_result\.data\.\*\.report\.threat\.bucket | string | 
action\_result\.data\.\*\.report\.threat\.heuristic\_raw\_score | numeric | 
action\_result\.data\.\*\.report\.threat\.heuristic\_score | numeric | 
action\_result\.data\.\*\.report\.threat\.threat\_score | numeric | 
action\_result\.data\.\*\.report\.version | numeric | 
action\_result\.data\.\*\.report\.versions\.file\.html | string | 
action\_result\.data\.\*\.report\.versions\.file\.ini | string | 
action\_result\.data\.\*\.report\.versions\.file\.js | string | 
action\_result\.data\.\*\.report\.versions\.file\.lnk | string | 
action\_result\.data\.\*\.report\.versions\.file\.pdf | string | 
action\_result\.data\.\*\.report\.versions\.file\.pe | string | 
action\_result\.data\.\*\.report\.versions\.file\.rtf | string | 
action\_result\.data\.\*\.report\.versions\.file\.txt | string | 
action\_result\.data\.\*\.report\.versions\.file\.version | string | 
action\_result\.data\.\*\.report\.versions\.heuristic\_model | string | 
action\_result\.data\.\*\.report\.versions\.network\.version | string | 
action\_result\.data\.\*\.report\.versions\.reversing\_labs | string | 
action\_result\.data\.\*\.report\.versions\.version | string | 
action\_result\.data\.\*\.report\.versions\.virustotal | string | 
action\_result\.data\.\*\.report\.versions\.yara | string | 
action\_result\.data\.\*\.report\.warnings\.\*\.code | string | 
action\_result\.data\.\*\.report\.warnings\.\*\.description | string | 
action\_result\.data\.\*\.report\.warnings\.\*\.error | string | 
action\_result\.data\.\*\.report\.warnings\.\*\.title | string | 
action\_result\.data\.\*\.status\.completed\_at | string | 
action\_result\.data\.\*\.status\.filename | string | 
action\_result\.data\.\*\.status\.id | string |  `threatgrid task id`  `md5` 
action\_result\.data\.\*\.status\.login | string | 
action\_result\.data\.\*\.status\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.status\.os | string | 
action\_result\.data\.\*\.status\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.status\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.status\.started\_at | string | 
action\_result\.data\.\*\.status\.state | string | 
action\_result\.data\.\*\.status\.status | string | 
action\_result\.data\.\*\.status\.submission\_id | numeric | 
action\_result\.data\.\*\.status\.submitted\_at | string | 
action\_result\.data\.\*\.status\.vm | string | 
action\_result\.data\.\*\.threat\.bis | string | 
action\_result\.data\.\*\.threat\.count | numeric | 
action\_result\.data\.\*\.threat\.max\-confidence | numeric | 
action\_result\.data\.\*\.threat\.max\-severity | numeric | 
action\_result\.data\.\*\.threat\.sample | string |  `md5` 
action\_result\.data\.\*\.threat\.score | numeric | 
action\_result\.summary\.id | string |  `threatgrid task id`  `md5` 
action\_result\.summary\.name | string | 
action\_result\.summary\.results\_url | string |  `url` 
action\_result\.summary\.target | string |  `file name`  `url`  `domain` 
action\_result\.summary\.vault\_file\_path | string | 
action\_result\.summary\.vault\_id | string | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'detonate url'
Load a URL in the Threat Grid sandbox and retrieve the analysis results

Type: **generic**  
Read only: **False**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**url** |  required  | URL to detonate | string |  `url`  `domain` 
**playbook** |  optional  | ThreatGrid Playbook to run on the submitted URL | string |  `threatgrid playbook name` 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.playbook | string |  `threatgrid playbook name` 
action\_result\.parameter\.url | string |  `url`  `domain` 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.asn | numeric | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.country | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.country\_name | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.org | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.reverse\_dns | string | 
action\_result\.data\.\*\.report\.annotations\.network\.\*\.ts | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.first\_seen | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.last\_seen | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.query\_hash\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.scanner\_count | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.scanner\_match | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.status | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.threat\_level | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.threat\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.antivirus\.reversing\_labs\.trust\_factor | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.created\-time | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.entropy | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.Sections\.InternetShortcut\.Properties\.URL | string |  `url` 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.exports | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.company\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.copyright | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.file\_description | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.file\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.internal\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.original\_file\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.product\_name | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.file\_info\.product\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.header\_relocations | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_code\_segment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_instruction\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_stack\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.initial\_stack\_segment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.pages | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.dos\.size\_in\_paragraphs | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.import\_hash | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.number\_of\_symbols | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.actual\_checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.claimed\_checksum | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.entrypoint\_address | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.file\_alignment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.linker\_major\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.linker\_minor\_version | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.loader\_flag | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.number\_of\_rva\_and\_sizes | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.reserved\_field | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.section\_alignment | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.optional\_header\.subsystem | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.signed | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.headers\.pe\.timestamp | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.imports\.\*\.dll | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.imports\.\*\.entries | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.internal\_checksum\_match | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.codepage | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.language | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.locale | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.offset | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.path | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.resource\_sha256 | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.sublanguage | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.resources\.\*\.type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.address | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.characteristics | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.data\_pointer | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.entropy | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.entropy\_type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.section | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.section\_hash | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.\*\.virtual\_size | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.sections\.InternetShortcut\.properties\.URL | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.signatures | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.tag\_attrs | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.tags | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.forensics\.urls | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.magic\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.magic\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.md5 | string |  `md5` 
action\_result\.data\.\*\.report\.artifacts\.\*\.mime\-type | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.origin | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.path | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.contains | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.extracted\_from | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.network | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.relation\.process | string | 
action\_result\.data\.\*\.report\.artifacts\.\*\.sha1 | string |  `sha1` 
action\_result\.data\.\*\.report\.artifacts\.\*\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.report\.artifacts\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.artifacts\.\*\.type | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.changed | boolean | 
action\_result\.data\.\*\.report\.disk\.mbr\.contents\.curr | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.contents\.orig | string | 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.curr\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.disk\.mbr\.hashes\.orig\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.changed | boolean | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.start | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.curr\.\*\.type | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.start | numeric | 
action\_result\.data\.\*\.report\.disk\.partition\_tables\.orig\.\*\.type | numeric | 
action\_result\.data\.\*\.report\.domains\.\*\.content\_categories | string | 
action\_result\.data\.\*\.report\.domains\.\*\.security\_categories | string | 
action\_result\.data\.\*\.report\.domains\.\*\.status | string | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.key | string | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.offset | numeric | 
action\_result\.data\.\*\.report\.dynamic\.extracted\_keys\.\*\.pattern | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_created | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_deleted | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.files\_modified | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.kpid | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.allocation\_type | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.entry\.\*\.base\_address | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.entry\.\*\.size | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.process | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.process\_handle | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.protect | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.memory\.\*\.zero\_bits | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.monitored | boolean | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.new | boolean | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.parent | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.pid | numeric |  `pid` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.ppid | numeric |  `pid` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.process\_name | string |  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.access | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_created\.\*\.options | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_deleted | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.data | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.data\_type | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.registry\_keys\_modified\.\*\.value\_name | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.command\_line | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.current\_directory | string |  `file path` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.desktop\_info | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.dll\_path | string |  `file path` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.image\_pathname | string |  `file path`  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.runtime\_data | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.shell\_info | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.tid | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.upid | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.uthread | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.startup\_info\.window\_title | string |  `file name` 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.client\_id | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.create\_suspended | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.process | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.process\_handle | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.return | numeric | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.threads\.\*\.thread | string | 
action\_result\.data\.\*\.report\.dynamic\.processes\.\*\.time | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.category | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.confidence | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Answer\_Data | string |  `ip` 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Answer\_Type | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Artifact\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Code | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Description | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Disk\_Artifact\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Filetype | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Method | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Net\_Artifact\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Network\_Stream | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Path | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Process\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Process\_Name | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Query\_Data | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Query\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Rule | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.SHA256 | string |  `sha256` 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Script\_Type | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Status | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.TTL | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.Trans\_ID | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.data\.\*\.URL | string |  `url` 
action\_result\.data\.\*\.report\.iocs\.\*\.description | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.heuristic\_coefficient | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.hits | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.ioc | string |  `url` 
action\_result\.data\.\*\.report\.iocs\.\*\.mitre\-tactics | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.severity | numeric | 
action\_result\.data\.\*\.report\.iocs\.\*\.tags | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.title | string | 
action\_result\.data\.\*\.report\.iocs\.\*\.truncated | boolean | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.report\_created | numeric | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.sandbox\_id | string | 
action\_result\.data\.\*\.report\.metadata\.general\_details\.sandbox\_version | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.filename | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.magic | string | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.sha256 | string |  `hash`  `md5`  `sha256` 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.size | numeric | 
action\_result\.data\.\*\.report\.metadata\.malware\_desc\.\*\.type | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.analysis\_end | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.analysis\_start | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.controlsubject | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.current\_os | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.display\_name | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.run\_time | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.sample\_executed | numeric | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.sandcastle | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.vm | string | 
action\_result\.data\.\*\.report\.metadata\.sandcastle\_env\.vm\_id | string |  `md5` 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_missed | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_orig | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_orig\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_resp | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.bytes\_resp\_payload | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.conn\_state | string | 
action\_result\.data\.\*\.report\.network\.\*\.dst | string |  `ip` 
action\_result\.data\.\*\.report\.network\.\*\.dst\_port | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.duration | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.history | string | 
action\_result\.data\.\*\.report\.network\.\*\.packets | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.packets\_orig | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.packets\_resp | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.service | string | 
action\_result\.data\.\*\.report\.network\.\*\.session | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.src | string |  `ip` 
action\_result\.data\.\*\.report\.network\.\*\.src\_port | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.transport | string | 
action\_result\.data\.\*\.report\.network\.\*\.ts\_begin | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.ts\_end | numeric | 
action\_result\.data\.\*\.report\.network\.\*\.uid | string | 
action\_result\.data\.\*\.report\.status\.analysis\_started\_at | numeric | 
action\_result\.data\.\*\.report\.status\.analysis\_submitted\_at | numeric | 
action\_result\.data\.\*\.report\.status\.done\_url | string |  `url` 
action\_result\.data\.\*\.report\.status\.id | string |  `md5` 
action\_result\.data\.\*\.report\.status\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.report\.status\.origin | string | 
action\_result\.data\.\*\.report\.status\.original\_filename | string | 
action\_result\.data\.\*\.report\.status\.playbook | string | 
action\_result\.data\.\*\.report\.status\.queue | string | 
action\_result\.data\.\*\.report\.status\.ran | boolean | 
action\_result\.data\.\*\.report\.status\.running\_on | string | 
action\_result\.data\.\*\.report\.status\.sample\_started\_at | numeric | 
action\_result\.data\.\*\.report\.status\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.report\.status\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.report\.status\.state | string | 
action\_result\.data\.\*\.report\.status\.status | string | 
action\_result\.data\.\*\.report\.status\.ven | string | 
action\_result\.data\.\*\.report\.status\.vm | string | 
action\_result\.data\.\*\.report\.status\.vm\_runtime | numeric | 
action\_result\.data\.\*\.report\.threat\.bucket | string | 
action\_result\.data\.\*\.report\.threat\.heuristic\_raw\_score | numeric | 
action\_result\.data\.\*\.report\.threat\.heuristic\_score | numeric | 
action\_result\.data\.\*\.report\.threat\.threat\_score | numeric | 
action\_result\.data\.\*\.report\.version | numeric | 
action\_result\.data\.\*\.report\.versions\.file\.html | string | 
action\_result\.data\.\*\.report\.versions\.file\.ini | string | 
action\_result\.data\.\*\.report\.versions\.file\.js | string | 
action\_result\.data\.\*\.report\.versions\.file\.lnk | string | 
action\_result\.data\.\*\.report\.versions\.file\.pdf | string | 
action\_result\.data\.\*\.report\.versions\.file\.pe | string | 
action\_result\.data\.\*\.report\.versions\.file\.rtf | string | 
action\_result\.data\.\*\.report\.versions\.file\.txt | string | 
action\_result\.data\.\*\.report\.versions\.file\.version | string | 
action\_result\.data\.\*\.report\.versions\.heuristic\_model | string | 
action\_result\.data\.\*\.report\.versions\.network\.version | string | 
action\_result\.data\.\*\.report\.versions\.reversing\_labs | string | 
action\_result\.data\.\*\.report\.versions\.version | string | 
action\_result\.data\.\*\.report\.versions\.virustotal | string | 
action\_result\.data\.\*\.report\.versions\.yara | string | 
action\_result\.data\.\*\.status\.completed\_at | string | 
action\_result\.data\.\*\.status\.filename | string | 
action\_result\.data\.\*\.status\.id | string |  `threatgrid task id`  `md5` 
action\_result\.data\.\*\.status\.login | string | 
action\_result\.data\.\*\.status\.md5 | string |  `hash`  `md5` 
action\_result\.data\.\*\.status\.os | string | 
action\_result\.data\.\*\.status\.sha1 | string |  `hash`  `sha1` 
action\_result\.data\.\*\.status\.sha256 | string |  `hash`  `sha256` 
action\_result\.data\.\*\.status\.started\_at | string | 
action\_result\.data\.\*\.status\.state | string | 
action\_result\.data\.\*\.status\.status | string | 
action\_result\.data\.\*\.status\.submission\_id | numeric | 
action\_result\.data\.\*\.status\.submitted\_at | string | 
action\_result\.data\.\*\.status\.vm | string | 
action\_result\.data\.\*\.threat\.bis | string | 
action\_result\.data\.\*\.threat\.count | numeric | 
action\_result\.data\.\*\.threat\.max\-confidence | numeric | 
action\_result\.data\.\*\.threat\.max\-severity | numeric | 
action\_result\.data\.\*\.threat\.sample | string |  `md5` 
action\_result\.data\.\*\.threat\.score | numeric | 
action\_result\.summary\.id | string |  `threatgrid task id`  `md5` 
action\_result\.summary\.results\_url | string |  `url` 
action\_result\.summary\.target | string |  `url`  `domain` 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list playbooks'
List the playbooks available in the connected ThreatGrid environment

Type: **investigate**  
Read only: **True**

#### Action Parameters
No parameters are required for this action

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.data\.\*\.description | string | 
action\_result\.data\.\*\.display | string | 
action\_result\.data\.\*\.name | string |  `threatgrid playbook name` 
action\_result\.summary\.Total Playbooks | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric |   

## action: 'list submissions'
List the submissions present on ThreatGrid based on the query provided

Type: **investigate**  
Read only: **True**

#### Action Parameters
PARAMETER | REQUIRED | DESCRIPTION | TYPE | CONTAINS
--------- | -------- | ----------- | ---- | --------
**query** |  optional  | Query text to search in the submissions | string | 
**limit** |  optional  | Limit for number of records to fetch \(default\: 100\) | numeric | 

#### Action Output
DATA PATH | TYPE | CONTAINS
--------- | ---- | --------
action\_result\.status | string | 
action\_result\.parameter\.limit | numeric | 
action\_result\.parameter\.query | string | 
action\_result\.data\.\*\.item\.analysis\.behaviors | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.analyzed\_file\.filename | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.analyzed\_file\.magic | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.analyzed\_file\.md5 | string |  `md5` 
action\_result\.data\.\*\.item\.analysis\.metadata\.analyzed\_file\.sha1 | string |  `sha1` 
action\_result\.data\.\*\.item\.analysis\.metadata\.analyzed\_file\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.item\.analysis\.metadata\.analyzed\_file\.size | numeric | 
action\_result\.data\.\*\.item\.analysis\.metadata\.analyzed\_file\.type | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.general\_details\.report\_created | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.general\_details\.sandbox\_id | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.general\_details\.sandbox\_version | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.malware\_desc | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.analysis\_end | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.analysis\_start | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.controlsubject | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.current\_os | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.display\_name | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.run\_time | numeric | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.sample\_executed | numeric | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.sandcastle | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.vm | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.sandcastle\_env\.vm\_id | string |  `md5` 
action\_result\.data\.\*\.item\.analysis\.metadata\.submitted\_file\.filename | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.submitted\_file\.magic | string | 
action\_result\.data\.\*\.item\.analysis\.metadata\.submitted\_file\.md5 | string |  `md5` 
action\_result\.data\.\*\.item\.analysis\.metadata\.submitted\_file\.sha1 | string |  `sha1` 
action\_result\.data\.\*\.item\.analysis\.metadata\.submitted\_file\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.item\.analysis\.metadata\.submitted\_file\.size | numeric | 
action\_result\.data\.\*\.item\.analysis\.metadata\.submitted\_file\.type | string | 
action\_result\.data\.\*\.item\.analysis\.threat\_score | numeric | 
action\_result\.data\.\*\.item\.filename | string | 
action\_result\.data\.\*\.item\.login | string | 
action\_result\.data\.\*\.item\.md5 | string |  `md5` 
action\_result\.data\.\*\.item\.organization\_id | numeric | 
action\_result\.data\.\*\.item\.private | boolean | 
action\_result\.data\.\*\.item\.sample | string |  `md5` 
action\_result\.data\.\*\.item\.sha1 | string |  `sha1` 
action\_result\.data\.\*\.item\.sha256 | string |  `sha256` 
action\_result\.data\.\*\.item\.state | string | 
action\_result\.data\.\*\.item\.status | string | 
action\_result\.data\.\*\.item\.submitted\_at | string | 
action\_result\.data\.\*\.item\.vm\_runtime | numeric | 
action\_result\.data\.\*\.score | numeric | 
action\_result\.summary\.search\_report | numeric | 
action\_result\.message | string | 
summary\.total\_objects | numeric | 
summary\.total\_objects\_successful | numeric | 