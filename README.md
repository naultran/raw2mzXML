# Converting XEVO-TQS files to mzXML for analysis with MAVEN

## Requirements
Download and install [ProteoWizard release 3.0.6485](https://proteowizard.sourceforge.io/) version  


Download and install [OpenMS version 1.12.0](https://sourceforge.net/projects/open-ms/)



## Setting up your environment (Cygwin)
```
PATH=$PATH:{PATH_TO_PROTEOWIZARD}/
```

## Converting Waters TQS data to mzXML
### 1. RAW to mzML (ProteoWizard)
_Note_: You may see the following error message
Error opening index file TEST_KO_001.raw\_func001.ind
This does not appear to cause any downstream problems
```
for raw_file in *.raw
do
	msconvert ${raw_file} --mzML
done
```

### 2. mzML to mzXML (Open-MS)
```
for mzML_file in *.mzML
do
	newname=$(echo $mzML_file | sed 's/mzML/mzXML') 
	{PATH_TO_OPEN_MS}/bin/FileConverter -in ${mzML_file} -out $newname
done
```