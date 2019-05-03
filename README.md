# Example of reading DICOM images from Cloud Object Storage
Jukka Ruponen / IBM, 2019-05-03

The method used  will first **download the file from COS** and then access the file locally in the Notebook.

**Reason:**
It seems that S3 (COS) StreamingBody access to DICOM file (which generates a buffered IO-object) does not retain the metadata in the resulting object. To get full .dcm file, with all it's metadata retained, it seems the way is to download it first and then access it from the underlying file system (GPFS).

**Note:**
If you'd need to iterate with and download multiple files in S3 (COS) bucket, there are plenty of examples in the web how to do this.
Search for instance "boto3 download multiple files" and then change the script below according to your needs.

