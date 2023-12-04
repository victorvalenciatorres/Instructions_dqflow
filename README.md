<!-- doxy
\page refDetectorsMUONMCHEvaluation MCH Evaluation
/doxy -->

# Instructions dqFlow


O2Physics Enviroment:

```shell
alienv enter O2Physics/latest

```

 AO2D.root (run2 or run3):

```shell
sh downloadAOD.sh run2

```

```shell
sh downloadAOD.sh run3

```

----------------------------------------------------------------------------------------

Table Maker + dqFlow:

```shell
python3 runTableMaker.py configuration-mau.json -runData --add_extra_conv --add_bc_conv --add_zdc_conv --add_col_conv --add_track_prop


```

Table Reader:

```shell
  o2-analysis-dq-table-reader --configuration json://configAnalysisData.json -b --aod-writer-json writerConfiguration_dileptons.json
```

Table Reader + dqCorrelation :

```shell
o2-analysis-dq-table-reader -b --configuration json://FlowConfig.json | o2-analysis-dq-correlation -b --configuration json://FlowConfig.json

```


--------------------------------------------------------------------------------------


