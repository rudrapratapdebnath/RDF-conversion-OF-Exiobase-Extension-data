# RDF-conversion of the Exiobase Extension data

Steps for the RDF conversion of the extension table of the Exobases dataset:
To covert the extension table of the Exiobase dataset in RDF, we follow the following four steps:
1.	Source data cleansing (RStudio (R script))
2.	Source ontology extraction (Used tool: SETLBI)
3.	Source to target mapping (Used tool: SETLBI)
4.	Data transformation (Used tool: SETLBI)

SETLBI link: https://github.com/rudrapratapdebnath/setlbi 

All source intermediate and RDF files are available in the Extension folder of this repository. There are two larger files in the Instance folder which is missing in the Extension folder. Therefore, we direct users to https://drive.google.com/drive/folders/1eJM2x3Aa01JcRJ2HUL37HgBRVGdwEqdR?usp=sharing. 

1.	Source data cleansing (RStudio (R script))  
 Flow Objects from the extension table: In the extension table, there exist different types of emissions (normal, unregistered, and avoided), different types of waste (waste, machinery, stock, and packing), Lands, Resources, and crop-residues. From the classification Excel file, we manually create a code for each flow objects. The output file contains five Excel sheets and each Excel sheet contains a category of flow objects. The column names of each sheet are Code and Name, where Code contains the generated codes and Name records the names of flow objects. 
        The path of the final file is Extension/Excel/Processed/extension_flow_object.xlsx.
        
        
Supply and Use transactions from MR_HSUT_2011_v3_  3_17_extensions.xlsb : We separate the supply and use sheets into two separate excel files based on the Exiobase_v3_3_17_figures.pdf file. In each sheet of a file, flow objects are replaced by their corresponding codes and activity codes are regenerated by concatenating the previous activity codes with the country names. 


Original files: MR_HSUT_2011_v3_3_17_extensions.xlsb  and Exiobase_v3_3_17_figures .pdf  in Extension/Excel/Originalfiles.
Processed files: extension_supply.xlsx and extension_use.xlsx  in Extension/Excel/Processed.


Cleansing the processed files: We cleanse the excel files and transform the Use and supply files according to the target ontology Flow structure. We use an R script to transform the excel files into CSV files. 


R script: ProcessingExtensionData.rmd in Extension/RScript.
The output of the R script is four CSV files: Inputflow, Outputflow, Activity, and Flowobject under the Extension folder. 



2.	Source ontology extraction (Used tool: SETLBI)
To use SETLBI download the SETL software from the Github link: https://github.com/rudrapratapdebnath/setlbi . After creating a java project with the SETL folder in the link, run SETLFrame.java defined under SETL/src/view. Open the ETL Layer interface from New->ETL Layer and open the following .xml file and run it.
ETL file:  SourceOntologyETL.xml in Extension/ETL
Source Ontologies: SourceOntology.ttl in Extension/SourceOntology

3.	Source to target mapping (Used tool: SETLBI)
Mapping file: map_version_1.ttl in Extension/Mapping


4.	Semantic transformation (Used tool: SETLBI)
Open the ETL Layer interface from New->ETL Layer and open the following .xml file and run it. 
ETL file: TargetABoxETL.xml in Extension/ETL
RDF files: Activity.ttl, Activitytype.ttl, Flowobject.ttl, Inputflow.ttl, and Outputflow.ttl in Extension/Instance




 
