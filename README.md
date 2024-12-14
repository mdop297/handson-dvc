### How to version data in images folder
```code
git init
dvc init
dvc add <path-to-target-data-folder>: dvc add ./images 
```

- Then, follow instructions:
```code
git add .gitignore images.dvc
-git commit -m "added raw data")
```
To store data on a remote server like: google drive, google cloud storage, aws s3, or azure cloud
```code
dvc remote add -d <default> <name of the storage> <storage uri>
```

Add credential to gdrive:
- Create a sevice account 
- Download json file contains service account key 
- Share the folder to that service account. Then run these command (replace the path to json file)
```code
dvc remote modify myremote gdrive_use_service_account true
dvc remote modify myremote --local \
              gdrive_service_account_json_file_path path/to/file.json
```
To push data to remote storage
```code
dvc push
```

Get data from remote storage
```code
dvc pull
```

Update data when having new data:
1. Check the status
```
dvc status
```
2. update data with `dvc add`:
```
dvc add ./images 
```