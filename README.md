<!-- doxy
\page refDetectorsMUONMCHEvaluation MCH Evaluation
/doxy -->

# Instructions dqFlow

First, modify dqFlow.cxx by the new code (/Users/valencia/alice/O2Physics/PWGDQ/Tasks/dqFlow.cxx) and compile

```shell
aliBuild build O2Physics

```

Second, enter in the enviroment:

```shell
alienv enter O2Physics/latest

```

Third, download the AO2D.root (run2 or run3):

```shell
sh downloadAOD.sh run2

```

```shell
sh downloadAOD.sh run3

```

----------------------------------------------------------------------------------------

1st attempt to execute dqFlow (run2):

```shell
o2-analysis-bc-converter --configuration json://tempConfigTableMaker.json -b | o2-analysis-timestamp --configuration json://tempConfigTableMaker.json -b | o2-analysis-zdc-converter --configuration json://tempConfigTableMaker.json -b  | o2-analysis-collision-converter --configuration json://tempConfigTableMaker.json -b | o2-analysis-tracks-extra-converter --configuration json://tempConfigTableMaker.json -b | o2-analysis-multiplicity-table --configuration json://tempConfigTableMaker.json -b | o2-analysis-centrality-table --configuration json://tempConfigTableMaker.json -b | o2-analysis-event-selection --configuration json://tempConfigTableMaker.json -b | o2-analysis-trackextension --configuration json://tempConfigTableMaker.json -b | o2-analysis-trackselection --configuration json://tempConfigTableMaker.json -b | o2-analysis-fwdtrackextension --configuration json://tempConfigTableMaker.json -b | o2-analysis-dq-flow --configuration json://tempConfigTableMaker.json -b | o2-analysis-dq-table-maker --configuration json://tempConfigTableMaker.json --aod-writer-json OutputDirector.json --severity error --shm-segment-size 12000000000 -b


```

2nd attempt to execute dqFlow (run3):

```shell
 python3 runTableMaker.py configuration-new.json -runData --arg table-maker:MuonOnlyWithQvector:true --add_extra_conv --add_bc_conv --add_zdc_conv --add_col_conv
```

Finally, for the table reader:

```shell
o2-analysis-dq-table-reader --configuration json://configAnalysisData.json -b --aod-writer-json writerConfiguration_dileptons.json
```


--------------------------------------------------------------------------------------

