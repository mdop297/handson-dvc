### How to version data in images folder

- git init
- dvc init
- dvc add <path-to-target-data-folder>: dvc add ./images 
    - follow instruction:
        - git add .gitignore images.dvc
        - (git commit -m "added raw data")

To store data on a remote server like: google drive, google cloud storage, aws s3, or azure cloud
- dvc remote add -d [==default] [name of the storage] [storage uri]

Add credential to gdrive:
- Create a sevice account 
- Download json file contains service account key 
- Share the folder to that service account. Then run these command (replace the path to json file)
- dvc remote modify myremote gdrive_use_service_account true
- dvc remote modify myremote --local \
              gdrive_service_account_json_file_path path/to/file.json

To push data to remote storage
- dvc push