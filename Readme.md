RegRipper
=======

![Last tested in Nuix 7.4](https://img.shields.io/badge/Nuix-7.4-green.svg)

View the GitHub project [here](https://github.com/Nuix/Reg-Ripper) or download the latest release [here](https://github.com/Nuix/Reg-Ripper/releases).

## Overview
The RegRipper script will search a case for relevant registry hive files, export the files, and then pass them to RegRipper for processing.

## Prerequisites
Download and extract [RegRipper](https://github.com/keydet89/RegRipper2.8)

## Setup

Begin by downloading the latest release.  Extract the contents of the archive into your Nuix scripts directory.  In Windows the script directory is likely going to be either of the following:

- `%appdata%\Nuix\Scripts` - User level script directory
- `%programdata%\Nuix\Scripts` - System level script directory

## Settings
### GUI Settings
- **RegRipper Installation Path** - Directory containing the RegRipper CLI (rip.exe)
- **Export Path** - Directory for the export performed by the script. 
	- **Delete export on completion?** - Check this box to have the export deleted after the script finishes
- **Output Path** - Directory for the output of the script
- **Ingest results on completion?** - Check this box to have the reports generated by RegRipper ingested back into the case for review

### HiveProfileMap.json
The `HiveProfileMap.json` file defines the plugin profile that RegRipper will use for a particular registry hive. 
A plugin profile is a plain text file that defines a list of RegRipper plugins to use. 
Plugin profiles can be found in the `plugins` directory inside of the RegRipper installation directory. 
Individual plugins have a `.pl` extension while plugin profiles have no extension.
The format for the `HiveProfileMap.json` file is:
```
{
  "<registry hive>" : "<plugin profile>",
  ...
}
```

## Output
The report files generated by RegRipper will be written to the supplied `Output Path`, using the following naming convention, `<EvidenceContainerName>_<UserName>_<HiveFileName>_<DuplicateIndex>.txt`

- **EvidenceContainerName** - Name of the evidence container that contains the hive file. If you are processing multiple registries you should ingest them into separate evidence containers to keep the reports separate.
- **UserName**  - This will only appear for `NTUSER.DAT` and `USRCLASS.DAT` registry files.
- **HiveFileName** - Name of the hive file used to generate the report.
- **DuplicateIndex** - Only used if the report file's name would be identical to an existing report.

The script will also generate a summary report (summary_report.csv) in the output directory which will contain the following columns
- **Report file** - Path to the report file.
- **Hive file** - Path to the hive file used to generate the report.
- **ItemGuid** - This will can be used to recall the hive file in the Nuix case that was used to generate the report.

# License

```
Copyright 2018 Nuix

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```
