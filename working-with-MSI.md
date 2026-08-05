## Using MSI (Minnesota Supercomputer Institute)

This is how to do it with command line from a local directory, the Grissom lab Wiki has info on using RClone and Google Drive. But fuck google, ya know?

You need to get into and out MSI. I tend to log in and out maybe two dozen times or so each use.

**Using SSH**

To access MSI, you need to use an SSH key with your UMN x500 and password. In command line:

```
ssh paul0805@agate.msi.umn.edu
# enter password when prompted
# do duo
```


**Running a script**

1. Make a scratch directory:

   ```
   mkdir -p /scratch.global/paul0805/
   ```

3. Copy data

   NOTE: create empty folder HMM_output in your local directory first
   In normal command line:
    ```
    scp -r /home/gus/Documents/VP_GAD1_DREADDs_first/ paul0805@agate.msi.umn.edu:/scratch.global/paul0805/
    ```

4. Log into SSH

   ```
   ssh paul0805@agate.msi.umn.edu
   # enter password
   # do duo
   ```

6. Enter output folder

  ```
  cd /scratch.global/paul0805/VP_GAD1_DREADDs_first/HMM_output/pre-surgery/
  ```

5. run

  ```
  sbatch /scratch.global/paul0805/VP_GAD1_DREADDs_first/HMM_run/launcher_runHMM_danaSW_v3.slurm
  ```

6. check

   ```
   squeue --format="%.18i %.9P %.30j %.8u %.8T %.10M %.9l %.6D %R" --me
   ```

8. Get the data back

  ```
  scp -r paul0805@agate.msi.umn.edu:/scratch.global/paul0805/VP_GAD1_DREADDs_first/HMM_output/pre-surgery/ /home/gus/Documents/VP_GAD1_DREADDs_first/
  ```

*Bonus:* If you need a reset, delete the scratch folder:

  ```
  cd /scratch.global/paul0805
  rm -rf directoryname
  ```


