## dvc push
`dvc status -c` what is going to be pushed by default. Meaning new files in cache and outs in current dir that are not in remote.  
## dvc run
--no-run-cache - forcefully execute the command again, even if the same dvc run command has already been run in this workspace. Useful if the command's code is non-deterministic (meaning it produces different outputs from the same list of inputs).
### dvc commit
You changed some stage's dependency but you know that this change is inconsequential to output of the stage, you can run `dvc commit` to force update this dependency without running stage.

## Free up gpu memory
kill -9   
fuser -v /dev/nvidia*  
fuser -k /dev/nvidia*

## demo
- no output files at first
- show dvc.yaml
- run dvc repro --no-run-cache
- show files that were created
- delete them, with dvc repro show how cache works
- show params and that you can specify as dependency only section of params
- dvc dag
- explain what gets put to cache
- results are in mlflow


Possible next actions:
- put all config in params
    benefit: apecify different config parts for different stages
- create pipeline for updating dataset, meaning discuss:
    - do we finetune on new data, or train from scratch
    - if finetune, then maybe we need pipeline that will preserve train val split with new data coming.x`